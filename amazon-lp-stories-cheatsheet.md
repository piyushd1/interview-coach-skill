# Amazon LP Stories Cheatsheet — Piyush Deveshwar
**Amazon Sr. PM - Mobile Growth, EMXO PLX | Screening: 2026-03-20**

---

## Quick Reference: LP → Story Map

| Leadership Principle | Best Story | Backup Story |
|---|---|---|
| Customer Obsession | S003 (LLM Search — rescuing 65K failed searches/day) | S006 (Cancellations 20%→3%, NPS turnaround) |
| Ownership | S001 (JD Xperts 0-to-1, ₹4.8cr ARR) | S009 (Self-serve vendor platform, ₹13cr unlock) |
| Invent and Simplify | S004 (Shared OMS — 3 months→3 weeks) | S003 (Repurposed internal LLM service) |
| Are Right, A Lot | S005 (Invented "Lost Potential Bookings" KPI) | S007 (LTV data → C-suite pricing) |
| Learn and Be Curious | S003 (LLM search — self-taught LangChain, fine-tuning) | S015 (WordPress→AWS side project) |
| Hire and Develop the Best | S014 (Built PM org from scratch, 6 PMs) | S001 (First hire, built full team) |
| Insist on the Highest Standards | S006 (Cancellations 20%→3%, NPS -12→+28) | S003 (3-stage model evolution for quality) |
| Think Big | S011 (C-suite pitch for vertical marketplace) | S001 (Diversification from adtech to services) |
| Bias for Action | S010 (Frugal MVP: Deals & Offers, 160K daily users) | S008 (AC Repairs: 0→₹1cr in 6 months) |
| Frugality | S010 (Frugal MVP) | S004 (Shared OMS — build once, launch 4 verticals) |
| Earn Trust | S007 (LTV data → convinced C-suite on pricing) | S016 (Restructured model → 3x professional income) |
| Dive Deep | S003 (Root-caused 4 failure buckets, built LLM pipeline) | S005 (Discovered hidden metric gap) |
| Have Backbone; Disagree and Commit | S007 (Challenged C-suite pricing position with data) | S011 (Pushed vertical marketplace against horizontal status quo) |
| Deliver Results | S001 (₹4.8cr ARR, 5.4x unit economics) | S009 (₹13cr revenue unlock) |
| Strive to be Earth's Best Employer | S014 (Built PM org, culture, career paths) | S016 (3x professional income) |
| Success and Scale Bring Broad Responsibility | S004 (Shared OMS enabled 4 business lines) | S012 (Headless booking engine, 48% volume growth) |

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

**Result**: New vertical launch time dropped from ~3 months to ~3 weeks. Enabled 4 new business lines. Freed engineering bandwidth across the org. Standardized internal processes.

**Earned Secret**: "The hardest part wasn't the architecture — it was the org politics. Team leads didn't want to depend on shared services they didn't control. The technical decision was obvious; the organizational decision required earning trust that shared infrastructure wouldn't become a bottleneck. I had to prove reliability before teams would voluntarily adopt."

---

### S005 — Inventing "Lost Potential Bookings" KPI ⚠️ SEED
**LPs**: Are Right A Lot, Dive Deep, Have Backbone; Disagree and Commit
**Best for**: "Tell me about a time you used data to change a decision" / strategic thinking

- **Situation**: Org metrics weren't capturing missed opportunities — only tracking what happened, not what could have happened
- **Task**: Created new KPI — "Lost Potential Bookings" — to quantify what the org was leaving on the table
- **Action**: Built methodology to estimate potential vs. actual bookings. Socialized with leadership. The metric initially made current performance look worse — required courage to present
- **Result**: KPI shifted org strategy. Leadership reallocated resources based on new visibility
- *Needs detail: methodology, specific decisions that changed, pushback handling*

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

**Result**: Vendor cancellations dropped from 20% to 3%. NPS flipped from -12 to +28. Ops bandwidth freed up. Built the quality foundation that made commission-on-completion economics work.

**Earned Secret**: "The data initially misled us — we assumed cancellation = bad vendor. But ratings measured attitude and service quality, not technical capability for that specific appliance. The fix wasn't a better algorithm — it was asking the right question: not 'who is good?' but 'who is good at THIS?'"

---

### S007 — LTV Analysis → C-Suite Pricing Decision ⚠️ SEED
**LPs**: Earn Trust, Have Backbone; Disagree and Commit, Are Right A Lot
**Best for**: "Tell me about a time you influenced without authority" / data-driven persuasion

- **Situation**: C-suite had a pricing position. Data suggested a different direction
- **Task**: Build data-driven case using LTV analysis to influence pricing decision at Urban Company
- **Action**: Built LTV model segmented by customer cohort. Presented analysis showing long-term value was being sacrificed for short-term revenue. Challenged C-suite's position respectfully with data
- **Result**: C-suite approved new pricing strategy. 85% complaint reduction. Business impact validated
- *Needs detail: specific LTV numbers, what the C-suite's original position was, the "killer slide"*

---

### S008 — Scaling AC Repairs to ₹1cr Revenue in 6 Months ⚠️ SEED
**LPs**: Bias for Action, Deliver Results, Ownership
**Best for**: "Tell me about a time you launched something quickly" / 0-to-1 in new category

