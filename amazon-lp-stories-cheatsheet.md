# Amazon LP Stories Cheatsheet — Piyush Deveshwar
**Amazon Sr. PM - Mobile Growth, EMXO PLX | Screening: 2026-03-20**

---

## Quick Reference: LP → Story Map

| Leadership Principle | Best Story | Backup Story | Third Option |
|---|---|---|---|
| Customer Obsession | S003 (LLM Search — rescuing 65K failed searches/day) | S006 (Cancellations 20%→3%, NPS turnaround) | S017 (Category exploration, leads +59%) |
| Ownership | S001 (JD Xperts 0-to-1, ₹4.8cr ARR) | S009 (Self-serve vendor platform, ₹13cr unlock) | S019 (Failure: owned post-mortem) |
| Invent and Simplify | S004 (Shared OMS — 3 months→3 weeks) | S012 (Anti-corruption layer, 48% order growth) | S013 (CRM-lite from scratch) |
| Are Right, A Lot | S005 (Invented "Lost Potential Bookings" KPI) | S007 (LTV data → delayed launch, saved category) | S018 (Segmentation → PMF) |
| Learn and Be Curious | S003 (LLM search — self-taught LangChain, fine-tuning) | S015 (Free blog → 100K users, self-taught infra) | S019 (Failure → changed research approach) |
| Hire and Develop the Best | S014 (Built PM org from scratch, 6 PMs) | S001 (First hire, built full team) | — |
| Insist on the Highest Standards | S007 (LTV analysis → delayed launch for quality) | S006 (Cancellations 20%→3%, NPS -12→+28) | S013 (Built CRM when none existed) |
| Think Big | S010 (Deals MVP → ₹120M projected vertical) | S001 (Diversification from adtech to services) | S004 (Platform for all future verticals) |
| Bias for Action | S008 (AC Repairs: 6x growth, ₹1cr revenue) | S012 (Headless booking engine, weeks not quarters) | S010 (Frugal MVP, live in weeks) |
| Frugality | S010 (CSV-upload CMS → 18K users/day) | S015 (₹2500→₹800/mo, 100x traffic) | S013 (CRM-lite vs. Zendesk) |
| Earn Trust | S007 (LTV data → convinced Business Head on pricing) | S019 (Owned failure, transparent post-mortem) | S016 (3x professional income) |
| Dive Deep | S003 (Root-caused 4 failure buckets, built LLM pipeline) | S005 (Hourly data exposed hidden demand gaps) | S018 (50 interviews → 4 segments) |
| Have Backbone; Disagree and Commit | S007 (Challenged Business Head pricing with LTV data) | S017 (Pushed back on template approach) | S011 (Vertical marketplace against horizontal) |
| Deliver Results | S001 (₹4.8cr ARR, 5.4x unit economics) | S009 (₹13cr revenue unlock) | S008 (₹1cr single category, 190K users) |
| Strive to be Earth's Best Employer | S014 (Built PM org, culture, career paths) | S016 (3x professional income) | — |
| Success and Scale Bring Broad Responsibility | S004 (Shared OMS enabled 4 business lines) | S012 (Unlocked call center channel for all) | S013 (Scaled support without scaling team) |

---

## Standing Narratives

### Tell Me About Yourself (2 minutes)
"I'm Piyush — I've spent the last 6+ years building marketplace products in India, most recently as GPM at Justdial where I led a team of 6 PMs and 15+ cross-functional members.

Three things define my work: First, I've built from zero. I took JD Xperts — a home services vertical — from concept to ₹4.8cr ARR with 5.4x unit economics. I was the first hire, built the team, proved the business model. Second, I've shipped AI at production scale. Our LLM-powered search engine cut search failures from 11% to 2%, rescuing 65,000 searches daily — handling Hinglish, misspellings, and free-text queries that rules-based systems couldn't touch. Third, I understand the emerging market merchant. I discovered that nearly half our app users were actually businesses, built self-serve monetization for them, and unlocked ₹13cr in revenue from categories that were structurally unprofitable under a sales-led model.

That last insight — that in emerging markets, you need product-led self-serve because you can't scale a sales team to match the long tail — is exactly what EMXO is building. I've lived the friction this role is designed to solve: mobile-only users, trust-driven purchase decisions, multilingual search, and vendors who need simple self-serve tools to grow."

### Why I Left Justdial (30–45 seconds)
"I'd been at Justdial for nearly 5 years — built JD Xperts from zero, then led the mobile product org. By late 2025 I'd accomplished what I came to do: proved the new business model, scaled the LLM search engine, built the PM org. Two things converged: a leadership transition was underway, and the role I wanted next — something more technically forward, closer to the AI and platform frontier — wasn't going to be created there. I decided this was the right moment to deliberately invest in being closer to where technology is moving. That's what has me here talking to Amazon."

### Why Amazon / Why This Role (60–90 seconds)
"The EMXO charter maps almost exactly to the problems I've been working on — mobile-first users, emerging market dynamics, self-serve vendor growth, long-tail monetization. At Justdial, I discovered that nearly half our app users were actually businesses. When we built self-serve monetization flows for them — removing the sales team as the intermediary — we unlocked ₹13cr in revenue in categories that were structurally unprofitable under a sales-led model. The insight was the same one Amazon is building on: in emerging markets, you can't scale a sales team to match the long tail. You need product-led self-serve. The EMXO mission is to make Amazon work for merchants and customers across 10 markets where the friction looks very different than North America. I've lived that friction — building products where Hinglish queries break your search engine, where trust signals matter more than price, where mobile is the only screen. That's not context I'd need to learn here. I'd be walking in with it."

---

## Full Stories (STAR Format)

### ★ S001 — Zero-to-One P&L: JD Xperts to ₹4.8cr ARR
**LPs**: Ownership, Deliver Results, Think Big
**Best for**: "Tell me about a time you built something from scratch" / "Tell me about your biggest business impact"

