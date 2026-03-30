# Amazon LP Stories — Revision Guide
**Piyush Deveshwar | EMXO Sr. PM Loop | 22 Stories**

---

## Quick Reference Table

| Story | Title | Company | Key Metric | LPs |
|-------|-------|---------|-----------|-----|
| S001 | Zero-to-One P&L: JD Xperts | Justdial | ₹4.8cr ARR, 5.4x unit economics | Ownership, Deliver Results, Think Big, Bias for Action, Customer Obsession |
| S003 | LLM Search Engine | Justdial | 11%→2% failure, 90K leads/day | Customer Obsession, Invent and Simplify, Dive Deep, Learn and Be Curious |
| S004 | Shared OMS Architecture | Justdial | 3 months→3 weeks launch time | Invent and Simplify, Think Big, Are Right A Lot, Have Backbone |
| S005 | Lost Potential Bookings KPI | Justdial | Onboarding 8.6%→14%/month | Are Right A Lot, Dive Deep, Have Backbone |
| S006 | Cancellations Fix | Justdial | 20%→3% cancellations, NPS -12→+28 | Customer Obsession, Highest Standards, Dive Deep |
| S007 | LTV Analysis → Delayed Launch | Urban Company | Price-gouging 28%→4%, rating 4.8 | Earn Trust, Have Backbone, Are Right A Lot, Highest Standards |
| S008 | AC Repairs Scaling | Urban Company | 6x growth, ₹1cr revenue, 190K users | Bias for Action, Deliver Results, Ownership, Are Right A Lot |
| S009 | Self-Serve Vendor Platform | Justdial | ₹13cr revenue unlock | Ownership, Deliver Results, Customer Obsession, Dive Deep |
| S010 | Frugal MVP: Deals & Offers | Justdial | 28K users/day, ₹12cr projected | Frugality, Bias for Action, Invent and Simplify, Think Big |
| S011 | Vertical Marketplace (Interior) | Justdial | 60% CTR, 31% faster response | Think Big, Have Backbone, Customer Obsession, Dive Deep |
| S012 | Headless Booking Engine | Justdial | 48% order growth, 42% conversion | Invent and Simplify, Think Big, Deliver Results, Bias for Action |
| S013 | CRM-Lite from Scratch | Justdial | -37% negative reviews, +22 CSAT | Customer Obsession, Invent and Simplify, Frugality, Highest Standards |
| S015 | Indian Music Diaries | Side Project | 100K users/month, PageSpeed 50→90+ | Learn and Be Curious, Dive Deep, Frugality, Ownership |
| S017 | Category Exploration Pages | Justdial | Leads 23K→36.7K/day (59% increase) | Customer Obsession, Dive Deep, Deliver Results, Are Right A Lot |
| S018 | Dance Category Segmentation | Urban Company | CAC ₹2,700→₹1,800, connect rate +71% | Customer Obsession, Dive Deep, Are Right A Lot, Deliver Results |
| S019 | Failure: Phone Connect Rate | Justdial | Connect rate dropped 74%→71% | Ownership, Learn and Be Curious, Dive Deep, Earn Trust |
| S020 | AI Lead Salvaging | Justdial | 8K leads/day salvaged, VSAT 81%→83.5% | Customer Obsession, Invent and Simplify, Deliver Results, Dive Deep |
| S021 | Login Pop-up Debugging | Justdial | Login success 92%→85%→93% | Dive Deep, Customer Obsession, Are Right A Lot, Ownership |
| S022 | Merchant Metrics A/B Test | Justdial | Prevented bad rollout for 70% vendors | Are Right A Lot, Dive Deep, Bias for Action, Customer Obsession |
| S023 | Day Pass 4G Debugging | Justdial | Fixed sync rendering cascade on 4G | Bias for Action, Dive Deep, Frugality, Invent and Simplify |
| S024 | OTP Failure: Notification Gateway | Justdial | Zero OTP outages post-gateway | Dive Deep, Ownership, Highest Standards, Customer Obsession |
| S025 | ML Lead Ranking (XGBoost) | Justdial | Response rate ~35%→~42% | Invent and Simplify, Learn and Be Curious, Are Right A Lot, Hire and Develop |
| S026 | Silent Banner Targeting Bug | Justdial | Conversion 0.007%→0.018% recovered | Dive Deep, Customer Obsession, Highest Standards, Ownership |

---

### S001 — Zero-to-One P&L: JD Xperts to ₹4.8cr ARR (5.4x Unit Economics)
**LPs**: Ownership, Deliver Results, Think Big, Bias for Action, Customer Obsession | **Company**: Justdial

**HOOK**: "I was the first hire for a new business line at Justdial. I built it from zero to ₹4.8cr ARR with 5.4x unit economics over 2.5 years."

**SITUATION**: 2020 — Justdial's ad revenue (~₹800cr annually) was declining as advertisers shifted to Google/Meta. Users were already searching for home services — 15,000+ daily searches with no transactional product. High-quality vendors wanted a better channel than banner ads but Justdial only offered lead generation at ~₹50 per connection event.

**TASK**: I was the first hire. I negotiated from business lead to product + business lead. I needed to build the full org (~25 people), own the P&L end-to-end (revenue, costs, margins, vendor economics), and prove the model within the existing org with no separate budget.

**ACTION**:
1. I leveraged Justdial's existing organic traffic from 300M+ users instead of spending on marketing — user CAC near-zero, the structural advantage that made unit economics work.
2. I chose a hybrid architecture — plugged into JD's existing app shell, CMS, user auth, and notification systems while building independent microservices for everything order-critical. I defined a facade pattern to securely verify existing user session tokens via a lightweight internal auth service, keeping our microservices completely decoupled.
3. I shifted the model from handshake (₹50 per connection) to commission-on-completion. Average ticket ₹1,100-1,200, blended revenue ₹270/order — 5.4x the legacy model. CAC <₹200, LTV ₹1,080.
4. I invested in granular skill-tag matching to ensure vendor-job fit — the quality foundation the business model required.
5. I led the case for shared OMS infrastructure to collapse launch times for future verticals.

**RESULT**:
- ₹4.8cr ARR (~$580K) over ~2.5 years, closing at 490-500 orders/day
- 5.4x unit economics (₹270 revenue vs. ₹50 legacy per transaction)
- 5,000+ paying customers
- Vendor retention: 60% → 82%
- Platform ratings: 4.1 → 4.7
- Net NPS: 45
- Quarterly repeat users: 6% → 19%
- Shared OMS enabled 4 verticals at dramatically reduced launch time

**KEY DECISION**: Commission-on-completion over higher-volume lead gen model — quality over quantity. Every bad match, every cancellation costs us money. That alignment makes the product better.

**EARNED SECRET**: "The ₹4.8cr ARR was built on zero customer acquisition cost — we leveraged Justdial's existing 300M+ organic traffic instead of brute-force sales."

**TECHNICAL DEPTH**: Java microservices, MySQL, Elasticsearch for vendor search/matching, Redis for caching booking state, WhatsApp Business API. Core services: Booking Engine, Matchmaking Service (skill-tag based with rating + distance + availability scoring), Vendor Management, Shared OMS (REST APIs), Settlement Service (async ledger with weekly batch reconciliations). Shared OMS: 6 weeks upfront → 65% reduction in new vertical launch time.

---

### S003 — Solving 11% Search Failure with LLM Engine
**LPs**: Customer Obsession, Invent and Simplify, Dive Deep, Learn and Be Curious | **Company**: Justdial

**HOOK**: "I cut search failure from 11% to ~2% and generated 90,000 high-intent leads daily from previously dead traffic using a fine-tuned LLM engine."

**SITUATION**: Justdial processed millions of searches daily, but 11% were failing — ~1-1.5 lakh searches. 3% true failures (zero results), 8% returned poor-quality results. Failures clustered into 4 buckets: misspellings, colloquial/local language spellings, free-text natural language queries, and Hindi/Hinglish code-switched text.

**TASK**: Fix search failure rate. I owned end-to-end solution, led cross-functional team of 8 across product, engineering, and data.

