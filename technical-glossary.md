# Technical Architecture Glossary — Amazon LP Stories
## Piyush Deveshwar | Sr. PM Interview Prep

> **How to use this doc:** For every technical term you've used in your stories, this explains (1) what it is in plain English, (2) why you chose it over alternatives, and (3) how to survive the follow-up question. Organized by story, then cross-referenced.

---

## PART 1: ARCHITECTURE PATTERNS (Used Across Multiple Stories)

---

### 1. Facade Pattern (S001)
**What you said:** "Hybrid architecture — legacy JD auth + decoupled microservices via facade pattern."

**Plain English:** Imagine a hotel receptionist. You don't talk to housekeeping, kitchen, and maintenance separately — you talk to the receptionist, who routes your request. A facade is a single "front door" API that sits between your new microservices and the old monolith. Your new services call the facade, and the facade translates those calls into whatever the old system understands.

**Why you chose it:**
- JD had a massive legacy monolith handling authentication, user sessions, and search. Rewriting it would take 12+ months.
- The facade let you build new services (Booking, Matchmaking, Settlement) independently while still using JD's existing login and user data.
- Trade-off: You accepted some latency overhead (every call hops through the facade) in exchange for not touching the monolith.

**Follow-up survival:**
- *"How did you handle distributed session state between the legacy monolith and your microservices?"*
  → The facade held a lightweight session cache (Redis). When a user logged in via JD's monolith, the facade issued a short-lived token that your microservices validated independently. This avoided coupling your services to JD's session store. TTL was ~30 minutes, refreshed on activity.
- *"What happens if the facade goes down?"*
  → Single point of failure risk. Mitigated with a load balancer in front of 2-3 facade instances, plus health checks. If all facade instances died, the entire Xperts experience was down — but JD core search still worked.

**Alternatives you rejected:**
| Option | Why rejected |
|--------|-------------|
| Full rewrite of JD monolith | 12+ months, not your mandate |
| Direct DB access from microservices | Tight coupling, schema changes would break everything |
| API Gateway (e.g., Kong) | Overkill for the scale; facade was simpler and faster to ship |

---

### 2. Microservices Architecture (S001, S004, S008)
**What you said:** "Built hybrid microservices — Booking, Matchmaking, Settlement."

**Plain English:** Instead of one giant application doing everything (monolith), you split it into small, independent services. Each service does one thing well: Booking handles order creation, Matchmaking handles vendor assignment, Settlement handles payments. They talk to each other via APIs (like internal phone calls).

**Why it matters for your story:**
- Each service could be developed, deployed, and scaled independently.
- When AC season hit (S008, 6x spike), you could scale just the Matchmaking service without scaling everything else.
- Different teams could own different services without stepping on each other.

**Follow-up survival:**
- *"How did services communicate?"*
  → Synchronous REST APIs for real-time operations (booking creation calls matchmaking immediately). Asynchronous events via message queue for non-blocking operations (settlement triggers notification after payment).
- *"What's the biggest downside?"*
  → Distributed system complexity. A single booking now involves 3 network calls instead of 3 function calls. You need retries, timeouts, and circuit breakers. Debugging is harder because logs are spread across services.

---

### 3. Saga Pattern (S004)
**What you said:** "Mandated URI versioning and Saga pattern for cross-domain eventual consistency."

**Plain English:** When a single user action (like placing an order) touches multiple services, you need a way to handle partial failures. A Saga is a sequence of steps where each service does its part. If step 3 fails, you run "compensation" steps to undo steps 1 and 2.

**Concrete example from your OMS:**
```
Step 1: OMS creates order (status: PENDING)
Step 2: Matchmaking assigns vendor (status: ASSIGNED)
Step 3: Payment reserves amount (status: PAYMENT_HOLD)

If Step 3 fails:
  → Compensation Step 2: Release vendor assignment
  → Compensation Step 1: Cancel order, notify user
```