**Situation**: 2020 — Justdial's ad revenue drops. Leadership wants revenue diversification beyond ad tech. Users are already searching for home services. High-quality vendors want a better marketing channel than banner ads.

**Task**: First hire for the initiative. Negotiated from business lead to product + business lead. Hired engineers, PMs, operators — built the full org. Reported to CPO. No separate budget — had to prove the model first within the existing org.

**Action**:
1. **Model shift: handshake → completion.** Legacy model: Justdial connects vendor to user, earns ~₹50 per connection event. New model: commission on completed bookings. Average ticket ₹1,100–1,200, blended revenue ₹270/order. **5.4x the legacy model.** Vendors preferred it — more assured returns than ad spend.
2. **Matchmaking algorithm.** Commission-on-completion only works if matches are good. Built algorithm that cut cancellations from 20% → 3%, flipped NPS from -12 → +28. This was the quality foundation the business model required.
3. **Shared OMS.** Foresaw each new category would need ~3 months standalone build. Built abstracted shared infrastructure — new verticals launch in 3 weeks. Enabled 4 new business lines.

**Result**: ₹4.8cr ARR (~$580K) over ~2.5 years. 5.4x unit economics. Proved the model to exec team. OMS enabled 4 verticals at dramatically reduced launch time.

**Earned Secret**: "When you flip to commission-on-completion, every bad match, every cancellation, every poor NPS score becomes your problem economically. That alignment is what makes the product better. We didn't just build a new revenue line — we built a fundamentally different relationship between platform quality and platform revenue."

---

### ★ S003 — Solving 11% Search Failure with LLM Engine
**LPs**: Customer Obsession, Invent and Simplify, Dive Deep, Learn and Be Curious
**Best for**: "Walk me through a technical architecture decision" / "Tell me about a time you used technology to solve a customer problem"

**Situation**: Justdial processed millions of searches daily, but 11% were failing — no results or irrelevant results followed by repeat search. ~80,000 dead searches daily from high-intent users. Failures clustered into 4 buckets: misspellings, colloquial/local language spellings, free-text natural language queries, and Hindi/Hinglish code-switched text.

**Task**: Fix search failure rate. Owned end-to-end solution, led cross-functional team of 8 across product, engineering, and data.

**Action**:
1. **Evaluated 3 options**: (a) Expand rules-based dictionary — rejected, can't enumerate Hinglish variants. (b) Google Vertex API — strong quality but per-query cost at 80K+ daily failures was unworkable. (c) Fine-tune in-house model — higher upfront, full cost and quality control.
2. **Chose option 3, staged it.** Repurposed existing internal LLM entity extraction service (built for phone call transcripts) as an independent search service rather than building from scratch.
3. **Architecture**: Async message queue with worker node pool. Failing queries processed asynchronously, corrections delivered via SMS/WhatsApp. "Did you mean ___?" served double duty — helped user immediately AND response became ranked feedback signal for Elasticsearch layer. LangChain semantic matching pipeline parsed intent from raw queries.
4. **Unit economics evolution**: External LLM APIs first (fast, expensive) → cheaper hosted model → fully in-house fine-tuned model. Moving in-house fixed Hinglish quality — general models handled code-switching poorly.
5. **Rollout**: Batch-tested on previous week's failed queries, manually QA'd outputs, then staged rollout — small app traffic percentage, then two cities.

**Result**: Search failure 11% → ~2%. Rescued ~65,000 searches daily. ~90,000 high-intent leads daily from previously dead traffic. ~50,000 unique users captured.

**Earned Secret**: "Most teams treat their LLM cost problem as procurement — negotiate better API rates. We treated the model as a product we owned. Moving in-house gave us cost control and quality control simultaneously — general models handled Hinglish badly because they'd never been trained on India's local search code-switching patterns. You can't buy your way to that. You have to build it."

---

### ★ S009 — Self-Serve Vendor Platform: ₹13cr Revenue Unlock
**LPs**: Ownership, Deliver Results, Customer Obsession, Dive Deep
**Best for**: "Tell me about a time you found a hidden opportunity" / Amazon EMXO domain match story

**Situation**: Justdial's apps had lower engagement than web. Org optimized for "users" as one undifferentiated segment. All vendor advertising sold through offline/direct sales. Product-driven advertising was 0.5% of total (~₹1.5cr on ~₹65cr app ad base).

**Task**: Improve mobile monetization and unlock new revenue from the vendor segment.

**Action**:
1. **Deep dive into data**: Reviewing engagement metrics, noticed app and web diverged unexpectedly. Went deeper — cohort analysis, behavioral segmentation, booking patterns. Found 45-50% of app users were actually businesses — vendors tracking leads, responding to customers, managing presence. Known anecdotally in org, never treated as product opportunity.
2. **Reframed the problem**: Not "why is app engagement lower?" but "why are we serving two completely different user types with one product?"
3. **Built self-serve capabilities**: Contextual prompts on search results ("You can buy this position"), direct purchase of banners/trust badges/verified badges/sponsored positions — no sales call required.
4. **Structural insight — long tail**: Sales-team cost-of-sale exceeded revenue per long-tail category, so sales skipped them. Digital self-serve removed cost-of-sale barrier entirely. Actively drove traffic to long-tail categories, created advertising inventory that now had buyers.

**Result**: App advertising revenue from ~₹65cr to ~₹78cr — ₹13cr incremental unlock. Primary driver: long-tail categories previously unprofitable under sales-led model.

**Earned Secret**: "The insight wasn't new — old hands knew half the app users were businesses. What was new was treating it as a product problem rather than a sales problem. When you remove the sales team as intermediary, cost-of-sale collapses and the long tail becomes economically viable for the first time. That's not a growth hack — that's a structural shift. Amazon EMXO is building exactly this."