**ACTION**:
1. I evaluated 3 options: (a) expand rules-based dictionary — rejected, can't enumerate Hinglish variants. (b) Google Vertex API — strong quality but per-query cost at 1L+ daily failures was unworkable. (c) Fine-tune in-house model.
2. I chose option 3 and repurposed existing internal LLM entity extraction service (built for phone call transcripts — Whisper pipeline) as an independent search service.
3. I designed a 5-step pipeline: query interceptor (fail-open at 250-300ms) → async queue → Llama 3.2 intent extraction → pgvector semantic matching with ElastiCache caching → WhatsApp retargeting "Did you mean ___?" (40% blended CTR). If the LLM hallucinated an intent that didn't match our strict vendor category taxonomy whitelist, the system discarded the output. I implemented a strict TTL hop-counter of 1 to prevent infinite retry loops.
4. I evolved unit economics: external LLM API → cheaper hosted model → fully in-house fine-tuned Llama 3.2. Moving in-house fixed Hinglish quality.
5. Staged rollout: batch-tested on previous week's failed queries, manually QA'd, then small app traffic percentage, then two cities.

**RESULT**:
- Search failure: 11% → ~2%
- 90,000 high-intent leads daily from ~50,000 unique users via WhatsApp retargeting (~40% blended CTR)
- Turned previously dead search traffic into the highest-volume lead generation channel
- In-house model: <₹0.05/query marginal cost, 2-month payback

**KEY DECISION**: In-house fine-tuning over Google Vertex API — cost + quality control. General models handled Hinglish code-switching poorly because they'd never been trained on India's local search patterns.

**EARNED SECRET**: "Most teams treat their LLM cost problem as procurement — negotiate better API rates. I treated the model as a product I owned."

**TECHNICAL DEPTH**: Python (LangChain), Llama 3.2 (fine-tuned for Hinglish), pgvector (semantic matching), ElastiCache, Elasticsearch, RabbitMQ async queue, WhatsApp Business API. P90 latency ~150ms. 8-person team (2 ML engineers, 3 backend, 1 data analyst, 1 QA, PM). Feedback loop cached high-ranking keywords back into Elasticsearch to improve base search.

---

### S004 — Foreseeing the Bottleneck: Shared OMS Architecture
**LPs**: Invent and Simplify, Think Big, Are Right A Lot, Have Backbone | **Company**: Justdial

**HOOK**: "I identified that 4 teams were independently rebuilding the same infrastructure and led the case for shared microservices — cutting new vertical launch time from 3 months to 3 weeks."

**SITUATION**: JD Xperts was built as a monolith. Meanwhile, Justdial was spinning up parallel product pods (doctors, insurance, laundry). 4 teams were duplicating order management, notifications, vendor management — burning ~12 engineering-months of duplicated effort, with hiring projected at upwards of ₹2cr in additional costs.

**TASK**: I noticed the problem while helping hire for other teams. I recognized every future vertical would rebuild the same components and advocated for shared microservices instead.

**ACTION**:
1. I mapped what was category-specific vs. reusable: user management, scheduling, order management, and customer experience were nearly identical across verticals.
2. I built the case to the CPO — with significant pushback from other team leads who wanted autonomy. I argued a slight increase in system complexity would give us a 10x multiplier in go-to-market speed. I agreed to implement strict SLAs and decoupled databases to isolate the blast radius.
3. I paused individual builds and spent 4 months building 4 shared microservices: User Management, Configurable Scheduling, OMS, and Customer Experience module. Designed with graceful degradation.
4. I mandated URI versioning for major breaking changes and additive schema evolution for minor ones. For cross-domain order consistency, I opted for Eventual Consistency using a Saga pattern with compensating transactions.