**Why Saga over alternatives:**
| Pattern | How it works | Why you rejected it |
|---------|-------------|-------------------|
| Two-Phase Commit (2PC) | Lock all databases simultaneously, then commit all at once | Too slow. Requires all services to be available at the same time. One slow service blocks everything. Doesn't scale. |
| Saga (Choreography) | Each service emits events, next service listens and acts | What you used for simpler flows. No central coordinator. Risk: harder to track overall state. |
| Saga (Orchestration) | A central "orchestrator" service directs each step | Used for complex multi-step flows (full order lifecycle). OMS acted as orchestrator. |

**Follow-up survival:**
- *"What was the compensation logic if a downstream service failed?"*
  → Example: If Payment failed after Matchmaking assigned a vendor, the OMS (orchestrator) sent a "release_assignment" command to Matchmaking and a "cancel_order" event. The vendor saw the job disappear from their queue. The user got an "order couldn't be processed" notification with a retry option. Each compensation was idempotent — safe to retry if the compensation itself failed.
- *"How did you handle the case where compensation also fails?"*
  → Dead Letter Queue (DLQ). Failed compensations went into a DLQ that ops reviewed manually. In practice, this was <0.1% of cases. You tracked it with a simple Grafana dashboard showing DLQ depth.

---

### 4. Database-Per-Service (S004)
**What you said:** "Built 4 shared microservices with per-service databases to isolate blast radius."

**Plain English:** Each microservice gets its own database. The Booking service has its own MySQL instance, the Matchmaking service has its own, etc. No service can directly read or write another service's database.