---

### S002 — 5.4x Unit Economics Transformation ⚠️ SEED
**LPs**: Deliver Results, Dive Deep, Are Right A Lot
**Best for**: "Walk me through a financial decision" / unit economics deep dive

- **Situation**: JD Xperts needed sustainable economics to justify continued investment
- **Task**: Transform unit economics from uncertain to healthy
- **Action**: Shifted from ₹50/connection (legacy ad model) to ₹270/order (commission on ₹1,100–1,200 avg ticket). Key levers: pricing model change, matchmaking quality (lower cancellations = higher completion rate), vendor retention
- **Result**: 5.4x unit economics. Business became self-sustaining
- *Note: This story overlaps heavily with S001. Use S001 as primary; deploy S002 framing only if interviewer probes specifically on unit economics mechanics*

---

### ★ S004 — Foreseeing the Bottleneck: Shared OMS Architecture
**LPs**: Invent and Simplify, Think Big, Are Right A Lot, Have Backbone; Disagree and Commit
**Best for**: "Tell me about a time you simplified a complex problem" / technical depth / platform thinking / "Tell me about a time you disagreed with stakeholders"

**Situation**: JD Xperts was built as a monolith — order placement, fulfillment, ratings, user management, all in one system. Meanwhile, Justdial was spinning up parallel product pods (doctors, insurance, laundry) as full-stack verticals. Each team was independently building practically the same infrastructure in silos — 4 teams duplicating order management, notifications, vendor management.

**Task**: I noticed the problem while helping hire for other teams and sharing architectural decisions. My EM's bandwidth was getting stretched helping all teams with know-hows. I recognized that every future vertical would rebuild the same components — and advocated for shared microservices instead.

**Action**:
1. **Identified the shared core.** Mapped what was category-specific vs. reusable: user management, notification/comms layers, and vendor management (including availability) were nearly identical across verticals. Content management needed scope expansion. Matchmaking was configurable.
2. **Built the case to the CPO.** Other team leads pushed back — they didn't want dependency on another team's infrastructure. I got the CPO on my side by showing how this would save months of duplicated effort per vertical and standardize processes for all future development.
3. **Decomposed the monolith into microservices.** Each service exposed APIs — new verticals simply made calls. Example: availability was managed by a vendor management service; any new vertical could call it to find available vendors instead of rebuilding availability logic from scratch.