**RESULT**:
- New vertical launch time: ~3 months → ~3 weeks (65% reduction)
- Enabled 4 new business lines (including JD Loans — #1 priority)
- Uptime: 99.9% → 99.99%
- Bug rate for new category launches: down 35%
- 4-month investment that saved 12 eng-months + ₹2cr/year

**KEY DECISION**: Per-service databases (database-per-service pattern) over shared DB. Eliminated cross-vertical deployment dependencies. Accepted 4-month upfront investment for 10x future velocity multiplier.

**EARNED SECRET**: "The hardest part wasn't the architecture — it was the org politics. Team leads didn't want to depend on shared services they didn't control."

**TECHNICAL DEPTH**: Java microservices, MySQL (per-service databases), REST APIs with versioned contracts, Nginx for API gateway/load balancing. Saga pattern with compensating transactions for eventual consistency. Graceful degradation: if Customer Experience module (reviews) went down, core orders still processed. Versioned REST APIs — new verticals simply plugged in.

---

### S005 — Inventing "Lost Potential Bookings" KPI
**LPs**: Are Right A Lot, Dive Deep, Have Backbone | **Company**: Justdial

**HOOK**: "I invented a new metric — Lost Potential Bookings — that shifted the org from reactive to proactive supply expansion and increased onboarding growth from 8.6% to 14% per month."

**SITUATION**: JD Xperts was doing 130-140 orders/day, growing at 8.6% MoM in onboarding. Conversion funnels looked steady at daily/weekly averages. But customer calls told a different story: users couldn't find slots, availability was patchy. Daily averages were masking localized capacity gaps.

**TASK**: I needed real-time visibility into when/where demand exceeded supply, and a way to calculate how many vendors were actually needed on the ground. I needed to capture high-signal data without slowing down the live checkout process.

**ACTION**:
1. I looked at data at hourly granularity. Confirmed hypothesis — daily/weekly averages were hiding localized spikes.
2. I led development of a standalone analytics system: an async event pipeline feeding a structurally isolated PostgreSQL database, processed by a 3-hour cron job outputting to a static HTML dashboard. I used a non-blocking "fire-and-forget" queue payload so the main checkout thread never waited.
3. Two critical trade-offs: (a) Isolation over Simplicity — decoupled analytics DB from core transactional system. (b) Speed over Perfect Architecture — chose dedicated PostgreSQL over internal ClickHouse (would have taken 3 weeks via central data team). 3-hour batch over real-time — matched stakeholder decision-making cadence.
4. I created the "Lost Potential Bookings" metric: LPB = Visitors on slot page x (benchmark max conversion - actual conversion). Simple enough for sales teams to act on.

**RESULT**:
- Hub-wise demand growth: 9.6% → 12%
- Slot page conversion: ~12% → ~14%
- Onboarding growth: 8.6% → 14% per month
- Revenue improved by ~₹3L/month
- Org shifted from reactive to proactive supply-driven expansion

**KEY DECISION**: PostgreSQL over ClickHouse — stop the bleeding now (days vs. 3 weeks). Isolated DB over shared — protect live checkout. 3-hour cron over real-time — matched stakeholder decision cadence.

**EARNED SECRET**: "Averages are the most dangerous metric in a marketplace. They make you feel fine while you're starving specific zones of supply."

**TECHNICAL DEPTH**: Async event pipeline, dedicated PostgreSQL instance (isolated from core transactional DB), 3-hour cron job, static HTML dashboard. Events enriched with pin code, GPS location, campaign referrer links at hub x time-of-day granularity. Automated alerts to city sales managers when LPB exceeded threshold for 3+ consecutive hours.

---

### S006 — Cancellations 20% to 3%, NPS -12 to +28
**LPs**: Customer Obsession, Insist on the Highest Standards, Dive Deep | **Company**: Justdial

**HOOK**: "I dropped vendor-side cancellations from 20% to 3% and flipped NPS from -12 to +28 by discovering it was a skill mismatch problem, not a vendor quality problem."

**SITUATION**: A few months into JD Xperts, daily cancellations stood at 30-35% overall, with vendor-side cancellations at 20%. With 95% new customers, every cancellation meant 100% churn. 45% of ops bandwidth was consumed managing this.

**TASK**: Find and fix the root cause of cancellations to make the commission-on-completion model viable.

**ACTION**:
1. I bypassed aggregate dashboards. Pulled raw cancellation logs and cross-referenced with customer support transcripts and vendor feedback.
2. I sliced data by vendor ID x item SKU. Found the blind spot: sub-variant complexity. A vendor trained on standard ACs was being dispatched to an inverter split AC. Our system treated "AC Repair" as a flat, interchangeable skill — constantly setting vendors up to fail.
3. I built a hierarchical skill-matching system. Worked with appliance trainers to map complexity into a skill tree. Root: AC Repair → Branch: Split vs. Window → Leaf: Inverter vs. Non-inverter. Built vendor questionnaires to map the existing fleet to leaf nodes. Back-tested historical ratings against specific appliance variants.
4. I implemented rule-based matching with tree traversal. Technical implementation took 15 days (2 sprint cycles). Ran batched city experiment first, validated, then rolled out broadly.

**RESULT**:
- Vendor cancellations: 20% → 3%
- NPS: -12 → +28
- Blended new-user churn: 76% → 66%
- Ops intervention rate: 45% → 25%
- Vendor utility: 1.2 → 1.7 jobs/day

**KEY DECISION**: Rule-based over ML — faster to ship (15 days), interpretable, worked with noisy (high-cancellation) data. Accepted a few ms tree-traversal latency for dispatch accuracy.

**EARNED SECRET**: "The data initially misled us. Not 'who is good?' but 'who is good at THIS?'"

**TECHNICAL DEPTH**: MySQL for vendor skill profiles, rule-based matching engine (Java), phone-call verification pipeline. Hierarchical tree structure: Root → Branch → Leaf taxonomy. To prevent gaming, skill-tags triggered mandatory 4-5 question quizzes, cross-referenced with historical ratings. ~2,000+ vendors re-profiled with granular skills.

---

### S007 — LTV Analysis: Delaying Launch to Protect Customer Trust
**LPs**: Earn Trust, Have Backbone, Are Right A Lot, Highest Standards | **Company**: Urban Company

**HOOK**: "I convinced the Business Head and Marketing Head to delay a category launch by showing that every price-gouged customer would cost the business ₹200 — a ₹650 swing per customer vs. a happy one."

**SITUATION**: Urban Company, ~2019-2020. Business Head and Marketing Head wanted to launch RO (water purifier) vertical fast with a flat ₹249 lead-gen model, 15-day timeline. My demand analysis showed "service" queries outweighed "repair" 6:1. Service ticket was ~₹2,100 vs. ₹249 for repair — nearly 9x gap. ARPO was ₹1,700, compared to ~₹350 for other repair categories. Historical data showed price-gouging was the second-largest complaint category at 28%.

**TASK**: I found a problem leadership hadn't seen and had to decide whether to raise it, knowing it would delay a launch they'd already committed to.

**ACTION**:
1. I identified demand composition was inverted. Service demand was 6x repair — this was a high-ticket, variable-pricing category being launched as if it were a low-ticket commodity.
2. I turned opinion into arithmetic. Great experience: LTV ≈ ₹450. Complaint resolved via revisit: LTV ≈ ₹190. Price-gouging complaint: LTV ≈ -₹200 (NPS -20, 100% churn). ₹650 swing per customer.
3. I challenged leadership directly: "Give me a stronger reason to launch immediately versus a one-week delay that guarantees a better on-ground experience." I reframed from "speed vs. quality" to "unprofitable vs. profitable growth."
4. I built during the extra week: strict upfront pricing SKUs, billing spike trackers, city x service-type pricing grids published upfront.

**RESULT**:
- Launched in 3 weeks instead of 15 days — just 7-8 extra days
- RO category rating: 4.8 (highest on platform)
- Overall complaint rate: 5% → 3.45%
- Price-gouging complaints: 28% → 4%
- MoM growth: 12% from month 2 (vs. 9.5% comparable categories)
- ARPO ₹1,700 (vs. ₹350 for other repair categories — ~5x higher value)

**KEY DECISION**: 7-8 extra days for fixed-price system. Math showed near-immediate breakeven vs. weekly LTV destruction at 28% gouging rate.

**EARNED SECRET**: "Leadership was optimizing for acquisition. I was optimizing for lifetime value. When you show ₹650 swing per customer, the argument becomes arithmetic."

**TECHNICAL DEPTH**: SQL-based LTV cohort analysis on data warehouse, financial modeling for LTV by complaint type, city x service-type pricing grid system, billing spike tracker monitoring vendor billing patterns across weeks/months, vendor accountability dashboard.

---

### S008 — Scaling AC Repairs: 6x Growth, ₹1cr Revenue, 190K New Users
**LPs**: Bias for Action, Deliver Results, Ownership, Are Right A Lot | **Company**: Urban Company

**HOOK**: "I turned seasonal risk into the lowest-CAC acquisition window of the year — 6x growth, ₹1cr revenue from a single category, 190K new users at 1/3rd the business average CAC."

**SITUATION**: Urban Company, AC repair demand spikes 4-5x every Indian summer. The org treated seasonality as risk. As P&L owner for appliance repair, I realized this spike was actually our lowest-CAC acquisition window. AC repair users have high LTV because they repeat across other appliance categories.

**TASK**: Build a predictable, scalable framework across operations, supply, and engineering to capture this latent demand without systems or service quality buckling under 6x load.

**ACTION**:
1. I built a predictive demand model ingesting 20 months of historical order data, weather spike correlations, and top-of-funnel metrics to generate exact vendor acquisition targets per city.
2. I ran failure mode analysis on supply alignment. Differentiated supply needed for longer periods vs. peak-only. Structured tiered vendor pools backed by Minimum Business Guarantees (MBGs).
3. I defined Non-Functional Requirements for 6x load. Specified latency thresholds, projected traffic shape, established business logic for supply isolation. Worked with engineering to isolate, stress-test, and independently scale matchmaking and service catalog display microservices.
4. I created early-bird discount campaigns to flatten the demand curve — shifted 30% of peak bookings to shoulder weeks, keeping vendor utilization at ~80% throughout season.

**RESULT**:
- 6x growth in orders served, zero system downtime
- ₹1cr revenue from a single category (record-breaking)
- 190K new users added to platform (highest to date)
- CAC 1/3rd the business average
- NPS ~12 maintained throughout

**KEY DECISION**: Demand shaping over supply scaling — kept vendor utilization ~80% vs. hiring 2x for 2-month spike. Microservice isolation over monolith scaling — targeted specific bottlenecks.

**EARNED SECRET**: "Seasonal categories look risky because demand is peaky. But if you can shape demand with early-bird incentives and build supply resilience with vendor lock-in models, the peaks become your advantage."

**TECHNICAL DEPTH**: City-wise demand estimation from 20 months historical + weather + search data. Vendor tiering: Tier 1 exclusives with MBGs, Tier 2 on-call, Tier 3 overflow. Independently scaled matchmaking service and service catalog display for 6x volume. Demand shaping shifted 30% of peak bookings to shoulder weeks.

---

### S009 — Self-Serve Vendor Platform: ₹13cr Revenue Unlock
**LPs**: Ownership, Deliver Results, Customer Obsession, Dive Deep | **Company**: Justdial

**HOOK**: "I discovered that ~50% of app users were actually businesses, built self-serve monetization for them, and unlocked ₹13cr in revenue from categories that were structurally unprofitable under a sales-led model."

**SITUATION**: Justdial's apps had lower engagement than web. All vendor advertising sold through offline/direct sales. Product-driven advertising was 0.5% of total (~₹1.5cr on ~₹65cr app ad base). While diving deep into user data, I discovered that ~50% of app users were actually business owners — vendors.

**TASK**: I dug into why and found a structural flaw: for distant vendors and lower-ticket categories, the cost of a sales call completely wiped out the potential revenue. This massive vendor segment was systematically ignored. I needed to collapse the cost of acquisition and unlock the long tail.

**ACTION**:
1. I reframed the problem: not "why is app engagement lower?" but "why are we serving two completely different user types with one product?"
2. I built self-serve capabilities: contextual prompts on search results ("You can buy this position"), direct purchase of customized lower-ticket packages — no sales call required.
3. I built a detailed package management system integrated with billing. Automatic flagging of vendor accounts based on lifecycle state, triggered granular targeting for renewals and upsells.
4. Self-serve dropped cost-of-sale to near zero, making the long tail economically viable for the first time.

**RESULT**:
- App advertising revenue: ~₹65cr → ~₹78cr (₹13cr incremental unlock)
- Run rate: ₹1.25cr/week → ₹1.5cr/week
- Saved ~5% commission on ₹65cr channel
- 3x higher conversion on contextual prompts vs dashboard approach in A/B test
- Made "hidden" vendor segment profitable to serve for the first time

**KEY DECISION**: Contextual prompts into existing search results vs. separate vendor dashboard. Contextual prompts intercepted vendors at moment of intent — 3x higher conversion in A/B test.

**EARNED SECRET**: "When you remove the sales team as intermediary, cost-of-sale collapses and the long tail becomes economically viable for the first time. That's not a growth hack — that's a structural shift."

**TECHNICAL DEPTH**: Java backend, MySQL for ad inventory/transactions, Redis for real-time bid/position caching. Vendor Segmentation Engine (behavioral analysis identifying vendors from app usage patterns). Contextual Ad Prompt Service (rule-based, intercepting at moment of intent). Package Management System with billing integration pipeline. Self-serve purchase flow end-to-end without sales call.

---

### S010 — Frugal MVP: Deals & Offers to 28K Daily Users, ₹12cr Projected Revenue
**LPs**: Frugality, Bias for Action, Invent and Simplify, Think Big | **Company**: Justdial

**HOOK**: "I validated a ₹12cr annual revenue opportunity by building a CSV-upload CMS that got us to 28K users/day at near-zero incremental engineering cost."

**SITUATION**: At Justdial, I surfaced data on offers that local vendors were already listing. I analyzed offer-related keyword search volumes and estimated we could capture ~2 million additional daily organic visits. Leadership agreed to let me execute only if I could do it without impacting existing timelines.

**TASK**: Validate the opportunity with near-zero incremental engineering investment.

**ACTION**:
1. I designed a zero-new-infrastructure MVP reusing existing components — same results page skeletons, card layouts, rendering pipeline. Only net-new: a lightweight offer data model and routing logic.
2. I built a CSV-based content pipeline. Marketing could bulk-populate offers. Strict validation layer — if a single field violated regex conditions, the entire batch was rejected (fail-safe) to prevent partial data corruption.
3. I leveraged marketing as the content engine. They had bulk offer details from large brands — exactly the structured, keyword-rich content needed to rank. Created roughly 9,000 brand pages.
4. I optimized for crawlability from day one — sitemap, meta tags, structured data.

**RESULT**:
- ~28,000 daily users within 4 months
- 9,000 brand pages created
- Near-zero incremental engineering capacity consumed
- Validated ~2M daily traffic opportunity (₹12cr annual revenue projected)
- Early traction secured full vertical investment from leadership

**KEY DECISION**: Reuse + CSV pipeline over purpose-built product. At validation stage, the question was "will this traffic convert?" not "can we scale?"

**EARNED SECRET**: "The MVP wasn't a smaller version of the final product — it was a completely different architecture designed to answer one question: will this audience convert?"

**TECHNICAL DEPTH**: Existing Justdial APIs, CSV-upload CMS with strict regex validation (fail-safe batch rejection), SEO page generation pipeline, Google Search Console for keyword tracking. Deliberately manual — faster to ship than automated brand integration.

---

### S011 — Vertical Marketplace for Interior Design & Construction
**LPs**: Think Big, Have Backbone, Customer Obsession, Dive Deep | **Company**: Justdial

**HOOK**: "I proved that vendor churn wasn't an engagement problem — vendors needed a vertical marketplace to source materials and close deals. Marketplace pages hit 60% CTR and dropped time-to-response by 31%."

**SITUATION**: In high-ticket categories, Justdial was losing vendors — churn crept from ~14% to 17% per quarter over 3 years. Leadership proposed engagement features (reels). But after extensive vendor interviews, the real picture emerged: vendors saw Justdial as "just a marketing platform" while competitors helped them close and convert. Justdial had all the ingredients (supplier listings on JD Mart, calculators, B2B catalog) — just hadn't collated them.

**TASK**: Push back on the engagement features diagnosis. The CPO had already committed to reels. I had to advocate for a fundamentally different product.

**ACTION**:
1. I proved the real root cause with data. Vendor interviews confirmed they used other platforms to source materials. Our previous billing/estimates feature failed because it was isolated from the supply ecosystem.
2. I pushed back on reels — presented data to CPO showing engagement features would generate vanity metrics but not retention.
3. I built and tested an MVP (4-5 week effort). Created a searchable marketplace extension from JD's B2B platform. Solved matching on time to deliver (proxied via geographic distance + historical supplier ratings) and best available prices.
4. I tested with ~1,500 vendors in a single city — interior designers, contractors, architects.

**RESULT**:
- Marketplace pages: ~60% blended CTR
- Time to response in interiors: down 31%
- Vendor-side revenues: +11% YoY
- Enquiries generated: +5%
- Suppliers got actual orders for the first time

**KEY DECISION**: Vertical marketplace over engagement features (reels). Previous billing feature failed in isolation — marketplace succeeded by connecting estimates to supply ecosystem.

**EARNED SECRET**: "Vendors aren't social media users — they're businesses. They don't want reels; they want to find their cement dealer faster."

**TECHNICAL DEPTH**: JD Mart B2B APIs for supply catalog, searchable marketplace extension with design/style/material filters, estimate builder, supplier matching engine (time to deliver via distance proxy + best price), client-facing estimate sharing flow. Three-sided marketplace: vendor → supplier → end customer.

---

### S012 — Headless Booking Engine: Unlocking Call Center Channel, 48% Order Growth
**LPs**: Invent and Simplify, Think Big, Deliver Results, Bias for Action | **Company**: Justdial

**HOOK**: "I built a headless booking engine that unlocked the call center as a distribution channel — 48% order growth in 3 weeks, with 42% conversion rate (nearly double the app)."

**SITUATION**: At Justdial, 28% of all leads came from users calling directly — a high-intent cohort. But satisfaction was 2.8-3.2 vs. 4.2 for online JD Xperts users. Same-category repeat for callers was below 5%. The call center operated on a legacy text-based console with a 52-second average call time that couldn't render any modern web interface.

**TASK**: Give this 28% of high-intent callers access to JD Xperts managed experience without rebuilding legacy infrastructure.

**ACTION**:
1. I chose the pragmatic path: translation layer (weeks) over deep integration (months of admin blockers).
2. I built a headless booking engine with translation + anti-corruption layers. Created APIs converting between legacy call center XML and our modern JSON services. I defined an idempotency requirement: unique hash based on caller's phone number and 5-minute time window to prevent duplicate orders from agent refreshes/double-clicks.
3. I designed an async user journey via messaging. Key insight: callers don't need to complete everything on the phone. Order details transported to Xperts OMS, then pushed WhatsApp/SMS deep links. I kept deep links purely informational — no login wall for order status.

**RESULT**:
- Daily Xperts orders: 135 → 200 (48% growth) within 3 weeks
- Caller funnel conversion: 42-44% (vs. 23-24% web/app — nearly 2x)
- Customer satisfaction: 2.8 → 4.5
- CPA effectively near-zero — most profitable acquisition source

**KEY DECISION**: Translation layer (weeks) over full modernization (9-12 months). Async messaging journey rather than cramming into 52-second call.

**EARNED SECRET**: "The call center wasn't a legacy liability — it was an untapped distribution channel with 2x the conversion rate of our app."

**TECHNICAL DEPTH**: Java wrapper API, XML→JSON translation layer, Redis (short-lived cache for multi-turn booking state), WhatsApp Business API for async post-booking comms, idempotency layer. Anti-corruption layer prevented legacy data model from leaking into clean architecture. Phone call initiates; digital touchpoints complete.

---

### S013 — Building CRM-Lite from Scratch: -37% Negative Reviews, +22 CSAT
**LPs**: Customer Obsession, Invent and Simplify, Frugality, Highest Standards | **Company**: Justdial

**HOOK**: "I built a CRM-lite for ₹2L instead of buying Zendesk at ₹15-20L/year — dropped negative reviews 37% and cut first contact time from 24-48 hours to 2 hours."

**SITUATION**: As JD Xperts scaled, I had no CRM. The flow was broken: helpline agent → ticket for sales → Excel → ops agent eventually acted. Three handoffs, no context. Over 1,000 unclosed tickets, first response time exceeded 24 hours. At 350 orders/day with projected 100% YoY growth, this would completely collapse.

**TASK**: Build a scalable CRM-lite that gave ops agents instant context on call connect, eliminated manual handoffs, and reduced resolution time from days to hours.

**ACTION**:
1. I built an order-level complaint database with encrypted user lookup. When a call came in, system looked up caller's phone number, retrieved exact orders and complaint history, surfaced on ops dashboard instantly.
2. I chose frugal internal build over Zendesk/Salesforce — 6-month integration at significant cost vs. weeks at fraction of cost.
3. I built keyword-based auto-classification and routing. "Revisit"/"not fixed" → Ops queue; "late"/"delay" → Category queue; "refund"/"charged" → Refunds queue. Agent-driven tagging via dropdown — ~80% accuracy, no NLP needed.
4. I automated acknowledgment: every complaint triggered immediate WhatsApp acknowledgment. "Revisit" complaints auto-created follow-up vendor orders.
5. I enforced pessimistic locking at the application level — only one ops agent could be assigned to a ticket at a time.

**RESULT**:
- First contact: 24-48 hours → ~2 hours, most resolved in 6 hours, many in 2 hours
- Negative public reviews: -37% MoM
- Post-resolution CSAT: +22 points over 3 months
- Scaled orders 100% YoY without scaling ops team
- 1,000+ unclosed tickets cleared in first month

**KEY DECISION**: Internal build over Zendesk — fraction of cost, shipped in weeks. Encrypted translation layer over core system changes — bridged gap without admin blockers.

**EARNED SECRET**: "50% of negative reviews weren't about bad service — they were about feeling ignored. The cheapest intervention was acknowledgment."

**TECHNICAL DEPTH**: Internal ticket DB (MySQL), keyword-based classification engine (Java), WhatsApp Business API, encrypted translation layer bridging JD's core user management and Xperts' order system. Pessimistic locking for concurrent write prevention. Agent-driven tagging via dropdown (not AI text-parser).

---

### S015 — Indian Music Diaries: From Free Blog to 100K Users/Month
**LPs**: Learn and Be Curious, Dive Deep, Frugality, Ownership | **Company**: Side Project

**HOOK**: "I built and operate a 100K-user content platform as a side project — taught myself AWS, CDN, performance engineering, and saved ₹5-6L/year through self-management."

**SITUATION**: Indian Music Diaries is an indie music e-magazine — a friend's passion project I joined. Started as a free WordPress blog with minimal infrastructure, poor performance (PageSpeed ~50), and growing but unstable traffic.

**TASK**: Build and scale the platform from a hobby blog into a stable, performant content platform — handling traffic growth, performance, and cost optimization, all as a side project with no budget.

**ACTION**:
1. I drove progressive infrastructure evolution: Free WordPress → dedicated hosting (with web reliability engineer on retainer) → AWS Lightsail. I chose Lightsail for its EC2 migration path + stacked application server.
2. I implemented multi-layer caching: browser caching, object caching, server-side caching. These alone dramatically improved stability.
3. I consolidated multiple paid plugins into a single custom plugin — reducing overhead, conflicts, and annual licensing costs.
4. I learned infrastructure myself — hosting, caching, custom plugin development — saving over ₹5-6L/year. Server costs alone: ₹2,500 → ₹800/month. Bulk of savings from eliminating devops retainer and plugin licenses.
5. I implemented cache invalidation via WordPress hooks triggering API calls to purge CDN edge cache and local object cache for specific URLs on publish.

**RESULT**:
- Scaled to 100K monthly users
- PageSpeed: ~50 → 90+
- Saved ₹5-6L/year (includes devops retainer, plugin licenses, hosting)
- Hosting costs: ₹2,500 → ₹800/month
- Fully self-managed infrastructure

**KEY DECISION**: Lightsail over raw EC2 or managed hosting — right balance of control and ops overhead. Custom plugin over multiple paid plugins — upfront dev saved annual licensing.

**EARNED SECRET**: "Every PM should build and operate something end-to-end. Running infrastructure taught me what 'latency' actually feels like to a user."

**TECHNICAL DEPTH**: WordPress on AWS Lightsail (stacked application server), multi-layer caching (browser + object + server-side), custom PHP plugin, cache invalidation via WordPress hooks → CDN edge purge + local object cache purge per-URL. Optimized for mobile users on slow connections — image compression, lazy loading, CDN for Indian users.

---

### S017 — Category Exploration Pages: Leads 23K to 36.7K/day (59% Increase)
**LPs**: Customer Obsession, Dive Deep, Deliver Results, Are Right A Lot | **Company**: Justdial

**HOOK**: "I increased lead generation 59% — from 23K to 36.7K/day — by proving that adding qualifying friction to the user journey actually increased engagement."

**SITUATION**: While analyzing app UX, I found users searching but dropping off. Low-complexity keywords had lower conversion, filter usage was unusually high. Generic category searches (e.g., "Doctor") led to generic listing pages, but actual needs were far more specific. 98,000 daily clicks on homepage categories were being funneled into pages that couldn't differentiate intent.

**TASK**: Improve the user journey for broad-intent searches without disrupting existing flow. Goal: lift lead volume by >15%.

**ACTION**:
1. I identified two discovery gaps: (a) Category refinement — users search "Doctor" but need "Gastroenterologist." (b) Problem-first search — users search "hernia surgery" not "Doctor."
2. I navigated leadership pushback on friction. I presented external case studies on high-intent friction to secure buy-in for a controlled experiment.
3. I scoped a scrappy MVP — queried the "services provided" data that vendors had already supplied. Used this to map problem keywords to sub-categories. Category-specific modules varied by vertical (symptom checker for doctors, price calculator for repairs).
4. I chose "Packers and Movers" first — most straightforward taxonomy. Experiment proved adding friction did NOT cause drop-off.
5. I scaled to 11 additional categories. Enforced fixed dimensions for component containers to prevent CLS.

**RESULT**:
- Lead generation: 23,000 → 36,700/day (59% increase, far exceeding 15% goal)
- Blended CTR: ~37%
- Irrelevant lead feedback from vendors: 17% vs. 23% platform average (7pp better lead quality)
- 1 pilot → 12 categories

**KEY DECISION**: Dynamic template engine with 10 reusable components (configured per category) over one smart template. Single template would serve mediocre experience everywhere. CLS prevention via fixed container dimensions critical for mobile UX.

**EARNED SECRET**: "'Doctors' is actually 15 different user journeys wearing one label. The 59% lift came not from better design but from acknowledging variance in intent."

**TECHNICAL DEPTH**: Dynamic template engine using 10 reusable components configured via backend per category. Module framework: search refinement, price estimator, symptom/need checker, photo galleries, review highlights, cross-sell widgets. Per-category config defining which modules to show, order, data sources. Traffic volume x lead value scoring for category prioritization.

---

### S018 — Finding Product-Market Fit Through Customer Segmentation
**LPs**: Customer Obsession, Dive Deep, Are Right A Lot, Deliver Results | **Company**: Urban Company

**HOOK**: "I diagnosed a product-market fit failure in Urban Company's Dance category, identified 4 distinct customer segments, and dropped CAC 33% while surging connect rate 71%."

**SITUATION**: Urban Company Dance had high search volume but unsustainable economics: CAC ~₹2,700 (vs. ~₹1,900 benchmark), user-to-studio connect rate only 0.7. The category was bleeding money despite apparent demand.

**TASK**: Diagnose root cause and pivot. KPIs: (1) CAC under ₹2,000. (2) Connect rate above 1.0. (3) Improve studio satisfaction with lead quality.

**ACTION**:
1. My hypothesis: the "homogeneous demand" assumption was wrong. I was serving a generic product to a highly segmented market.
2. I personally interviewed 50 customers. Designed quantitative survey to validate at scale.
3. I identified 4 distinct segments: Parents (kids' classes), Fitness enthusiasts, Hobbyists/passion seekers, Event-based (wedding choreography).
4. I chose segment-level personalization — 4 distinct category funnels instead of a 1:1 personalization engine. Smaller lift, captured 80% of value.
5. I completely changed the discovery flow. Instead of "Dance → Find Studio", I routed "Fitness → Dance Studio", separating cohorts from click zero.
6. For events segment, I introduced at-home choreography — a completely new service format from understanding that segment's needs.

**RESULT**:
- CAC: ₹2,700 → ₹1,800 (33% reduction)
- Connect rate: 0.7 → 1.2 (71% surge)
- Studio quality rating: 2.3 → 4.2
- Entire initiative: ~3 weeks
- Became the blueprint at Urban Company for new category launches

**KEY DECISION**: 4 segment funnels over personalization engine — 80% of value in 20% of effort. At-home choreography = segment-specific product innovation.

**EARNED SECRET**: "High search volume with poor conversion isn't a marketing problem — it's a segmentation problem. 'Dance classes' is four markets wearing one label."

**TECHNICAL DEPTH**: 50 qualitative interviews → thematic coding → 4 segment hypotheses → quantitative survey validation. Segment-level funnels: each got distinct landing page messaging, search filters, studio matching criteria, pricing display. Marketing campaigns tagged by segment for CAC/conversion tracking. Studio quality feedback loop.

---

### S019 — Failure Story: Solving the Wrong Problem (Phone Connect Rate)
**LPs**: Ownership, Learn and Be Curious, Dive Deep, Earn Trust | **Company**: Justdial

**HOOK**: "I made the problem worse. My fixed-number caller ID system dropped connect rate from 74% to 71% — I'd given vendors a tool to filter us OUT."

**SITUATION**: Justdial's user-to-vendor phone connect rate sat at 74%. In vendor reviews and help centre complaints, I kept seeing "spam" — our caller identification numbers were showing up as spam in Truecaller.

**TASK**: Improve connect rate by making calls identifiable and trustworthy.

**ACTION**:
1. I designed a fixed-number caller ID system. Instead of cycling through ~100 masked numbers, I created 4-5 fixed numbers with recognizable names: "JD Lead," "JD Buyer," "JD Customer." Asked vendors to save them.
2. I launched and monitored. Expected immediate improvement.

**RESULT (FAILURE)**: After 3 days, pickup rate dropped from 74% to 71% — a 3pp drop. I made the problem worse.

**POST-MORTEM**:
1. I immediately reversed the change and took ownership.
2. I discovered multiple cascading failures: (a) Helper delegation — vendors with assistants stopped picking up saved "JD" numbers, assuming assistants would handle them. (b) Spam scaling — 4-5 fixed numbers got flagged worse because call volume concentrated. (c) Math killed it at scale — even 100% adoption would fail because non-vendors would spam-flag concentrated numbers.
3. The deeper learning: I had solved the wrong problem. The issue wasn't "identification" — it was "negative qualification." On-field interviews with ~100K worst-affected vendors confirmed: vendors were making rational economic decisions about which calls were worth their time.

**WHAT I DID NEXT**: Rolled back in 3 days (bottlenecked by telecom SLA). Increased CLIs from 100 to 600 (negligible cost — only paid per pulse). I implemented a data-driven circuit breaker: monitored pickup rates per CLI, if rolling 3-day average dropped below 10% threshold, automatically rotated that number out.

**KEY DECISION**: Fixed numbers for clear signal — got unambiguous negative result in 3 days. Eventually solved by expanding CLI rotation 6x + auto-removal of flagged numbers.

**EARNED SECRET**: "A broad assessment is not enough. The vendor who doesn't pick up isn't confused about who's calling — they're making a rational economic decision. Since then, I never ship a solution without first understanding the user's underlying incentive structure."

**TECHNICAL DEPTH**: Telephony system configuration, WhatsApp Business API for vendor outreach, internal analytics for pickup rate tracking by vendor cohort. Eventually: 100→600 CLIs in rotation, data-driven circuit breaker with rolling 3-day average threshold.

---

### S020 — AI-Powered Lead Salvaging: 8K Mismatched Leads/Day Recovered
**LPs**: Customer Obsession, Invent and Simplify, Deliver Results, Dive Deep | **Company**: Justdial

**HOOK**: "I discovered that 78% of vendor 'spam' flags were actually real leads going to the wrong vendor — I built an AI salvage engine that recovered 8,000 mismatched leads per day."

**SITUATION**: Justdial's paying vendors were flagging 80,000 calls/day as "irrelevant" or "spam." My deep dive into call transcripts revealed: 78% (~62,000) were high-intent users simply mismatched by the rigid keyword system — only ~18,000 were genuinely spam. VSAT at 81%, driving vendor churn.

**TASK**: Stop vendor churn and rebuild trust by proving lead quality wasn't the problem — matching was. Increase VSAT from 81% to >83%.

**ACTION**:
1. I designed business-driven traffic segmentation. GPU-bound — couldn't process all 80K in real-time. I used a pre-computed urgency matrix (category type x average order value) for routing. Focused expensive real-time processing on 25,000 daily calls with highest business impact; rest on cheaper async path.
2. I implemented "chunking" technique — keyword spotting to stop transcription early once intent identified. Reduced GPU compute by 75%.
3. I built LLM-powered intent extraction and rerouting. System extracted true intent from transcript, created correctly matched new lead. For salvaged leads, I appended "AI Verified User Intent" tag. If category was completely wrong, created net-new lead.

**RESULT**:
- ~8,000 leads/day salvaged and rerouted
- VSAT: 81% → 83.5%
- Revenue improvement: ~₹15L/month (saved vendor churn + more leads available)
- Built business case for larger strategic search platform overhaul (S003)

**KEY DECISION**: Sync/async dual path over all-sync (GPU-prohibitive). Applied real-time only to high-value calls (urgency x order value matrix), batch for rest.

**EARNED SECRET**: "78% of 'spam' was real demand going to the wrong place. Sometimes the fastest path to vendor trust isn't preventing the failure — it's recovering from it intelligently."

**TECHNICAL DEPTH**: GPU-accelerated transcription, in-house LLM for intent extraction, keyword spotting engine (chunking — 75% GPU reduction), sync/async dual processing paths. 25K sync + 55K async. Pre-computed urgency routing matrix (Plumber = Urgent, Wedding Planner = Non-Urgent). Auto-rerouting with net-new lead creation.

---

### S021 — Login Pop-up Debugging: Marketing Campaign Conflict
**LPs**: Dive Deep, Customer Obsession, Are Right A Lot, Ownership | **Company**: Justdial

**HOOK**: "I tracked a 7pp login success drop to a conflict between legacy JavaScript on marketing landing pages and new auth cookies — visible only when sliced by traffic source AND browser."

**SITUATION**: Justdial released a new login pop-up replacing an older full-page redirect flow. Login success rate dropped from 92% to 85% — 7pp decline. The drop wasn't showing in the pop-up's own metrics.

**TASK**: Diagnose why login success had dropped 7pp despite the new pop-up performing well in isolation.

**ACTION**:
1. I checked all flows and funnels — no pattern. Until I looked at Kibana logs and spotted a cluster of failures coming from Google Search App in user-agent strings.
2. I worked backwards from the user agent. Tested on Google Search App specifically and saw critical code failure. The conflict was in the Google Search App's WebView — stricter cookie/session handling.
3. I traced root cause: legacy JavaScript on marketing landing pages had outdated dependencies that conflicted with new session cookies, specifically running afoul of stricter SameSite cookie policies in Google Search App's WebView.
4. I collaborated with analytics team to build the segmented funnel view confirming the source-specific drop.

**RESULT**:
- Login success: 92% → 85% → recovered to 92%, later improved to 93%
- Google Search App was top 3 traffic source — fix prevented ongoing conversion loss
- Established new QA protocol: all marketing landing pages tested against new auth flows before release
- 2-day fix vs. 2-week refactor

**KEY DECISION**: Fix marketing landing pages (targeted, 2-day implementation) over making pop-up backwards-compatible (safer but 2-week refactor).

**EARNED SECRET**: "The most dangerous bugs are the ones that look fine in aggregate. This drop was invisible in the pop-up's own metrics — it only appeared when you sliced by traffic source AND browser."

**TECHNICAL DEPTH**: Analytics segmentation (SQL), browser user-agent analysis, JavaScript debugging on marketing landing pages, Google Search App WebView testing. Root cause: legacy JS with outdated dependencies → conflicts with new session cookies → SameSite cookie policy failure in WebView → silent login failure. New QA checklist added.

---

### S022 — Merchant Metrics Redesign: Preventing a Bad Launch with A/B Test
**LPs**: Are Right A Lot, Dive Deep, Bias for Action, Customer Obsession | **Company**: Justdial

**HOOK**: "I prevented a dashboard rollout that would have degraded lead responses for ~70% of vendors by pushing for an A/B test — only 15% benefited while the majority saw responses drop from 4.1 to 3.8/day."

**SITUATION**: Justdial's merchant engagement team proposed showing vendors business performance metrics and gamifying via leaderboards above the leads section. Time to first response sat at 28 seconds. Clear correlation between category-level conversion and response speed.

**TASK**: Evaluate the proposal before full rollout. My agency was limited, so I needed to fight with data.

**ACTION**:
1. I analyzed the vendor base. Found that ~70% of vendors had little local competition, sparse lead history, and no meaningful data to display in charts.
2. I identified that synchronous API calls for leaderboard data degraded the core experience. On 4G networks (majority of merchant app users), this slowed the page where vendors respond to leads.
3. I pushed for A/B test on 10% mix. Results: only ~15% slightly improving. The remaining didn't find enough relevant data. Lead responses dropped from 4.1/day to 3.8/day for the majority.
4. I used data to kill the feature for the 70% it was harming. Changed the logic: show metrics only to vendors with sufficient data density. For critical categories (home services, emergency repairs), rolled back entirely.

**RESULT**:
- Prevented full rollout that would have degraded responses for ~70% of vendors (4.1→3.8/day)
- Improved engagement for ~15% high-volume cohort
- Protected 28-second time-to-first-response in critical categories
- Established A/B testing as requirement for merchant app redesigns

**KEY DECISION**: A/B test over ship-and-iterate. Shipping would have degraded experience for 70% of vendors including paid vendors whose response times directly impact revenue.

**EARNED SECRET**: "Features designed for power users can destroy the experience for everyone else. For 70% of our vendors in Tier 2/3 cities, there was no meaningful competition to gamify — just empty charts and slower page loads."

**TECHNICAL DEPTH**: A/B testing framework, merchant data density calculator. I defined the logic: evaluate PIN code, expand radius until 5 competitors, calculate median distance and lead density. If threshold not met, dashboard didn't render. Category-level override for response-critical categories. Performance monitoring for page load times per variant.

---

### S023 — Day Pass for Vendors: Performance Debugging on 4G
**LPs**: Bias for Action, Dive Deep, Frugality, Invent and Simplify, Customer Obsession | **Company**: Justdial

**HOOK**: "I discovered that a synchronous pricing API that was 200ms on Wi-Fi ballooned to 3 seconds on 4G — cascading to block every element below it on the page, including the lead response section."

**SITUATION**: ~85% of Justdial's free vendors had never seen the paid dashboard. I wanted to give them a "Day Pass" — free 24-hour trial of paid features. Engineering constraint: no dedicated sprint allocation.

**TASK**: Design and ship Day Pass to convert free vendors to paid. Goal: increase free-to-paid conversion from ~2% to ~5%.

**ACTION**:
1. Engineering built a quick pricing calculation — real-time API calls for each vendor's category x city combination. Since full pricing infrastructure didn't exist for Day Pass SKUs, it calculated on-the-fly.
2. After launch, I saw clicks on critical CTAs drop — concentrated on 4G networks.
3. I diagnosed: pricing API calls were synchronous — blocked page rendering. 200ms on Wi-Fi, 1.5-3 seconds on 4G. Because page elements loaded synchronously, the Day Pass banner delayed ALL subsequent elements. The delayed banner caused severe CLS, pushing lead content down.
4. I traced the impact chain: slow Day Pass API → synchronous rendering blocked lead section → lead API calls timed out → CTA clicks dropped.

**RESULT**:
- Identified and fixed: moved Day Pass pricing to async/lazy loading
- I decoupled the critical path: if dynamic pricing API timed out, fell back to a SQL table serving 1-day stale pricing data
- CTA click rates recovered
- ~3.5% conversion after fix
- Established new protocol: all features tested on simulated 4G before launch

**KEY DECISION**: Hacky pricing (ship fast) + async rendering fix (2 days) over rebuilding pricing infrastructure (4 weeks). Pragmatic at each step.

**EARNED SECRET**: "Never trust internal testing on Wi-Fi. A 200ms API call becomes 3 seconds on 4G — and if it's synchronous, it cascades to everything below it."

**TECHNICAL DEPTH**: Dynamic pricing API (category x city), synchronous→async page rendering refactor, network performance monitoring, 4G network simulation. Fallback to SQL table with 1-day stale pricing on timeout. CLS caused by synchronous banner delayed all subsequent elements.

---

### S024 — OTP Failure: Notification Gateway Build
**LPs**: Dive Deep, Ownership, Highest Standards, Customer Obsession | **Company**: Justdial

**HOOK**: "I traced a spike in OTP failures to a marketing message queued as 'critical' — consuming the critical queue's rate limit and dropping real OTPs across all verticals. Then I built a centralized notification gateway that has had zero OTP outages since deployment."

**SITUATION**: When Justdial launched new verticals, each team got the legacy notification system's SDK. I saw a sudden spike in "No OTP received" complaints from service vendors, causing unfair "late show" penalties. Ops team wrote it off as cellular network issues. I wasn't convinced — network degradation doesn't cause sudden, localized spikes.

**TASK**: Identify true root cause of OTP delivery delays and implement a systemic architectural fix.

**ACTION**:
1. I contradicted the initial diagnosis. The spike didn't correlate with new user growth rates across any of the new verticals.
2. I partnered with a Senior Technical Architect to inspect the notification queue. Discovered one team had misconfigured: a daily marketing promotion was queued with "critical" priority instead of "marketing."
3. I traced the cascade: marketing messages consuming the critical queue's rate limit → OTPs dropped → retries added more pressure.
4. I fixed the misconfiguration immediately. Then led a small team to build a centralized Notification Gateway — deprecated direct SDKs. Three core requirements: (a) Strict Authentication — auth token per team, every payload traceable. (b) Priority Queues & Rate Limiting — Critical (OTPs), Transactional, Marketing with strict independent rate limits. (c) Payload Validation — strict JSON schema validation script as pre-flight check, rejecting malformed payloads before they consumed processing power.

**RESULT**:
- 15% improvement in "late show" metrics
- 15% reduction in Ops daily workload
- 3 similar misconfigurations caught in following quarter
- Zero OTP-related outages since gateway deployment
- ~500K+ daily notifications governed

**KEY DECISION**: Centralized gateway (adds ~10ms latency) over distributed per-team rate limiting. Governance guarantee worth the latency. Deployed across multiple Availability Zones with in-memory buffer.

**EARNED SECRET**: "Giving teams access to shared infrastructure without governance is a ticking time bomb. The teams weren't being malicious — they just didn't understand that 'critical' had rate-limiting implications."

**TECHNICAL DEPTH**: Java gateway service, message queue inspection, rate limiter per sender/priority, JSON schema validation rules engine, monitoring/alerting for queue health. Priority Queue Separation: Critical/Transactional/Marketing with strict independent limits. Marketing auto-downgraded if incorrectly classified. Audit log with sender, priority, classification, delivery status. Multiple AZ deployment with in-memory buffer for 99.99% uptime.

---

### S025 — ML-Powered Lead Ranking with XGBoost
**LPs**: Invent and Simplify, Learn and Be Curious, Are Right A Lot, Hire and Develop the Best | **Company**: Justdial

**HOOK**: "I used XGBoost as a diagnostic tool — not a production model — to discover that compound signals predicted lead quality where 5 isolated experiments had failed. Then I mentored a junior PM through the entire analytical framework."

**SITUATION**: Justdial's lead ordering showed all leads chronologically. Across ~50 lakh enquiries/day, this was suboptimal. Multiple teams had tried individual signals (distance, order value, quantity) — all isolated experiments failed. Lead response rates stagnant at ~35%.

**TASK**: Find a better lead ranking approach after multiple failed attempts. I also wanted to develop a junior PM's analytical skills.

**ACTION**:
1. I paired with a junior PM, coached them through the entire analytical framework — problem definition to feature engineering to experimentation design. They did hands-on work; I guided the approach.
2. I used XGBoost as a diagnostic tool. Ingested all available lead data (~15 features) into XGBoost as a "black box." Goal wasn't deployment — it was understanding which combinations predicted lead quality.
3. I worked backwards from the model. Key discovery: users who viewed more pictures on a vendor's profile were 2.3x more likely to convert. Distance alone didn't predict quality — but distance x order value x content engagement did.
4. I translated insights into a weighted scoring formula (not the model itself). I bucketed non-linear features into step-weights (e.g., distance: 0-2km = 10 pts, 2-5km = 5 pts). Formula weights deployed as config variables in Java service. Quarterly manual review based on offline model retraining.

**RESULT**:
- Lead response rate: ~35% → ~42% at peak
- Vendor satisfaction improved
- Junior PM grew significantly — later led own experimentation initiatives
- Formula captured 90% of ML model improvement

**KEY DECISION**: Weighted formula over ML model deployment. ML model was ~8% better but required serving infrastructure I didn't have. Formula was 90% of improvement, deployable in 2 days.

**EARNED SECRET**: "Every previous experiment tested one factor at a time. They all failed because lead quality is a compound signal. The picture-viewing insight was a bonus — nobody had thought to include content engagement."

**TECHNICAL DEPTH**: Python (XGBoost, pandas, scikit-learn), SQL for data extraction, scoring formula in Java ranking service, A/B testing. ~15 features per lead: distance, order value, quantity, locality match, content engagement (pictures viewed, time on page, reviews read), time-of-day, category, search history depth. Step-weight bucketing to approximate non-linear XGBoost results. ~50L enquiries/day ranked.

---

### S026 — Category Banner Conversion Drop: Silent Targeting Bug
**LPs**: Dive Deep, Customer Obsession, Highest Standards, Ownership | **Company**: Justdial

**HOOK**: "I traced a slow conversion decline to a silent schema mismatch between Core Billing and Marketing Targeting — vendors were being permanently removed from the targeting pool with no errors and no alerts."

**SITUATION**: I launched self-serve category-level marketing for vendors. Campaign conversion jumped from 0.007% to 0.018%. But over 2-3 months, conversion eroded back toward baseline. ₹15-20L in projected monthly revenue leaking — completely silent, no crashes or error spikes.

**TASK**: Find root cause of this erosion and implement permanent fix.

**ACTION**:
1. I broke down the funnel. Banner CTRs stable — ruled out content fatigue. Cohort analysis showed drop concentrated among repeat vendors hitting lifecycle renewal marks.
2. I traced the vendor state lifecycle between Core Billing monolith (publisher) and Marketing Targeting service (consumer). Found targeting pool volume was shrinking.
3. I found the gap: Core Billing published "expired" events with older, inconsistent schema. Marketing Targeting service couldn't parse the legacy payload, defaulted to safely dropping the vendor from active targeting pool entirely. Silent failure at the consumer level.
4. The compounding effect: every day, a small percentage of vendors permanently removed. Pool shrank cumulatively — only getting worse.
5. I drove structural fixes: (a) Consumer-Side: Dead Letter Queue for unparseable payloads + alerting. Ran replay script to re-ingest dropped vendors after schema fix. (b) Publisher-Side: asynchronous schema validation interceptor — billing transaction succeeds normally but invalid events flagged and quarantined before hitting event bus.

**RESULT**:
- Recovered full 0.018% conversion rate within 2 weeks
- Stopped ₹15-20L monthly revenue bleed
- Publisher-side validation protects all downstream services (not just marketing)
- Established monitoring alert for targeting pool size changes

**KEY DECISION**: Fixed both publisher (schema validation) AND consumer (alerting on unparseable payloads) — belt and suspenders. Publisher fix also protects all downstream services.

**EARNED SECRET**: "The scariest bugs work fine at first and degrade slowly. This was a silent failure — no errors, no alerts, just a targeting pool that shrank a little more every day."

**TECHNICAL DEPTH**: SQL cohort analysis (vendor age x conversion x targeting status), event payload log analysis, schema validation layer. Core Billing monolith → Marketing Targeting service: event-driven architecture with schema mismatch at consumer level. Dead Letter Queue (DLQ) with replay capability. Async schema validation interceptor at publisher side — quarantines invalid events before event bus. Daily targeting pool size monitoring with threshold alerts.

---

## Standing Narratives

### Tell Me About Yourself (2 minutes)
"I'm Piyush — I've spent the last 6+ years building marketplace products in India, most recently as GPM at Justdial where I led a team of 6 PMs and 15+ cross-functional members.

Three things define my work: First, I've built from zero. I took JD Xperts — a home services vertical — from concept to ₹4.8cr ARR with 5.4x unit economics. I was the first hire, built the team, proved the business model. Second, I've shipped AI at production scale. Our LLM-powered search engine cut search failures from 11% to ~2%, generating 90K high-intent leads daily from previously dead traffic — handling Hinglish, misspellings, and free-text queries that rules-based systems couldn't touch. Third, I understand the emerging market merchant. I discovered that nearly half our app users were actually businesses, built self-serve monetization for them, and unlocked ₹13cr in revenue from categories that were structurally unprofitable under a sales-led model.

That last insight — that in emerging markets, you need product-led self-serve because you can't scale a sales team to match the long tail — is exactly what EMXO is building. I've lived the friction this role is designed to solve: mobile-only users, trust-driven purchase decisions, multilingual search, and vendors who need simple self-serve tools to grow."

### Why I Left Justdial (30-45 seconds)
"I'd been at Justdial for nearly 5 years — built JD Xperts from zero, then led the mobile product org. By late 2025 I'd accomplished what I came to do: proved the new business model, scaled the LLM search engine, built the PM org. Two things converged: a leadership transition was underway, and the role I wanted next — something more technically forward, closer to the AI and platform frontier — wasn't going to be created there. I decided this was the right moment to deliberately invest in being closer to where technology is moving. That's what has me here talking to Amazon."

### Why Amazon / Why This Role (60-90 seconds)
"The EMXO charter maps almost exactly to the problems I've been working on — mobile-first users, emerging market dynamics, self-serve vendor growth, long-tail monetization. At Justdial, I discovered that nearly half our app users were actually businesses. When we built self-serve monetization flows for them — removing the sales team as the intermediary — we unlocked ₹13cr in revenue in categories that were structurally unprofitable under a sales-led model. The insight was the same one Amazon is building on: in emerging markets, you can't scale a sales team to match the long tail. You need product-led self-serve. The EMXO mission is to make Amazon work for merchants and customers across 10 markets where the friction looks very different than North America. I've lived that friction — building products where Hinglish queries break your search engine, where trust signals matter more than price, where mobile is the only screen. That's not context I'd need to learn here. I'd be walking in with it."