**Why this matters:**
- **Blast radius isolation:** If the Matchmaking database crashes, Booking still works (it just can't assign vendors temporarily). Without this, one bad query could take down the entire platform.
- **Schema independence:** The Booking team can change their table structure without coordinating with Matchmaking.

**The trade-off you accepted:**
- **No cross-service JOINs.** You can't do `SELECT * FROM bookings JOIN vendors` because they're in different databases. For analytics/reporting, you needed a separate data pipeline that combined data.
- **Data duplication.** Some information (like vendor name) exists in multiple databases. You accepted this as a reasonable cost for isolation.

**Follow-up survival:**
- *"How did you handle complex joins for analytics across verticals?"*
  → Built an analytics pipeline that replicated data from each service's DB into a shared read-only data warehouse (could be a simple nightly ETL into a single Postgres instance). Operational queries stayed within each service. Analytics queries hit the warehouse.

---

### 5. Event-Driven Architecture / Message Queues (S003, S005, S020, S024, S026)
**What you said (variously):** "async event pipeline," "RabbitMQ," "fire-and-forget," "event bus"

**Plain English:** Instead of Service A directly calling Service B and waiting for a response, Service A drops a message into a queue (like putting a letter in a mailbox). Service B picks it up whenever it's ready. This decouples the services — if B is slow or down, A doesn't freeze.

**Three flavors you used:**

| Pattern | Where you used it | How it worked |
|---------|-------------------|---------------|
| Fire-and-forget | S005 (LPB pipeline) | Booking service emitted events. A separate analytics consumer wrote to an isolated Postgres. If the consumer was slow, bookings weren't affected. |
| Request-reply via queue | S003 (LLM search) | Search interceptor dropped failed queries into RabbitMQ. LLM workers processed and wrote results. WhatsApp service picked up corrections. |
| Event bus (pub-sub) | S026 (Silent bug) | Billing monolith published vendor status events. Multiple downstream services subscribed. The marketing service was one subscriber — and it was silently failing. |

**Key concept — Eventual Consistency:**
When you use queues, data isn't immediately consistent everywhere. After a booking is created, it might take a few seconds before the analytics dashboard updates. You accepted this because the alternative (synchronous calls to everything) would make the checkout slow and fragile.

**Follow-up survival:**
- *"What happens if the queue backs up?"* (S003)
  → In RabbitMQ, messages pile up in memory/disk. You set queue length limits and a TTL (time-to-live) on messages. If a message sat in the queue for >5 minutes, it was dropped — the search correction was no longer useful because the user had moved on. You monitored queue depth with alerts.
- *"How did you ensure fire-and-forget didn't lose critical data?"* (S005)
  → For the LPB pipeline, losing an occasional event was acceptable (it's analytics, not transactions). For payment events (S004), you used persistent messages with acknowledgments — the message isn't deleted from the queue until the consumer confirms it processed successfully.

---

### 6. Anti-Corruption Layer (S012)
**What you said:** "Built anti-corruption layer (XML→JSON)."

**Plain English:** The legacy call center system spoke XML (an older data format). Your modern services spoke JSON (the current standard). Instead of polluting your clean new code with XML handling, you built a thin translation layer that sat between them. It received XML from the legacy system, converted it to clean JSON, and passed it to your OMS. This "protected" your new code from the "corruption" of the old system's format.

**Why this specific name matters in interviews:** "Anti-corruption layer" is a Domain-Driven Design (DDD) term. Using it signals you understand software architecture patterns, not just that you hacked together a converter. It shows you were thinking about long-term code health, not just making it work.

**Follow-up survival:**
- *"Where exactly did it sit in the network topology?"*
  → It was a lightweight middleware service (could be a simple Node.js or Python Flask app) deployed between the call center API and your API Gateway. Call center system → XML POST → Anti-corruption service → JSON POST → API Gateway → OMS. It had no database of its own — purely stateless transformation.
- *"Why not just update the legacy system to speak JSON?"*
  → The legacy system was maintained by a different org. You had zero control over their release cycle. Changing their output format required their team's buy-in and 3-6 month timeline. The translation layer took 3 days to build.

---

### 7. Idempotency (S012)
**What you said:** "Added idempotency hash (phone + 5min window) to prevent duplicate orders from agent refreshes."

**Plain English:** If a call center agent accidentally clicks "Submit" twice (or their browser refreshes), the system should NOT create two orders. Idempotency means "doing the same thing twice has the same result as doing it once."

**How you implemented it:**
- You generated a hash from the caller's phone number + a 5-minute time window.
- Before creating an order, the system checked Redis: "Has this hash been seen before?"
- If yes → return the existing order (don't create a duplicate).
- If no → create the order, store the hash in Redis with a 5-minute TTL.

**Why phone + time window (not just a UUID):**
- Call center agents weren't sophisticated enough to manage unique request IDs.
- A phone number + 5-minute window captured the real scenario: same caller, same session, accidental double-submit.
- After 5 minutes, a new order from the same phone was likely intentional (callback).

**Follow-up survival:**
- *"What if two different agents handle the same caller within 5 minutes?"*
  → Edge case you accepted. The first agent's order would win. The second agent would see "order already exists" and could pick it up. In practice, the call routing system prevented this (one caller = one agent).

---

### 8. Fail-Open vs. Fail-Closed (S003)
**What you said:** "250ms fail-open timeout to prevent app hangs."

**Plain English:**
- **Fail-open:** If the system can't process in time, let the user through anyway (degrade gracefully). Like a turnstile that opens when the power goes out.
- **Fail-closed:** If the system can't process in time, block the user. Like a vault door that locks when power fails.

**In your LLM search story:**
- The LLM pipeline had 250ms to attempt a correction. If it didn't respond in time, the app showed the original (failed) search results rather than hanging.
- The correction still processed in the background and was delivered via WhatsApp/SMS later (async recovery).
- Why 250ms? User perception research: <200ms feels instant, 200-500ms feels responsive, >1000ms feels broken. 250ms was aggressive enough to not hurt the core experience.

**Follow-up survival:**
- *"Why not fail-closed for search?"*
  → Because showing zero results is worse than showing fallback results. Fail-closed is for security (e.g., payment auth — if the fraud check times out, block the transaction). Fail-open is for UX (search, recommendations).

---

### 9. Circuit Breaker Pattern (S019, S024)
**What you said:** "Automated circuit breaker dropping numbers <10% pickup."

**Plain English:** Like an electrical circuit breaker in your house. If too much current flows (too many failures), the breaker trips and cuts the circuit to prevent damage. In software, if a service or endpoint keeps failing, the circuit breaker stops sending requests to it temporarily, tries again after a cooldown, and only fully reconnects when it's healthy.

**In your telephony story (S019):**
- You monitored pickup rates per caller ID number.
- If a number's pickup rate dropped below 10% (rolling 24-hour average), the circuit breaker "tripped" — that number was removed from the rotation pool.
- After 7 days, it was retested. If pickup recovered, it re-entered the pool.

**In your notification gateway (S024):**
- If the SMS provider started returning errors above a threshold, the circuit breaker stopped sending through that provider and switched to a backup.

**Three states:**
```
CLOSED (normal) → requests flow through
OPEN (tripped) → requests are blocked, fast-fail
HALF-OPEN (testing) → a few test requests sent to check recovery
```

---

### 10. Dead Letter Queue — DLQ (S004, S024, S026)
**What you said:** "Built publisher-side schema validation and consumer-side alerting + Dead Letter Queue."

**Plain English:** When a message in your queue can't be processed (bad data, schema mismatch, service error), instead of losing it or retrying forever, it goes to a special "dead letter" queue — a holding pen for failed messages. Ops or automated scripts can later inspect and replay them.

**In your silent targeting bug (S026):**
- The billing monolith published vendor events with an outdated schema.
- The marketing service couldn't parse them and was dropping them silently.
- Your fix: add a DLQ so unparseable messages aren't lost. An alert fires when DLQ depth > 0. A replay script re-ingests fixed messages.

**Follow-up survival:**
- *"How did the DLQ replay script handle state changes that occurred while the vendor was in the DLQ?"*
  → The replay script fetched current vendor state from the billing service before re-processing. If the vendor's state had changed (e.g., deactivated), the replay skipped them. The script was idempotent — safe to run multiple times.

---

## PART 2: DATA & STORAGE PATTERNS

---

### 11. pgvector / Semantic Search (S003)
**What you said:** "Llama 3.2 intent extraction → pgvector semantic match."

**Plain English:** pgvector is a PostgreSQL extension that lets you store and search "embeddings" — numerical representations of text meaning. Instead of matching exact keywords, it finds content that's semantically similar.

**How it worked in your search story:**
1. User types "AC thik karo" (Hinglish for "fix my AC").
2. LLM extracts intent: "AC repair."
3. This intent is converted to an embedding (a vector of ~768 numbers).
4. pgvector searches your service catalog by vector similarity, finding "Air Conditioner Repair Service" even though the words don't match.

**Why pgvector over alternatives:**
| Option | Why rejected |
|--------|-------------|
| Elasticsearch | More powerful but separate infrastructure to maintain. Overkill for a lookup table of ~5,000 service categories. |
| FAISS (Facebook's vector search) | Fast but in-memory only. No persistence. Good for 100M+ vectors, overkill for your scale. |
| pgvector | Already using PostgreSQL. Zero new infrastructure. Good enough for <10K categories with <50ms query time. |

**Follow-up survival:**
- *"How did you structure the embeddings?"*
  → Each service category had a pre-computed embedding stored in pgvector. When a new query came in, the LLM output was embedded on-the-fly and compared via cosine similarity against the stored embeddings. Top-3 matches above a 0.7 similarity threshold were returned. Below 0.7 = "no confident match" → routed to human review.

---

### 12. Redis Cache (S012, S006)
**What you said:** "Stateless wrapper with Redis cache" and implied caching in multiple stories.

**Plain English:** Redis is an in-memory database — extremely fast (sub-millisecond reads) because data lives in RAM, not on disk. Used for temporary data that needs to be accessed quickly and frequently.

**How you used it:**
- **S012 (Headless Booking):** Stored the idempotency hash (phone + time window) to prevent duplicate orders. TTL of 5 minutes = auto-deleted after 5 minutes.
- **S006 (Skill Matching):** Cached the skill taxonomy tree so it didn't have to be fetched from MySQL on every booking request. Invalidated when skills were updated.
- **S007 (Pricing):** Cached the pricing grid (city × service) for fast checkout rendering. Updated every 24 hours.

**Key concept — TTL (Time To Live):**
Every Redis entry has an expiration. After TTL seconds, Redis automatically deletes it. This prevents stale data and memory bloat.

---

### 13. Isolated Database Pattern (S005)
**What you said:** "Async event pipeline → isolated Postgres → 3-hour cron batch."

**Plain English:** You created a completely separate PostgreSQL database for analytics, disconnected from the live transactional database. Events were copied asynchronously into this isolated DB. Your LPB metric calculations ran against this copy, never touching the live system.

**Why this was critical:**
- Complex analytics queries (aggregating hourly slots across all hubs) can be very slow and CPU-intensive.
- Running these on the live database could slow down actual checkouts happening simultaneously.
- The isolated DB was a "read-only copy optimized for analytics" — different indexes, different query patterns.

**Follow-up survival:**
- *"Why not use a read-replica of the main DB instead?"*
  → A read-replica mirrors the live schema, which is optimized for transactional operations (insertions, lookups by primary key). Your analytics needed different indexing (by time-slot, by hub, by category). The isolated DB had custom indexes and pre-aggregated tables that would have been wasteful on the live DB.

---

### 14. Hierarchical Taxonomy / Skill Tree (S006)
**What you said:** "Root → Branch → Leaf taxonomy and rule-based matching engine."

**Plain English:** A tree structure for categorizing services. Like a file system:
```
Home Services (Root)
├── AC (Branch)
│   ├── Window AC (Sub-Branch)
│   │   ├── Installation (Leaf)
│   │   ├── Repair (Leaf)
│   │   └── Gas Refill (Leaf)
│   └── Split AC (Sub-Branch)
│       ├── Inverter - Installation (Leaf)
│       ├── Inverter - Repair (Leaf)
│       └── Non-Inverter - Repair (Leaf)
```

**How it was modeled in MySQL:**
Most likely an **adjacency list** (simplest):
```sql
CREATE TABLE skill_tree (
    id INT PRIMARY KEY,
    name VARCHAR(255),
    parent_id INT REFERENCES skill_tree(id),
    level INT  -- 0=root, 1=branch, 2=sub-branch, 3=leaf
);
```

**Follow-up survival:**
- *"How did you model this in MySQL? Adjacency list, nested sets?"*
  → Adjacency list for simplicity. Each node has a `parent_id`. To get a vendor's skills, you query their skill mappings and traverse up. For matching, you traverse down from the customer's request to find vendors tagged at the leaf level.
- *"Tree traversal adds latency. How did you optimize?"*
  → The tree was small (~500 nodes) and rarely changed. You cached the entire tree in Redis as a denormalized JSON object. Matching was done in-memory against the cache. Cache was invalidated only when the skill taxonomy was edited (rare — maybe monthly).
- *"Why rule-based instead of ML?"*
  → The tree had ~500 nodes. ML needs thousands of examples per category to train well. Most leaf nodes had <100 historical bookings. Rule-based matching (if customer wants "Inverter AC Repair" → match vendors tagged with that leaf) was 100% deterministic and debuggable. ML would have been a black box with worse accuracy at this scale.

---

## PART 3: API & INTEGRATION PATTERNS

---

### 15. URI Versioning (S004)
**What you said:** "Mandated URI versioning."

**Plain English:** When your API changes, old clients (other services still using the old format) shouldn't break. URI versioning puts the version number in the URL:
```
/api/v1/orders  → original
/api/v2/orders  → new fields added, old fields still work
```

**Why you mandated it for the shared OMS:**
- 4 different vertical teams were calling the OMS. If you changed the order creation API, all 4 would break simultaneously.
- With versioning, you could ship v2 for new verticals while existing verticals stayed on v1 until they were ready to migrate.

**Follow-up survival:**
- *"How long did you support old versions?"*
  → Rule: support current version + 1 previous version. Gave teams 1 quarter to migrate. After that, old versions were deprecated with a 30-day warning.

---

### 16. Sync vs. Async Processing (S003, S020)
**What you said:** "Split traffic: high-value/urgent (25K) to real-time, rest to batch."

**Plain English:**
- **Synchronous (sync):** Caller waits for a response. Like a phone call — you speak, the other person responds immediately. Fast but blocks the caller.
- **Asynchronous (async):** Caller drops a request and moves on. Like sending an email — you don't wait by your inbox. Response comes later via callback/webhook.

**Your dual-path design (S020 — Lead Salvaging):**
```
Incoming 80K "spam" calls
├── 25K high-value/urgent → Sync real-time LLM processing (respond in <2 sec)
└── 55K rest → Async batch processing (processed within 30 min)
```

**Why split?**
- Real-time LLM processing of all 80K calls would cost ~4x more in GPU compute.
- Only 25K were urgent enough to need immediate rerouting.
- The 55K batch calls could be processed with cheaper, shared GPU instances during off-peak hours.

**The "chunking" technique (S020):**
- For real-time calls, you didn't transcribe the entire 48-second audio.
- "Early stop" chunking: transcribe the first 10-15 seconds, run intent extraction. If confidence >80%, stop transcribing. This saved 75% of GPU compute.

---

### 17. Schema Validation (S024, S026)
**What you said:** "Strict JSON schema validation to reject malformed/misclassified payloads instantly."

**Plain English:** Before accepting any message, check that it has the right structure. Like a form that rejects submission if you leave a required field blank.

**Example from your Notification Gateway (S024):**
```json
// Expected schema for OTP notification:
{
  "type": "OTP",          // REQUIRED, must be OTP/MARKETING/TRANSACTIONAL
  "recipient": "+91...",   // REQUIRED, valid phone number
  "content": "Your OTP is 4521", // REQUIRED, <160 chars
  "priority": "CRITICAL",  // REQUIRED for OTP
  "sender_service": "auth-service" // REQUIRED, registered service name
}

// What the marketing team was sending (incorrectly):
{
  "type": "MARKETING",
  "priority": "CRITICAL",    // ← WRONG! Marketing should never be CRITICAL
  "recipient_list": [...1M numbers...],
  "content": "Summer sale!"
}
```

Your validation layer caught `priority: CRITICAL` on a `type: MARKETING` message and rejected it with an error, preventing it from consuming the OTP rate limits.

---

### 18. Pessimistic Locking (S013)
**What you said:** "Added pessimistic locking at the app layer to prevent agent collision."

**Plain English:** When two call center agents try to open the same customer ticket simultaneously, only one should be able to edit it. Pessimistic locking "locks" the ticket the moment Agent A opens it. Agent B sees "This ticket is being handled by Agent A" and can't edit it.

**Contrast with Optimistic Locking:**
| Type | How it works | Best for |
|------|-------------|----------|
| Pessimistic | Lock BEFORE editing. Others wait/blocked. | High-contention scenarios (many agents, few tickets) |
| Optimistic | Don't lock. Check at save time if someone else changed it. | Low-contention (rare conflicts, like wikis) |

**You chose pessimistic because:**
- Call center agents work fast. Two agents grabbing the same urgent ticket was common.
- With optimistic locking, Agent B would spend 5 minutes typing a response only to get "conflict" on save. That wastes time and causes frustration.
- Pessimistic locking prevented wasted effort upfront.

**Implementation:**
- When Agent A opens a ticket, a row-level lock is set in the database (or a Redis key with TTL).
- If Agent A doesn't release within 10 minutes (timeout), the lock auto-releases.
- Agent B sees a visual indicator: "Locked by Agent A."

---

## PART 4: PERFORMANCE & FRONTEND PATTERNS

---

### 19. Cumulative Layout Shift / CLS (S017, S023)
**What you said:** "Enforced fixed containers to prevent CLS" and "synchronous pricing API caused massive CLS on 4G."

**Plain English:** CLS measures how much page elements jump around while loading. Ever tried to click a button, but an ad loaded above it and pushed the button down, causing you to click the ad instead? That's layout shift.

**Google measures this as a Core Web Vital.** Score >0.1 is considered poor. It affects SEO ranking.

**How you caused it (S023):**
- The Day Pass pricing was loaded via a synchronous API call.
- On Wi-Fi, it loaded in 200ms — barely noticeable.
- On 4G, it took 3 seconds. During those 3 seconds, the price area was empty, and when data loaded, everything below it jumped down.
- Vendors trying to click on their leads kept hitting the wrong element.

**How you fixed it:**
- Reserved a fixed-height container for the pricing block (even before data loaded, the space was "held").
- Moved the pricing call to async (load it in the background, fill it in when ready).
- Added a 1-day stale SQL fallback: if the API didn't respond in 500ms, show yesterday's price instantly.

---

### 20. Async/Lazy Loading (S023, S022)
**What you said:** "Refactored to async rendering" and "conditional UI rendering."

**Plain English:**
- **Lazy loading:** Don't load something until the user needs it. If charts are below the fold (user needs to scroll to see them), don't load them on page open.
- **Async rendering:** Start showing the page immediately with whatever data you have. Fill in remaining sections as data arrives from APIs, without blocking the whole page.

**In your merchant dashboard fix (S022):**
- The original design loaded charts synchronously — the entire page waited for chart data.
- For 70% of vendors with sparse data, the chart APIs returned empty datasets, but still took 2-3 seconds.
- Your fix: check a "data density score" first. If score < threshold, don't even call the chart APIs. Show the leads section immediately.

---

### 21. XGBoost as Diagnostic Tool (S025)
**What you said:** "Used XGBoost off-line not for production, but as a 'black box' diagnostic."

**Plain English:** XGBoost is a machine learning algorithm (specifically, gradient-boosted decision trees). It's excellent at finding which combination of factors predicts an outcome.

**Your clever twist:** You didn't deploy XGBoost in production. You used it as an analysis tool to discover which features mattered for lead response, then translated those insights into a simple formula that could run in production without any ML infrastructure.

**The pipeline:**
```
Step 1: Train XGBoost on historical lead data
        Input: distance, ticket value, time of day, photos viewed, review count, etc.
        Output: probability vendor will respond

Step 2: Extract feature importances
        → "photos_viewed" has 2.3x impact
        → "distance < 5km" has 1.8x impact
        → "ticket_value > ₹500" has 1.5x impact

Step 3: Translate to step-weight formula
        score = (photos_viewed * 2.3) + (distance_bucket * 1.8) + (value_bucket * 1.5) + ...

Step 4: Deploy the formula as config variables in the Java service
        → No ML inference servers needed
        → No model versioning needed
        → Can be updated by changing config
```

**Follow-up survival:**
- *"How did you bucket non-linear continuous variables like distance?"*
  → XGBoost's decision trees naturally split continuous variables at thresholds. You extracted these split points: 0-3km = score 3, 3-5km = score 2, 5-10km = score 1, >10km = score 0. These became the "steps" in your step-weight formula.
- *"How often did the weights degrade?"*
  → You retrained the XGBoost monthly and compared new feature importances to the deployed weights. If the delta was >15% on any feature, you updated the config. In practice, the weights were stable for 2-3 months at a time.
- *"Why not just deploy the XGBoost model directly?"*
  → Three reasons: (1) No ML serving infrastructure existed. Building one was a 3-month project. (2) The linear formula captured ~90% of the ML model's predictive value. (3) The formula was fully interpretable — you could explain to stakeholders exactly why lead X ranked higher than lead Y. With XGBoost, it's harder to explain.

---

## PART 5: OBSERVABILITY & DEBUGGING PATTERNS

---

### 22. Cohort Analysis (S026)
**What you said:** "Cohort analysis ruled out fatigue."

**Plain English:** Grouping users by when they were acquired and tracking their behavior over time. If your January cohort and February cohort both show declining conversion at the same rate, it's fatigue. If only older cohorts decline while new ones are fine, something is systematically dropping old users.

**In your silent bug story:**
- Conversion spiked (new feature worked) but slowly eroded.
- Cohort analysis showed: newer vendor cohorts maintained conversion. Older vendor cohorts were disappearing from the targeting pool.
- This pointed to a data issue affecting existing vendors, not a feature degradation issue.

---

### 23. SameSite Cookie Conflict (S021)
**What you said:** "Legacy JS on marketing pages clashed with new SameSite cookie policies inside WebView."

**Plain English:** Cookies are small files websites store in your browser (for login sessions, preferences, etc.). `SameSite` is a security attribute that controls whether cookies are sent with cross-site requests.

**What happened:**
- Chrome and Android WebViews (like Google Search App's in-app browser) started enforcing `SameSite=Lax` by default.
- Your login pop-up set a session cookie. But when users arrived via the Google Search App, the WebView treated JD's marketing pages and the login pop-up as "different sites."
- The WebView blocked the cookie → login appeared to work but the session wasn't maintained → users couldn't complete actions.
- On regular Chrome, it worked fine because both pages were on the same domain.

**Follow-up survival:**
- *"How did you structure the Kibana query to identify this?"*
  → Filtered login events by `user_agent` containing "GSA" (Google Search App) and compared success rates to Chrome. GSA showed 45% failure vs. 8% for Chrome. This took you directly to the WebView issue.

---

### 24. Publisher-Side Schema Validation (S026)
**What you said:** "Built publisher-side asynchronous schema validation."

**Plain English:** Instead of only validating messages when the consumer receives them, you validated them at the publisher (sender) side before they even entered the event bus.

**Why "publisher-side" matters:**
- Consumer-side validation means bad messages travel through the entire pipeline before being caught.
- Publisher-side validation catches them at the source, preventing pollution of the entire event stream.
- "Asynchronous" means the validation didn't block the billing monolith's main thread — it ran in a background process.

---

## PART 6: QUICK-REFERENCE CHEAT CARD

**If an interviewer asks "why X over Y," here's your instant pattern:**

| They ask about... | You rejected... | Your reason in one sentence |
|---|---|---|
| Facade pattern | Full rewrite | "We couldn't afford 12 months; the facade let us ship in 3 weeks" |
| Saga pattern | Two-phase commit (2PC) | "2PC locks all services simultaneously — doesn't work at marketplace scale" |
| Database-per-service | Shared database | "Blast radius isolation — one bad query shouldn't take down checkout" |
| pgvector | Elasticsearch | "5K categories didn't justify new infrastructure; pgvector was already in our Postgres" |
| Rule-based matching | ML model | "500 nodes, <100 examples per leaf — ML would overfit; rules were deterministic" |
| Pessimistic locking | Optimistic locking | "High-contention scenario — agents wasting 5 min only to get a conflict is worse" |
| Fail-open | Fail-closed | "Showing stale results > showing nothing; fail-closed is for security, not search" |
| Step-weight formula | Deploy XGBoost | "No ML infra existed; the formula captured 90% of value at zero ops cost" |
| Isolated analytics DB | Read-replica | "Needed different indexes and pre-aggregated tables that would bloat the live DB" |
| URI versioning | No versioning | "4 teams consuming one API — any breaking change would cascade to all 4" |
| Anti-corruption layer | Update legacy system | "Different org owned legacy; their release cycle was 3-6 months" |
| Async processing | All-sync | "Blocking the user for 3 seconds on 4G killed conversion — async + fallback was the right trade-off" |

---

## PART 7: TERMS YOU SHOULD KNOW BUT HAVEN'T USED YET
*(Likely follow-up territory)*

**Rate Limiting:** Controlling how many requests a service accepts per second. You implicitly used this in S024 (OTP rate limits being consumed by marketing).

**Horizontal vs. Vertical Scaling:**
- Horizontal: add more machines (what you did with matchmaking microservices in S008).
- Vertical: make one machine bigger (more RAM/CPU). Cheaper but has a ceiling.

**SLA (Service Level Agreement):** A contract defining uptime/performance guarantees. You mentioned 99.99% uptime in S004 — that means <52 minutes of downtime per year.

**Canary Deployment:** Rolling out to 5-10% of traffic first, monitoring, then expanding. You should have done this in S019 (the caller ID experiment) — it would have limited the damage.

**Feature Flags:** Toggles that let you turn features on/off without deploying new code. Useful for your A/B tests (S022) and gradual rollouts.

**Webhook:** A "reverse API" — instead of you polling a service for updates, the service calls your URL when something happens. You used this implicitly with WhatsApp delivery notifications.