**Result**: New vertical launch time dropped from ~3 months to ~3 weeks (65% reduction). Enabled 4 new business lines (including JD Loans — the #1 priority). Uptime improved from 99.9% to 99.99%. Bug rate for new category launches dropped by 35%. Freed engineering bandwidth across the org. Standardized internal processes.

**Earned Secret**: "The hardest part wasn't the architecture — it was the org politics. Team leads didn't want to depend on shared services they didn't control. The technical decision was obvious; the organizational decision required earning trust that shared infrastructure wouldn't become a bottleneck. I had to prove reliability before teams would voluntarily adopt."

---

### ★ S005 — Inventing "Lost Potential Bookings" KPI
**LPs**: Are Right A Lot, Dive Deep, Have Backbone; Disagree and Commit
**Best for**: "Tell me about a time you used data to change a decision" / "Tell me about a time you invented a new metric" / strategic thinking

**Situation**: JD Xperts conversion funnels looked steady at daily/weekly averages — nothing alarming on dashboards. But customer calls told a different story: users couldn't find slots, availability was patchy. I personally experienced unavailable slots too. The dashboards weren't alerting anyone because daily averages were masking localized capacity gaps — specific hours, specific areas were demand-starved but invisible in aggregated data.

**Task**: Business/sales teams used these dashboards to plan vendor onboarding at city and category level. Two gaps: (A) no real-time visibility into when/where demand exceeded supply, and (B) no way to calculate how many vendors were actually needed on the ground.

**Action**:
1. **Looked at data at hourly granularity.** Confirmed hypothesis — daily/weekly averages were hiding localized spikes where demand far exceeded supply. The "steady" conversion rate was an artifact of averaging.
2. **Created "Lost Potential Bookings" metric.** LPB = Visitors on slot page × (benchmark max conversion − actual conversion). Designed it to be simple enough for sales teams to act on — a single number telling them exactly how many vendors to onboard in each area.
3. **Evolved the benchmarking.** Started simple, then incorporated events, time-of-day patterns, and rolling averages to make benchmarks more precise over time.

**Result**: Revealed that areas with "poor average conversion" were actually demand-hungry hubs — traffic had increased but supply hadn't kept up. Hub-wise demand growth increased from 9.6% to 12%. Slot page conversion rate improved from ~12% to ~14%. Org shifted from reactive to proactively supply-driven expansion.

**Earned Secret**: "Averages are the most dangerous metric in a marketplace. They make you feel fine while you're starving specific zones of supply. The fix wasn't better analytics — it was creating a metric simple enough that a sales team member in the field could act on it without a data analyst."

---

### ★ S006 — Cancellations 20% → 3%, NPS -12 → +28
**LPs**: Customer Obsession, Insist on the Highest Standards, Dive Deep
**Best for**: "Tell me about a time you improved quality" / "Tell me about a time you dove deep into data" / marketplace dynamics

**Situation**: A few months into JD Xperts, daily cancellations stood at 30–35% overall, with vendor-side cancellations at 20%. With 95% new customers, every cancellation meant 100% churn — permanent loss. 45% of ops bandwidth was consumed managing this issue.

**Task**: Find and fix the root cause of cancellations to make the commission-on-completion model viable.

**Action**:
1. **Spoke to customers first.** Users reported that vendors accepted orders but denied service after reaching the location. Initially attributed to vendor quality, but cancellation rates didn't correlate with vendor ratings — good-rated vendors were cancelling too.
2. **Dug deeper into data.** Discovered a skill mismatch problem: appliance repair is specialized — AC ≠ washing machine ≠ refrigerator. The matchmaking system treated all vendors as interchangeable within "appliance repair." A vendor skilled in ACs was being sent to fix a washing machine, arriving on-site, realizing they couldn't do it, and cancelling.
3. **Built skill-tag matching system.** Took inputs from vendors on specific skills, tested them via questionnaire and phone calls for edge cases, added granular skill tags to each profile. Rule-based matching — tag + rating against past appliance-specific cases. Technical implementation took just 15 days (2 sprint cycles).

**Result**: Vendor cancellations dropped from 20% to 3%. NPS flipped from -12 to +28. Blended new-user churn dropped from 76% to 66%. Ops intervention rate on cancellations dropped from 45% to 25%. Vendor utility improved from 1.2 to 1.7 jobs/day as they received better-matched leads. Built the quality foundation that made commission-on-completion economics work.

**Earned Secret**: "The data initially misled us — we assumed cancellation = bad vendor. But ratings measured attitude and service quality, not technical capability for that specific appliance. The fix wasn't a better algorithm — it was asking the right question: not 'who is good?' but 'who is good at THIS?'"

---

### ★ S007 — LTV Analysis → Delaying Launch to Protect Customer Trust
**LPs**: Earn Trust, Have Backbone; Disagree and Commit, Are Right A Lot, Insist on Highest Standards
**Best for**: "Tell me about a time you influenced without authority" / "Tell me about a time you pushed back on leadership" / data-driven persuasion

**Situation**: Urban Company, ~2019–2020. Business Head and Marketing Head wanted to launch RO (water purifier) service & repair vertical fast, with a flat ₹249 entry price to drive volume. My demand analysis showed "service" queries outweighed "repair" queries 6:1. Service ticket was ~₹2,100 vs. ₹249 for repair — nearly 9x gap. Meanwhile, historical data showed price-gouging was the second-largest complaint category at 28%. We were about to launch a category where the dominant transaction had the highest price-gouging risk.

**Task**: Validate category economics before go-live. As I dug in, I found a problem leadership hadn't seen — and had to decide whether to raise it, knowing it would delay a launch they'd already committed to with an aggressive 15-day timeline.

**Action**:
1. **Demand composition was inverted.** Service demand was 6x repair. Business had planned as if these were comparable — they weren't.
2. **Ran LTV by complaint type.** Great experience: LTV ≈ ₹450. Complaint resolved via revisit: LTV ≈ ₹190. Price-gauging complaint: LTV ≈ **−₹200** (NPS −20, 100% churn). Every price-gouged customer would cost the business ₹200 — a ₹650 swing per customer vs. a happy one.
3. **Shifted the conversation.** Presented full analysis to Business Head and Marketing Head. Reframed from "speed vs. quality" to "unprofitable growth vs. profitable growth." Recommended delaying launch to standardize pricing across cities, publish transparent price schedules, build vendor accountability.
4. **Executed the fix.** Worked with ops and city teams to agree on pricing grids, aligned business and marketing on fixed-price SKU model.

**Result**: Launch delayed 3 weeks. RO category launched with 4.8 rating (highest on platform). Price-gouging complaints reduced from 28% benchmark to just 4%. Overall complaint rate 3.75% vs. 5% platform benchmark. Became one of the most successful and trusted categories.

**Earned Secret**: "Leadership was optimizing for acquisition. I was optimizing for lifetime value. When you show that a price-gauging customer is worth −₹200 while a happy customer is worth ₹450 — a ₹650 swing per customer — the argument stops being a PM pushing back on a Business Head. It becomes arithmetic."

---

### ★ S008 — Scaling AC Repairs: 6x Growth, ₹1cr Revenue, 190K New Users
**LPs**: Bias for Action, Deliver Results, Ownership, Are Right A Lot
**Best for**: "Tell me about a time you identified and seized an opportunity" / "Tell me about a time you delivered outsized results" / operator story

**Situation**: Urban Company, AC repairs was an existing but underinvested category. Leadership mandated focus on high-growth-potential categories. While analyzing demand trends, I noticed a significant year-over-year jump in AC repair/service demand — seasonal but massive.

**Task**: As the P&L owner, I had to identify the right categories for investment, then plan and execute the growth strategy. I chose AC repairs based on the demand data and created the full operational plan.

**Action**:
1. **Built a city-wise demand estimation framework.** Estimated demand by city to plan capacity precisely — not just "more vendors" but exactly how many, where, and when.
2. **Built supply resilience.** Planned backup vendor capacity for demand peaks. Created a new model to lock in high-quality vendors with more stable, regular business for longer periods — giving them assured income in exchange for priority availability.
3. **Demand shaping via marketing.** Created campaigns offering discounts to early bookers, spreading demand across the season instead of letting it spike. This let us absorb more demand than ever before without quality drops.

**Result**: 6x growth in orders served. ₹1cr revenue from a single category — record-breaking. 190K new users added to the platform (highest till date). CAC was 1/3rd the overall business CAC, making it the most efficient acquisition channel. Positive NPS of ~12 maintained throughout.

**Earned Secret**: "Seasonal categories look risky because demand is peaky. But if you can shape demand with early-bird incentives and build supply resilience with vendor lock-in models, the peaks become your advantage — you acquire customers at 1/3rd normal CAC because the intent is so high. The trick isn't avoiding seasonality; it's engineering for it."

---

### ★ S010 — Frugal MVP: Deals & Offers → 18K Daily Users, ₹120M Projected Revenue
**LPs**: Frugality, Bias for Action, Invent and Simplify, Think Big
**Best for**: "Tell me about a time you did more with less" / "Tell me about a time you validated a new business opportunity" / MVP thinking

**Situation**: Two data points signaled a massive untapped opportunity: (1) Business listings with a "deal" tag had 12% higher CTR on our platform. (2) External search data showed ~2 million daily users searching Google for brand-specific deals (e.g., "Dominos offers") — traffic we weren't capturing at all.

**Task**: Establish "Deals & Offers" as a new product vertical. But before requesting full investment, I needed to prove we could attract and convert this user segment. Phased roadmap: Phase 1 = MVP to validate opportunity; Phase 2 = scale into full vertical.

**Action**:
1. **Chose frugality over feature-completeness.** Full deals vertical with discovery, homepage integration, brand pipelines = 9-month project. Instead, I proposed simple, standalone, brand-wise deal pages optimized for SEO.
2. **Used existing APIs + manual CMS.** Technical trade-off: existing APIs with lightweight, manually-updated CMS (CSV upload) vs. complex automated brand integration pipeline. Chose speed of learning, accepting operational overhead.
3. **Prioritized brands by data.** Weighted score of external search volume for deal keywords × number of active deals already in our system. Launched highest-potential brands first.

**Result**: Within 6 months: 18,000 new users/day, 720 high-intent enquiries daily, 4% conversion rate. Built financial model from 6-month run rate projecting ₹120M (~$14.4M) in incremental annual revenue at scale (160K daily users target). Data secured leadership buy-in — Deals & Offers now planned as a full dedicated vertical with own engineering team.

**Earned Secret**: "The MVP wasn't a smaller version of the final product — it was a completely different architecture designed to answer one question: will this audience convert? A CSV-upload CMS is embarrassing. But it got us to 18K users/day in weeks, and that data was worth more than any PRD."

---

### ★ S011 — Vertical Marketplace for Interior Design & Construction
**LPs**: Think Big, Have Backbone; Disagree and Commit, Customer Obsession, Dive Deep
**Best for**: "Tell me about a time you convinced leadership to change direction" / "Tell me about a time you identified a hidden user need" / strategic vision

**Situation**: Justdial was seeing vendor churn in several categories. Leadership's initial diagnosis was low engagement — vendors were dormant on the platform and missing incoming leads. They asked me to build engagement features (short videos/reels). But when I dug into the data and spoke to churning vendors, I found a completely different root cause: vendors weren't just consumers of leads — they were also *buyers*. An interior designer needed cement dealers, lighting manufacturers, tile suppliers. They used Justdial for some of this, but also used IndiaMART and vertical marketplaces. Justdial actually had all this supply via its JD Mart platform, but vendors weren't aware of the full breadth of offerings. The problem wasn't engagement — it was visibility and awareness of the B2B ecosystem.

**Task**: Validate the real churn driver and propose a solution. The CPO had already committed to the engagement/reels feature request from leadership. I had to decide whether to build what was asked or push back with a fundamentally different diagnosis.

**Action**:
1. **Validated the root cause.** Ran vendor interviews — vendors confirmed they used other platforms to find their own suppliers. User studies showed vendors didn't know Justdial listed designer home lighting manufacturers or specialized material dealers in their area. The gap was awareness and category discovery, not engagement.
2. **Pushed back on reels/engagement features.** Presented data to CPO showing that engagement features wouldn't address the structural cause of churn. The CPO resisted — the original request had come top-down and was simpler to execute. I argued that reels would generate vanity metrics but not retention.
3. **Proposed a vertical marketplace.** Built a v1 for interior designers, contractors, and architects — aggregating all the supplies and services these professionals need in one place. Goal: solve visibility and access first, then expand into fulfillment if traction justified it.

**Result**: V1 launched, solving the visibility gap for select categories. Validated that vendors would engage with B2B discovery when offerings were curated for their professional needs. Established the foundation for a potential fulfillment marketplace — a fundamentally larger business than engagement features would have created.

**Earned Secret**: "When vendors churn, the reflexive answer is 'build engagement features.' But vendors aren't social media users — they're businesses. They don't want reels; they want to find their cement dealer faster. The churn signal was actually a demand signal for a completely different product."

---

### ★ S012 — Headless Booking Engine: Unlocking Call Center Channel, 48% Order Growth
**LPs**: Invent and Simplify, Think Big, Deliver Results, Bias for Action
**Best for**: Technical depth / platform architecture / "Tell me about a time you found a creative solution to a constraint" / new channel unlocking

**Situation**: 28% of all Justdial leads came from users calling directly — a high-intent cohort. But their experience was poor (rating 2.8–3.2) because the call center connected them to the same unmanaged vendors. JD Xperts (our managed, high-quality service) had a modern web/app booking flow — completely inaccessible to callers. Call center operated on a legacy text-based console (52-second average call time) that couldn't render modern web interfaces.

**Task**: Tap into this underserved, high-intent segment by enabling them to book JD Xperts via the call center. Primary KPI: increase total Xperts order volume. Secondary: validate if callers could be a profitable acquisition channel.

**Action**:
1. **Chose speed over perfection.** Full call center modernization = 9–12 month project. Instead, I designed an **anti-corruption layer** — a mediating service that translated simple XML payloads from the legacy system into structured JSON our modern OMS expected.
2. **Stateless wrapper API.** Key trade-off: stateless (faster to build, agent script manages conversation state) vs. stateful service (cleaner but months longer). Chose stateless — launched in weeks, not quarters. Built short-lived Redis cache to manage booking state during multi-turn calls.
3. **Async post-booking communication.** All confirmations and updates moved to WhatsApp — no need to modify the legacy console for post-booking flows.
4. **Ensured idempotency.** Designed the API to prevent duplicate orders from the legacy system's retry behavior.

**Result**: 48% increase in total daily Xperts orders — 135 to 200 orders/day within 3 weeks. Caller funnel conversion was 42–44%, nearly double the 23–24% web/app rate, proving extreme high intent. Customer satisfaction jumped from 2.8 to 4.5. CPA for this channel was effectively near-zero — most profitable acquisition source.

**Earned Secret**: "The call center wasn't a legacy liability — it was an untapped distribution channel with 2x the conversion rate of our app. The insight was to stop trying to modernize the call center and instead build a translation layer that let it speak to our modern backend. Meet the channel where it is, not where you wish it was."

---

### ★ S013 — Building CRM-Lite from Scratch: -37% Negative Reviews, +22 CSAT
**LPs**: Customer Obsession, Invent and Simplify, Frugality, Insist on Highest Standards
**Best for**: "Tell me about a time you improved customer experience at scale" / "Tell me about a time you did more with less" / ops scaling

**Situation**: JD Xperts had **no CRM**. All complaints routed to a general helpline, manually logged in an Excel tracker by ops. Over 1,000 unclosed tickets. App Store review complaints took a week or more to be seen. At 350 orders/day, the manual process was already failing. With projected 100% YoY growth, it would completely collapse — and we couldn't just hire proportionally more ops agents.

**Task**: Design and build a scalable customer feedback system — effectively a "CRM-lite" from scratch. KPIs: reduce first response time from >24 hours to <10 hours, reduce negative public reviews, improve post-resolution CSAT.

**Action**:
1. **Chose frugal internal build over enterprise CRM.** Zendesk/Salesforce = high cost, 6-month integration. Instead, built a lightweight internal workflow engine that solved the biggest problems in a fraction of time and cost.
2. **Centralized ticket ingestion.** Pulled feedback from calls and App Store reviews into a single database with unique tickets per issue.
3. **Keyword-based auto-classification and routing.** Simple engine: "revisit," "not working," "late" → auto-classify and route to correct team queue (Ops, Category, Refunds). Frugal alternative to ML that solved 80% of routing.
4. **Automated actions.** "Revisit" complaints auto-created follow-up orders for vendors. All users got automated WhatsApp acknowledgment — closing the communication loop immediately.

**Result**: First response time: >24 hours → 9 hours (62.5% improvement). 37% month-on-month reduction in negative public reviews. Post-resolution CSAT increased by 22 points over 3 months. Business scaled orders by 100% without scaling the ops team.

**Earned Secret**: "The insight was that 50% of negative reviews weren't about bad service — they were about feeling ignored. An automated WhatsApp saying 'we've received your complaint and assigned ticket #1234' changed the emotional dynamic before anyone even looked at the issue. The cheapest intervention was acknowledgment."

---

### S014 — Building PM Org from Scratch (6 PMs, 15+ XFN) ⚠️ SEED
**LPs**: Hire and Develop the Best, Strive to be Earth's Best Employer
**Best for**: "Tell me about building a team" / people leadership

- **Situation**: Justdial needed a product management function built from scratch
- **Task**: Hire, build, and lead PM team of 6+ with 15+ cross-functional stakeholders
- **Action**: Defined hiring bar, team structure (pods vs. functional), OKR framework, feedback cadence, career development paths
- **Result**: Functional PM org that delivered on business outcomes
- *Needs detail: hiring philosophy, someone who didn't work out, performance management approach*

---

### ★ S015 — Indian Music Diaries: From Free Blog to 100K Users/Month
**LPs**: Learn and Be Curious, Dive Deep, Frugality, Ownership
**Best for**: "What do you do outside of work that makes you a better PM?" / technical depth / hands-on builder credibility / side project passion

**Situation**: Indian Music Diaries is an indie music magazine covering artists, events, and music news in India — a friend's project that I joined as a music enthusiast. The website started as a free blog with minimal infrastructure, poor performance (PageSpeed score ~30), and was serving about 1,000 users on a hosting setup costing ₹2,500/month.

**Task**: Build and scale the platform from a hobby blog into a real content platform — handling traffic growth, performance, and cost optimization, all as a side project with no budget for enterprise tooling.

**Action**:
1. **Progressive infrastructure evolution.** Started with a free blog → hosted domain on third-party service → self-hosted WordPress → full ownership of hosting, caching, and optimization. Each step taught me a new layer of the web stack.
2. **Performance engineering.** Added CDN layer for content delivery, implemented caching at multiple levels, optimized images and assets. Took PageSpeed Insights score from ~30 to 80+.
3. **Built a content management system.** Created a custom CMS that manages how content is posted across all channels — not just the website but social and distribution channels too.
4. **Cost optimization.** Reduced server costs from ₹2,500/month to ₹800/month while scaling from 1,000 to 100,000 users/month — a 100x traffic increase at 1/3rd the cost.

**Result**: 100K monthly users (100x growth from 1,000). PageSpeed score from ~30 to 80+. Server costs down from ₹2,500 to ₹800/month. Fully self-managed infrastructure with CDN, custom CMS, and multi-channel content distribution.

**Earned Secret**: "Every PM should build and operate something end-to-end — not just write PRDs about it. Running infrastructure taught me what 'latency' actually feels like to a user, what 'cost optimization' means when it's your own money, and why engineers push back when you ask for 'just one more feature' on a fragile system. It made me a fundamentally more empathetic and technically credible PM."

---

### S016 — Appliance Repair Restructure: 3x Professional Income ⚠️ SEED
**LPs**: Earn Trust, Customer Obsession, Strive to be Earth's Best Employer
**Best for**: "Tell me about a hard trade-off" / supply-side marketplace thinking

- **Situation**: Urban Company appliance repair used aggregator model. Professionals underpaid, quality inconsistent
- **Task**: Restructure from aggregator to individual professional model
- **Action**: Economic modeling of both models. Managed transition — aggregator relationships, professional onboarding, quality standards
- **Result**: 3x professional income. Improved service quality. More sustainable model
- *Needs detail: transition plan, aggregator relationship management, economic modeling*

---

### ★ S017 — Category Exploration Pages: Leads 23K → 36.7K/day (59% Increase)
**LPs**: Customer Obsession, Dive Deep, Deliver Results, Are Right A Lot
**Best for**: "Tell me about a time you improved a user experience with data" / "Tell me about a time you pushed back on a simpler approach" / product discovery

**Situation**: User funnel data showed 98,000 daily clicks on homepage "hotkeys" (doctors, repairs, etc.) — but these led to generic listing pages that failed to match the user's specific, unstated need. A user clicking "Doctors" might need a dermatologist vs. pediatrician — the generic page couldn't differentiate. Classic product discovery problem causing drop-off.

**Task**: Improve the user journey for broad-intent searches. Hypothesis: dedicated, curated category exploration pages would guide users better and increase qualified lead generation. Goal: lift lead volume by >15%. Initial scope: 9 super-categories, plan to scale to 30.

**Action**:
1. **Deep dive into user behavior.** Analyzed filter usage patterns and ran surveys. Key insight: a one-size-fits-all template wouldn't work — required modules varied drastically (symptom checker for doctors, insurance cross-sell for movers, price calculator for repairs).
2. **Pushed back on template approach.** Engineering wanted fast template-based solution. I argued against it with user journey data showing module requirements were too varied. Chose quality over speed — 9 custom-tailored exploration pages, each with category-specific discovery modules.
3. **Data-driven prioritization.** Created framework based on traffic volume × lead value to select the first 9 categories.

**Result**: Lead generation surged from 23,000 to 36,700/day — **59% increase**, far exceeding the 15% goal. Blended CTR ~37% (significant lift from generic pages). Irrelevant lead feedback from vendors was 7 percentage points lower than platform average (17% vs. 23%), proving lead quality improved alongside volume.

**Earned Secret**: "Generic pages optimize for the average user, who doesn't exist. When you have 98K daily clicks across 'doctors' and 'repairs,' the variance in intent is enormous. The 59% lift came not from better design but from acknowledging that 'Doctors' is actually 15 different user journeys wearing one label."

---

### ★ S018 — Finding Product-Market Fit Through Customer Segmentation (Urban Company)
**LPs**: Customer Obsession, Dive Deep, Are Right A Lot, Deliver Results
**Best for**: "Tell me about a time you solved a product-market fit problem" / "Tell me about a time customer research changed your strategy" / segmentation

**Situation**: Urban Company Dance category was a strategic puzzle. High top-of-funnel search volume, but unsustainable economics: CAC ~₹2,700 (vs. ~₹1,900 benchmark), user-to-studio connect rate only 0.7. The category was bleeding money despite apparent demand. My assessment: severe product-market fit failure.

**Task**: Diagnose root cause and pivot the offering. KPIs: (1) Reduce CAC to under ₹2,000. (2) Increase user-studio connect rate above 1.0. (3) Improve studio satisfaction with lead quality.

**Action**:
1. **Hypothesis: "homogeneous demand" assumption was wrong.** We were serving a generic product to a highly segmented market.
2. **Customer segmentation initiative.** Personally interviewed 50 customers to understand motivations. Designed quantitative survey to validate segments at scale.
3. **Identified 4 distinct segments**: Parents (kids' classes), Fitness enthusiasts, Hobbyists, Event-based (wedding choreography). Each had unique needs, was commercially viable, and could be targeted with distinct messaging.
4. **Pragmatic trade-off**: 1:1 personalization engine = massive undertaking. Instead, chose segment-level personalization — 4 distinct category funnels. Smaller engineering lift, captured 80% of value. Deprecated the generic offering.

**Result**: CAC reduced 33% (₹2,700 → ₹1,800). User-studio connect rate surged 71% (0.7 → 1.2). Lead quality rating from studios jumped from 2.3 to 4.2. Became the blueprint at Urban Company for how to approach new category launches.

**Earned Secret**: "High search volume with poor conversion isn't a marketing problem — it's a segmentation problem. 'Dance classes' isn't one market; it's four markets wearing one label. The fix wasn't better ads or lower prices — it was admitting that one product can't serve four completely different user motivations."

---

### ★ S019 — Failure Story: Solving the Wrong Problem (Phone Connect Rate)
**LPs**: Ownership, Learn and Be Curious, Dive Deep, Earn Trust
**Best for**: "Tell me about a time you failed" / "Tell me about a time you learned something that changed your approach" / intellectual humility

**Situation**: Justdial's user-to-vendor phone connect rate was 67%, costing an estimated ₹400K/month in lost connections. Vendor interviews consistently pointed to one issue: they didn't recognize our masked numbers and, fearing spam, ignored them.

**Task**: Improve connect rate by making our calls identifiable to vendors. Hypothesis: if vendors saved a fixed Caller ID from Justdial, trust would increase and pickup rate would rise.

**Action**:
1. **Initial MVP**: WhatsApp nudge asking vendors to save our number — adoption was low.
2. **Escalated the test.** Chose speed of learning over caution. Used device-side API to directly write "JD Buyer" to vendor contacts (with permission) — more aggressive test to get an unambiguous signal.

**Result (Failure)**: After a tiny initial bump of 1.5pp, pickup rate **dropped 3 percentage points to 64%**. We made the problem worse.

**Post-Mortem**:
1. **Immediately stopped the experiment.** Took ownership of the failure.
2. **Deep dive into the worst-affected vendors.** Focused on ~100K vendors whose rates dropped most. Went on-field, conducted detailed interviews.
3. **The learning was profound: I had solved the wrong problem.** The issue wasn't "identification" — it was **"negative qualification."** For vendors already fatigued by our call volume, the "JD Buyer" label didn't signal trust — it was a perfect signal to *ignore* the call. They knew it was a platform lead, not a potentially more valuable direct customer. My solution had given them a tool to filter us out.

**Earned Secret**: "A broad assessment is not enough. I correctly identified the symptom — vendors not recognizing the number. But I failed to understand the deeper vendor psychology and business context. The vendor who doesn't pick up isn't confused about who's calling — they're making a rational economic decision about which calls are worth their time. Since then, I never ship a solution without first understanding the user's underlying incentive structure, not just their stated pain point."

---

## LP Drill Reminders

**When you hear the LP, reach for the story:**

| If they ask about... | Start with... | Key phrase to anchor |
|---|---|---|
| Customer focus / user empathy | S003 | "80,000 dead searches daily from high-intent users" |
| Ownership / end-to-end | S001 | "I was the first hire, negotiated my role, built the org" |
| Simplification / innovation | S004 | "3 months → 3 weeks for new vertical launches" |
| Data-driven decisions | S005 | "Averages were masking localized capacity gaps" |
| Learning / curiosity | S015 | "Built a 100K-user platform as a side project — taught me infra" |
| Hiring / team building | S014 | "Built PM org from scratch — 6 PMs, 15+ cross-functional" |
| Quality / standards | S007 | "−₹200 LTV per price-gouged customer — delayed launch" |
| Big vision / ambition | S011 | "Vendors don't want reels — they want a vertical marketplace" |
| Speed / urgency | S012 | "Anti-corruption layer, launched in weeks, 48% order growth" |
| Doing more with less | S013 | "Built CRM-lite from scratch vs. Zendesk — scaled 100% without hiring" |
| Trust / influence | S007 | "₹650 swing per customer — the argument becomes arithmetic" |
| Deep analysis | S018 | "50 customer interviews → 4 segments → CAC dropped 33%" |
| Pushing back | S011 | "CPO wanted reels — I showed the real churn driver was supply access" |
| Delivering results | S001 | "₹4.8cr ARR, 5.4x unit economics, from zero" |
| People / culture | S014 | "Defined hiring bar, career paths, feedback cadence" |
| Broad impact | S004 | "Shared OMS enabled 4 business lines, 99.99% uptime" |
| Failure / learning | S019 | "Connect rate dropped 3pp — I'd given vendors a filter tool" |
| Product-market fit | S018 | "Dance wasn't one market — it was four" |
| New channel / growth | S012 | "Call center had 2x conversion rate of our app" |
| AI/ML for business impact | S020 | "78% of 'spam' calls were real leads — salvaged ₹15cr" |
| Side project / builder | S015 | "Free blog → 100K users, PageSpeed 30→80+, costs down 68%" |

---

### ★ S020 — Lead Salvaging with AI: ₹15cr Revenue Rescued from "Spam" Calls
**LPs**: Customer Obsession, Invent and Simplify, Deliver Results, Dive Deep
**Best for**: "Tell me about a time you found revenue in an unexpected place" / "Tell me about a time you used AI/ML to solve a business problem" / vendor trust

**Situation**: Justdial's paying vendors were manually flagging 80,000 calls per day as "irrelevant" or "spam." My deep dive into call transcripts revealed a shocking insight: 78% of these flagged calls were actually high-intent users who were simply mismatched by the rigid keyword-based system. This was destroying vendor trust (VSAT at 81%) and costing millions in lost leads.

**Task**: Stop the revenue leak and rebuild vendor trust by salvaging the 78% of good leads being incorrectly discarded. KPIs: reroute significant portion of leads, increase VSAT from 81% to >83%.

**Action**:
1. **Business-driven traffic segmentation.** We were GPU-bound — couldn't process all 80K calls in real-time. Created a prioritization matrix based on urgency of need × average order value. Focused expensive real-time processing on 25,000 daily calls with highest business impact; rest stayed on cheaper async path. Clear cost vs. latency trade-off.
2. **Technical frugality on the sync path.** For real-time calls, implemented a "chunking" technique using keyword spotting to stop transcription early once intent was identified. Reduced required GPU compute by 75%, making the synchronous solution financially viable.
3. **LLM-powered intent extraction and rerouting.** System used LLM to identify user's true intent from the transcript and automatically created a new, correctly matched lead — turning "spam" into revenue.

**Result**: With ARPL (Average Revenue Per Lead) of ₹52, the system salvaged an estimated ₹15 crore (~$1.8M) in annual revenue. VSAT improved from 81% to 83.5% within first quarter. Built the business case for the larger strategic search platform overhaul (S003).

**Earned Secret**: "The vendors weren't wrong to flag those calls — they were getting mismatched leads. But instead of fixing the matching upstream (a massive rebuild), we built a salvage engine downstream. Sometimes the fastest path to revenue isn't preventing the failure — it's recovering from it intelligently."

---

## ⚠️ Remaining Seeds — Not Yet Full STAR

- **S002** — Unit economics (heavy overlap with S001 — use S001 as primary, deploy only if interviewer probes specifically on unit economics mechanics)
- **S014** — Building PM Org (skipped for now — come back to it)
- **S016** — Appliance Repair Restructure: 3x professional income (needs details)

## Gaps Filled ✅
- ~~Failure/Learning~~ → **S019** (Phone Connect Rate failure)
- ~~Data-driven persuasion with specific numbers~~ → **S007** (LTV analysis with exact ₹ figures)
- ~~Product discovery / user research~~ → **S018** (50 interviews, 4 segments)
- ~~AI/ML business impact~~ → **S020** (Lead Salvaging, ₹15cr rescued)
- ~~Side project / builder credibility~~ → **S015** (Indian Music Diaries, 100K users)

---

*Last updated: 2026-03-19 | Screen: 2026-03-20*