- **Situation**: Urban Company was primarily beauty/home services. AC Repairs was a new category — zero presence
- **Task**: Launch and scale AC Repairs from zero to meaningful revenue
- **Action**: Supply acquisition (technician recruitment + training), pricing strategy, service design, GTM — moved fast with lean validation
- **Result**: ₹1cr revenue in 6 months. Became #1 acquisition channel for Urban Company
- *Needs detail: supply-side strategy, category selection rationale, growth mechanism*

---

### S010 — Frugal MVP: Deals & Offers → 160K Daily Users ⚠️ SEED
**LPs**: Frugality, Bias for Action, Invent and Simplify
**Best for**: "Tell me about a time you did more with less" / MVP thinking

- **Situation**: Justdial needed deals/offers feature to drive engagement and acquisition
- **Task**: Build and launch with minimal resources — frugal MVP
- **Action**: Ruthless scope cuts. Built minimum feature set that delivered core value. Launched lean, iterated based on data
- **Result**: 160K new daily users run-rate achieved cost-effectively
- *Needs detail: what was cut, what was kept, launch timeline, iteration decisions*

---

### S011 — Influencing C-Suite for Vertical Marketplace ⚠️ SEED
**LPs**: Think Big, Have Backbone; Disagree and Commit, Earn Trust
**Best for**: "Tell me about a time you convinced leadership to change direction" / strategic vision

- **Situation**: Justdial's horizontal search model had limitations for certain business segments
- **Task**: Convince C-suite to invest in vertical marketplace approach for SMBs
- **Action**: Built business case — TAM analysis, competitive landscape, pilot design. Managed pushback from those invested in horizontal model
- **Result**: Secured investment. Built vertical marketplace with measurable business results
- *Needs detail: specific objections, pilot results, business case numbers*

---

### S012 — Headless Booking Engine: 48% Volume Growth ⚠️ SEED
**LPs**: Invent and Simplify, Think Big, Deliver Results
**Best for**: Technical depth / platform architecture / "how do you think about system design?"

- **Situation**: Booking infrastructure tightly coupled with front-end, limiting speed and flexibility
- **Task**: Design headless booking engine consumable by multiple interfaces
- **Action**: API-first architecture, decoupled from presentation layer. Migration strategy for existing integrations
- **Result**: 48% volume growth without additional engineering overhead
- *Needs detail: API design decisions, migration plan, which surfaces consumed it*

---

### S013 — Automated Complaint Resolution: -37% Negative Reviews ⚠️ SEED
**LPs**: Customer Obsession, Invent and Simplify
**Best for**: "Tell me about a time you improved customer experience at scale" / automation

- **Situation**: High volume complaints damaging brand, consuming support resources
- **Task**: Build automated complaint resolution
- **Action**: NLP-based triage, automated resolution for common patterns, human escalation for complex cases
- **Result**: -37% negative reviews. +22 CSAT points
- *Needs detail: automation vs. human-in-the-loop boundary, classification approach*

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

### S015 — Indian Music Diaries: WordPress → AWS Migration ⚠️ SEED
**LPs**: Learn and Be Curious, Dive Deep
**Best for**: Technical depth / hands-on builder credibility / side project passion

- **Situation**: Personal music blog on WordPress with poor performance (PageSpeed <50)
- **Task**: Redesign and migrate to modern architecture on AWS
- **Action**: AWS service selection, CDN setup, performance optimization, migration execution
- **Result**: PageSpeed from <50 to >90. Modern scalable architecture
- *Use for: "What do you do outside of work that makes you a better PM?" or technical credibility*

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

## LP Drill Reminders

**When you hear the LP, reach for the story:**

| If they ask about... | Start with... | Key phrase to anchor |
|---|---|---|
| Customer focus / user empathy | S003 | "80,000 dead searches daily from high-intent users" |
| Ownership / end-to-end | S001 | "I was the first hire, negotiated my role, built the org" |
| Simplification / innovation | S004 | "3 months → 3 weeks for new vertical launches" |
| Data-driven decisions | S005 | "The metric made current performance look worse — that's why it mattered" |
| Learning / curiosity | S003 | "We treated the model as a product we owned" |
| Hiring / team building | S014 | "Built PM org from scratch — 6 PMs, 15+ cross-functional" |
| Quality / standards | S006 | "Cancellations 20% → 3%, NPS -12 → +28" |
| Big vision / ambition | S011 | "Convinced C-suite to shift from horizontal to vertical" |
| Speed / urgency | S010 | "160K daily users from a frugal MVP" |
| Doing more with less | S010 | "Frugal MVP — ruthless scope cuts, core value only" |
| Trust / influence | S007 | "LTV data that challenged the C-suite's pricing position" |
| Deep analysis | S003 | "Root-caused into 4 failure buckets" |
| Pushing back | S007 | "Respectfully challenged with data" |
| Delivering results | S001 | "₹4.8cr ARR, 5.4x unit economics, from zero" |
| People / culture | S014 | "Defined hiring bar, career paths, feedback cadence" |
| Broad impact | S004 | "Shared OMS enabled 4 business lines" |

---

## ⚠️ Gap Stories — Not Yet Built

These will likely NOT come up in a screening round, but flag for future loops:
- **Failure/Learning** — No explicit failure story exists. Need one with real consequences.
- **Peer influence without authority** — C-suite influence covered, peer-level thin.
- **Team conflict / difficult management** — Only S014 covers people leadership; needs a "hard conversation" story.

---

*Last updated: 2026-03-19 | Screen: 2026-03-20*
