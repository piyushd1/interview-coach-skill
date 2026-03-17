# Story Seeds — Pre-Mapped from Resume

These story seeds are extracted from the candidate's resume and pre-mapped to interview round types. Each seed contains a STAR skeleton, round-type suitability, follow-up question trees, and competency tags.

When running `stories add`, reference these seeds to accelerate story building. The candidate should validate and flesh out the STAR details — the skeletons below are inferred from resume data and need real narrative detail.

---

## Round Type Legend

- **Business** ★★★ = Core business story (P&L, unit economics, GTM, pricing, market strategy)
- **Product** ★★★ = Core product story (user problems, roadmap, metrics, launches, product sense)
- **Technical** ★★★ = Core technical story (system design, architecture decisions, AI/ML, data pipelines)
- ★★ = Moderate fit (can be framed for this round with emphasis shift)
- ★ = Weak fit (only use if no better option exists)

---

## S001 — Zero-to-One P&L: JD Xperts to ₹4.8cr ARR

**Source**: Justdial, GPM (2020-2023)
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: Justdial needed a new revenue stream. No B2B recruitment product existed.
- **Task**: Build JD Xperts from scratch — own the entire business including P&L, product, GTM, team.
- **Action**: [Candidate to detail: market research, MVP decisions, pricing model development, hiring, go-to-market, iteration cycles]
- **Result**: ₹4.8cr ARR, 5.4x unit economics, 5000+ paying customers.

### Earned Secret Prompt
"What do you know about building a B2B product inside a B2C company that most people wouldn't expect?"

### Follow-Up Trees

**Business Round:**
1. "Walk me through the P&L. What were your cost drivers? How did margins evolve?"
   → Emphasize: cost structure decisions, where you invested vs. cut, margin trajectory over time
2. "How did you arrive at the pricing model? What alternatives did you consider?"
   → Emphasize: pricing experimentation, competitive benchmarking, willingness-to-pay research
3. "How did you validate demand before committing resources?"
   → Emphasize: lean validation approach, what signals you looked for, when you decided to scale
4. "What was the hardest trade-off between growth and profitability?"
   → Emphasize: specific decision point, data used, outcome of the choice
5. "If you had 10x the budget from day one, what would you have done differently?"
   → Emphasize: resource allocation thinking, what constraints actually helped

**Product Round:**
1. "How did you decide what to build first? What was your prioritization framework?"
   → Emphasize: user research signals, MVP scoping, what you deliberately excluded
2. "How did you handle the transition from MVP to scale?"
   → Emphasize: architecture choices, feature evolution, user feedback loops
3. "What did users hate about the initial version? How did you respond?"
   → Emphasize: customer feedback integration, iteration speed, what you kept despite complaints

**Technical Round:**
1. "What was the technical architecture? How did you think about scalability?"
   → Emphasize: PM-style technical thinking — system design communication, build vs. buy decisions
2. "How did you handle data and analytics infrastructure for a new product?"
   → Emphasize: instrumentation decisions, what metrics you needed to track, how you built visibility

### Competency Tags
- **Primary**: P&L Ownership, 0-to-1 Building
- **Secondary**: GTM Execution, Pricing Strategy, Team Building

---

## S002 — 5.4x Unit Economics Transformation

**Source**: Justdial, GPM (JD Xperts)
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: JD Xperts needed sustainable economics to justify continued investment.
- **Task**: Transform unit economics from uncertain to 5.4x healthy.
- **Action**: [Candidate to detail: what levers they pulled — pricing changes, cost reduction, efficiency gains, automation]
- **Result**: 5.4x unit economics. Business became self-sustaining and justified scaling.

### Earned Secret Prompt
"What's the most counterintuitive thing you learned about unit economics in a marketplace/platform business?"

### Follow-Up Trees

**Business Round:**
1. "Break down the 5.4x — what were the components?"
   → Emphasize: CAC, LTV, margins, which lever had the most impact
2. "When you started, what was the unit economics? What was the trajectory?"
   → Emphasize: the journey from negative/uncertain to healthy — decisions at each stage
3. "How did you balance unit economics improvement against growth?"
   → Emphasize: specific trade-off moments, what you sacrificed for margin improvement
4. "How did you forecast and model the unit economics? What was your instrumentation?"
   → Emphasize: financial modeling approach, what data you tracked, how often you recalibrated

**Product Round:**
1. "What product changes drove the biggest unit economics improvements?"
   → Emphasize: feature/flow changes that reduced cost or increased revenue per unit
2. "How did you instrument the product to track unit economics in real-time?"
   → Emphasize: analytics and dashboards, what signals triggered action

### Competency Tags
- **Primary**: Unit Economics, Financial Acumen
- **Secondary**: Pricing Strategy, Data-Driven Decision Making

---

## S003 — Solving 11% Search Failure with LLM Engine

**Source**: Justdial, GPM (2023-2026)
**Rounds**: Business ★ | Product ★★★ | Technical ★★★

### STAR Skeleton
- **Situation**: 11% of searches on Justdial resulted in failure — no results or irrelevant results. This affected 90K daily leads.
- **Task**: Design and ship an LLM-powered search engine to solve the failure rate.
- **Action**: Cross-functional team of 8. [Candidate to detail: problem diagnosis, solution architecture, LLM choices, RAG pipeline design, testing approach, rollout strategy]
- **Result**: Dramatically reduced search failure rate. 90K daily leads recovered/improved.

### Earned Secret Prompt
"What did you learn about deploying LLMs in production at scale that surprised you?"

### Follow-Up Trees

**Product Round:**
1. "How did you define and measure 'search failure'? What was the taxonomy?"
   → Emphasize: problem definition rigor, distinguishing failure types, prioritization of which to solve first
2. "How did you decide LLM was the right solution vs. traditional NLP or rule-based?"
   → Emphasize: alternatives considered, build vs. buy evaluation, cost-benefit analysis
3. "What was the user experience change? How did users react?"
   → Emphasize: A/B testing approach, user qualitative feedback, metric movements

**Technical Round:**
1. "Walk me through the LLM architecture. What model? What's the RAG pipeline?"
   → Emphasize: architecture decisions, embedding strategy, retrieval approach, latency considerations
2. "How did you handle hallucinations and quality control?"
   → Emphasize: guardrails, evaluation framework, monitoring, edge cases
3. "What were the cost considerations? How did you optimize inference costs?"
   → Emphasize: cost per query, caching strategy, model selection trade-offs
4. "How did you handle the cold start problem and data quality?"
   → Emphasize: training data curation, feedback loops, continuous improvement pipeline
5. "What was the testing and rollout strategy? How did you manage risk?"
   → Emphasize: staged rollout, canary deployment, rollback planning, monitoring

**Business Round:**
1. "What was the business impact of solving search failure? How did you quantify it?"
   → Emphasize: revenue impact, user retention improvement, competitive positioning

### Competency Tags
- **Primary**: AI/ML Product Thinking, Technical Product Leadership
- **Secondary**: Cross-Functional Leadership, Problem Diagnosis

---

## S004 — Foreseeing the Bottleneck: Shared OMS Architecture

**Source**: Justdial, GPM (2023-2026)
**Rounds**: Business ★ | Product ★★ | Technical ★★★

### STAR Skeleton
- **Situation**: Multiple verticals at Justdial were building their own order management systems independently.
- **Task**: Foresaw this would become a scaling bottleneck. Advocated for and designed a shared OMS.
- **Action**: [Candidate to detail: how they identified the problem before it was urgent, how they built the case, architecture decisions, stakeholder alignment across verticals]
- **Result**: 65% reduction in new vertical launch time. Shared architecture enabled faster scaling.

### Earned Secret Prompt
"How do you convince an organization to invest in platform work when every team wants to build their own thing?"

### Follow-Up Trees

**Technical Round:**
1. "Walk me through the OMS architecture. How did you handle different verticals' needs?"
   → Emphasize: abstraction design, extensibility, what was shared vs. customizable
2. "How did you migrate existing verticals to the shared system?"
   → Emphasize: migration strategy, backward compatibility, risk management
3. "What trade-offs did you make between flexibility and standardization?"
   → Emphasize: design principles, where you drew the line, what went wrong

**Product Round:**
1. "How did you prioritize which verticals to onboard first?"
   → Emphasize: stakeholder complexity, dependency mapping, value sequencing
2. "How did you measure success? What was 'launch time reduction' baseline?"
   → Emphasize: metric definition, before/after measurement, attribution

**Business Round:**
1. "What was the cost of NOT building the shared OMS?"
   → Emphasize: opportunity cost quantification, technical debt accumulation projections

### Competency Tags
- **Primary**: Platform Strategy, System Design Communication
- **Secondary**: Strategic Thinking, Influence Without Authority

---

## S005 — Inventing "Lost Potential Bookings" — Shifting Org Strategy

**Source**: Justdial, GPM
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: The org was focused on metrics that weren't capturing the full picture of missed opportunities.
- **Task**: Created a new KPI — "Lost Potential Bookings" — to quantify what the organization was leaving on the table.
- **Action**: [Candidate to detail: how they identified the gap, how they defined and measured the metric, how they socialized it, how it changed priorities]
- **Result**: The KPI shifted org strategy. Leadership started making different decisions based on this new visibility.

### Earned Secret Prompt
"When is inventing a new metric more valuable than improving an existing one?"

### Follow-Up Trees

**Business Round:**
1. "How did you define 'Lost Potential Bookings'? What was the methodology?"
   → Emphasize: analytical rigor, how you estimated potential vs. actual, what data sources
2. "How did you convince leadership to adopt a completely new metric?"
   → Emphasize: C-suite communication, data presentation, gaining buy-in for something that made current performance look worse
3. "What decisions changed as a result of this metric? Give specific examples."
   → Emphasize: strategy shift, resource reallocation, specific initiatives launched because of it
4. "How did you prevent gaming of the new metric?"
   → Emphasize: metric design integrity, complementary metrics, monitoring for unintended consequences

**Product Round:**
1. "How did you build the instrumentation to track this KPI?"
   → Emphasize: data pipeline, dashboarding, real-time vs. batch, what was hard to measure
2. "How did LPB change product prioritization?"
   → Emphasize: roadmap decisions that shifted, features that got deprioritized or elevated

### Competency Tags
- **Primary**: Strategic Thinking, C-Suite Influence
- **Secondary**: Data-Driven Decision Making, Metric Design

---

## S006 — Cancellations from 20% to 3% — NPS Turnaround

**Source**: Justdial, GPM (Matchmaking Algorithm)
**Rounds**: Business ★★ | Product ★★★ | Technical ★★

### STAR Skeleton
- **Situation**: 20% cancellation rate in the marketplace. NPS was -12, indicating deep user dissatisfaction.
- **Task**: Fix the root cause — the matchmaking algorithm was sending wrong service providers.
- **Action**: [Candidate to detail: root cause analysis, algorithm redesign approach, what signals were used, testing methodology, rollout]
- **Result**: Cancellations dropped from 20% to 3%. NPS went from -12 to +28.

### Earned Secret Prompt
"What did you learn about matching supply and demand that the textbooks don't teach you?"

### Follow-Up Trees

**Product Round:**
1. "How did you diagnose that matchmaking was the root cause, not pricing or availability?"
   → Emphasize: hypothesis-driven diagnosis, data analysis, ruling out alternatives
2. "What signals went into the new algorithm? How did you weigh them?"
   → Emphasize: feature engineering thinking, what data was available vs. needed, experimentation
3. "How did you measure the NPS improvement? Was it correlated or causal?"
   → Emphasize: attribution methodology, confounding factors, holdout testing

**Technical Round:**
1. "Walk me through the algorithm architecture. What changed from old to new?"
   → Emphasize: the design logic, how matching criteria were determined, computational trade-offs
2. "How did you handle edge cases — new providers, sparse data, cold start?"
   → Emphasize: practical ML/algorithm challenges, how you handled imperfect data

**Business Round:**
1. "What was the revenue impact of reducing cancellations from 20% to 3%?"
   → Emphasize: financial quantification, retention economics, second-order effects on supply side
2. "How did this affect your supply-side relationships?"
   → Emphasize: marketplace dynamics, provider satisfaction, retention impacts

### Competency Tags
- **Primary**: Problem Diagnosis, Marketplace Strategy
- **Secondary**: AI/ML Product Thinking, User Experience

---

## S007 — Using LTV Data to Convince C-Suite on Pricing

**Source**: Urban Company, Senior PM (2019-2020)
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: Pricing strategy was contentious. C-suite had a different view on where pricing should go.
- **Task**: Build a data-driven case using LTV analysis to influence pricing decisions.
- **Action**: [Candidate to detail: LTV analysis methodology, how they segmented customers, how they modeled pricing impact, how they presented to leadership, what pushback they got]
- **Result**: C-suite approved new pricing strategy. 85% complaint reduction. Business impact validated.

### Earned Secret Prompt
"What's the hardest part about influencing C-suite decisions with data, that isn't about the data itself?"

### Follow-Up Trees

**Business Round:**
1. "Walk me through the LTV model. What were the inputs? How did you segment?"
   → Emphasize: analytical sophistication, cohort analysis, segmentation logic
2. "What was the C-suite's initial position, and why were they wrong?"
   → Emphasize: understanding their perspective, respecting their logic, showing where data diverged
3. "How did you present the case? What format? What was the killer slide?"
   → Emphasize: executive communication skills, data storytelling, persuasion technique
4. "What happened after the price change? Did the LTV model prediction hold?"
   → Emphasize: validation, intellectual honesty about what you predicted correctly vs. not

**Product Round:**
1. "How did pricing changes affect the product experience?"
   → Emphasize: user behavior changes, perception shifts, complaint patterns
2. "How did you instrument the product to track pricing impact in real-time?"
   → Emphasize: dashboard design, alerting, leading indicators

### Competency Tags
- **Primary**: C-Suite Influence, Pricing Strategy
- **Secondary**: Data-Driven Decision Making, Financial Acumen

---

## S008 — Scaling AC Repairs to ₹1cr Revenue in 6 Months

**Source**: Urban Company, Senior PM (2019-2020)
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: Urban Company was primarily a beauty/home services marketplace. AC Repairs was a new category.
- **Task**: Launch and scale AC Repairs from zero to ₹1cr revenue. Became #1 acquisition channel.
- **Action**: [Candidate to detail: market research, supply acquisition, pricing, service design, marketing/GTM]
- **Result**: ₹1cr revenue in 6 months. #1 acquisition channel.

### Earned Secret Prompt
"What's different about scaling a services category vs. a product feature?"

### Follow-Up Trees

**Business Round:**
1. "How did you know AC Repairs was the right category to launch? What alternatives did you evaluate?"
   → Emphasize: market analysis, category selection framework, competitive landscape
2. "Walk me through the unit economics at launch vs. 6 months in."
   → Emphasize: margin evolution, cost structure, what scaled well vs. what didn't
3. "How did it become #1 acquisition channel? What was the growth mechanism?"
   → Emphasize: growth loops, word-of-mouth, cross-sell dynamics
4. "What was the supply-side strategy? How did you recruit and retain AC technicians?"
   → Emphasize: supply acquisition cost, training, quality control, retention

**Product Round:**
1. "What was the product experience for first-time users? How did you optimize conversion?"
   → Emphasize: funnel thinking, onboarding, trust signals, booking flow
2. "How did you handle quality control for a skilled trades category?"
   → Emphasize: rating systems, quality metrics, customer satisfaction loops

### Competency Tags
- **Primary**: 0-to-1 Building, GTM Execution
- **Secondary**: Marketplace Strategy, Category Building

---

## S009 — 19% QoQ Revenue: Mobile Merchant Strategy

**Source**: Justdial, GPM (Merchant-Centric)
**Rounds**: Business ★★ | Product ★★★ | Technical ★

### STAR Skeleton
- **Situation**: Merchant engagement on mobile was low, contributing to churn.
- **Task**: Build a merchant-centric mobile strategy to increase revenue and reduce churn.
- **Action**: [Candidate to detail: merchant research, product redesign, feature prioritization, retention mechanics]
- **Result**: 19% QoQ revenue increase. Merchant churn reduced from 17% to 14%.

### Earned Secret Prompt
"What's the most important thing about building for merchants/supply-side that consumer PMs miss?"

### Follow-Up Trees

**Product Round:**
1. "How did you understand merchant needs? What research methods?"
   → Emphasize: qualitative + quantitative research, going into the field, merchant personas
2. "What features drove the revenue increase? How did you prioritize?"
   → Emphasize: feature-revenue attribution, experimentation, what you killed vs. shipped
3. "How did you reduce churn? What was the root cause?"
   → Emphasize: churn analysis, cohort behavior, intervention design

**Business Round:**
1. "Walk me through the merchant economics. What drives churn vs. retention?"
   → Emphasize: LTV by segment, ROI for merchants, value demonstration
2. "How did you balance merchant needs against consumer experience?"
   → Emphasize: two-sided marketplace trade-offs, where interests aligned vs. diverged

### Competency Tags
- **Primary**: Marketplace Strategy, User Research
- **Secondary**: Retention/Churn, Revenue Growth

---

## S010 — Frugal MVP: Deals & Offers — 160K Daily Users

**Source**: Justdial, GPM
**Rounds**: Business ★★ | Product ★★★ | Technical ★

### STAR Skeleton
- **Situation**: Justdial needed a deals/offers feature to drive user engagement and new user acquisition.
- **Task**: Build and launch with minimal resources — frugal MVP approach.
- **Action**: [Candidate to detail: how they scoped the MVP, what they cut, what they built, how they launched]
- **Result**: 160K new daily users run-rate achieved cost-effectively.

### Earned Secret Prompt
"When is a frugal MVP the right approach, and when does it hurt more than it helps?"

### Follow-Up Trees

**Product Round:**
1. "How did you decide what was 'minimum' in his MVP? What did you deliberately exclude?"
   → Emphasize: scope discipline, user needs vs. engineering cost trade-offs, launch criteria
2. "How did you measure success? What was the 160K run-rate trajectory?"
   → Emphasize: growth curve, leading indicators, when you knew it was working
3. "What would you add in v2 that you cut from v1?"
   → Emphasize: learning from launch, user feedback, prioritization for next phase

**Business Round:**
1. "What was the cost to build vs. the value generated?"
   → Emphasize: ROI thinking, engineering investment justification
2. "How did this affect user acquisition costs for the broader platform?"
   → Emphasize: acquisition channel economics, cross-feature synergies

### Competency Tags
- **Primary**: 0-to-1 Building, Product Sense
- **Secondary**: Frugal Innovation, Execution Speed

---

## S011 — Influencing C-Suite for Vertical Marketplace

**Source**: Justdial, GPM (Business Marketplace for SMBs)
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: Justdial's traditional horizontal search model had limitations for certain business segments.
- **Task**: Convince C-suite to invest in a vertical marketplace approach for SMBs.
- **Action**: [Candidate to detail: business case construction, data analysis, presentation approach, pilot design, stakeholder management]
- **Result**: Secured investment. Built vertical marketplace with measurable business results.

### Earned Secret Prompt
"What makes a horizontal marketplace vs. vertical marketplace decision? When is each the right choice?"

### Follow-Up Trees

**Business Round:**
1. "What was the business case? How did you model the opportunity?"
   → Emphasize: TAM/SAM/SOM, financial projections, competitive positioning
2. "What was the pushback from C-suite? How did you handle it?"
   → Emphasize: objection handling, data vs. narrative, building coalition
3. "What would have happened if the vertical marketplace failed?"
   → Emphasize: risk management, exit criteria, downside planning

**Product Round:**
1. "How was the vertical marketplace product different from the horizontal search?"
   → Emphasize: user experience design, what changed for buyers and sellers
2. "How did you design the pilot? What signals determined go/no-go?"
   → Emphasize: pilot design, success criteria, measurement framework

### Competency Tags
- **Primary**: C-Suite Influence, Strategic Thinking
- **Secondary**: Marketplace Strategy, Business Case Building

---

## S012 — Headless Booking Engine: 48% Volume Growth

**Source**: Justdial, GPM (2023-2026)
**Rounds**: Business ★ | Product ★★ | Technical ★★★

### STAR Skeleton
- **Situation**: Booking infrastructure was tightly coupled with the front-end, limiting speed and flexibility.
- **Task**: Design a headless booking engine that could be consumed by multiple interfaces.
- **Action**: [Candidate to detail: architecture decisions, API design, migration strategy, cross-team coordination]
- **Result**: 48% volume growth without additional engineering overhead.

### Earned Secret Prompt
"When is 'headless' architecture the right choice for a product team, and when is it over-engineering?"

### Follow-Up Trees

**Technical Round:**
1. "Walk me through the headless architecture. What was the API contract?"
   → Emphasize: API design principles, versioning strategy, backward compatibility
2. "How did you handle the migration from coupled to headless?"
   → Emphasize: migration strategy, risk management, rollback planning
3. "What was the performance impact? How did you ensure latency didn't increase?"
   → Emphasize: performance testing, monitoring, optimization

**Product Round:**
1. "How did 48% volume growth happen without engineering overhead? Break it down."
   → Emphasize: leverage effects, what teams could do that couldn't before, self-serve capability
2. "What interfaces consumed the headless engine? How were they different?"
   → Emphasize: multi-surface strategy, different UX needs served by same backend

### Competency Tags
- **Primary**: Platform Strategy, System Design Communication
- **Secondary**: Technical Product Leadership, Scalability

---

## S013 — Automated Complaint Resolution: -37% Negative Reviews

**Source**: Justdial, GPM
**Rounds**: Business ★★ | Product ★★ | Technical ★★

### STAR Skeleton
- **Situation**: high volume of complaints was damaging brand reputation and consuming customer support resources.
- **Task**: Build automated complaint resolution to reduce negative reviews and improve CSAT.
- **Action**: [Candidate to detail: NLP/automation approach, triage logic, resolution workflow design, human-in-the-loop decisions]
- **Result**: -37% negative reviews. +22 CSAT points.

### Earned Secret Prompt
"When should you automate customer support, and when does automation make things worse?"

### Follow-Up Trees

**Technical Round:**
1. "What was the automation architecture? How did you handle edge cases?"
   → Emphasize: NLP/classification approach, confidence thresholds, escalation triggers
2. "How did you ensure automated responses didn't make angry customers angrier?"
   → Emphasize: sentiment analysis, tone calibration, human-in-the-loop design

**Product Round:**
1. "How did you measure success beyond 'negative reviews reduced'?"
   → Emphasize: CSAT methodology, resolution time, repeat complaint rate
2. "What complaint types were automatable vs. required human intervention?"
   → Emphasize: classification taxonomy, the 80/20 of automation, cost-per-resolution analysis

**Business Round:**
1. "What was the cost savings from automation? How did it affect CS headcount?"
   → Emphasize: ROI, headcount reallocation, operational efficiency
2. "How did complaint reduction affect retention and LTV?"
   → Emphasize: downstream business impact, second-order effects

### Competency Tags
- **Primary**: Operations Strategy, AI/ML Product Thinking
- **Secondary**: Customer Experience, Process Automation

---

## S014 — Building PM Org from Scratch (6 PMs, 15+ XFN)

**Source**: Justdial, GPM
**Rounds**: Business ★★ | Product ★ | Technical ★

### STAR Skeleton
- **Situation**: Justdial needed a product management function built from scratch.
- **Task**: Hire, build, and lead a PM team of 6+ with 15+ cross-functional stakeholders.
- **Action**: [Candidate to detail: hiring philosophy, team structure, onboarding, OKR setting, performance management, culture building]
- **Result**: Functional PM org that delivered on business outcomes.

### Earned Secret Prompt
"What's the most important thing about building a PM org that PM hiring guides don't tell you?"

### Follow-Up Trees

**Business Round:**
1. "How did you design the team structure? What was your org philosophy?"
   → Emphasize: pod vs. functional structure, what you optimized for, what broke
2. "How did you set OKRs that actually drove behavior?"
   → Emphasize: OKR design anti-patterns you avoided, accountability mechanisms
3. "Tell me about someone you hired who didn't work out. What did you miss?"
   → Emphasize: hiring mistakes, what you learned, how you adjusted your process
4. "How did you handle performance management?"
   → Emphasize: feedback cadence, difficult conversations, growing people

### Competency Tags
- **Primary**: Team Building, People Management
- **Secondary**: Org Design, Hiring

---

## S015 — Side Project: Indian Music Diaries — WordPress to AWS

**Source**: Personal project
**Rounds**: Business ★ | Product ★ | Technical ★★★

### STAR Skeleton
- **Situation**: Personal music blog on WordPress with poor performance (PageSpeed <50).
- **Task**: Redesign and migrate to modern architecture on AWS.
- **Action**: [Candidate to detail: AWS architecture decisions, CDN setup, performance optimization, migration approach]
- **Result**: PageSpeed from <50 to >90. Modern scalable architecture.

### Earned Secret Prompt
"What drove you to do this outside of work, and what did you learn that you brought back to your day job?"

### Follow-Up Trees

**Technical Round:**
1. "Walk me through the AWS architecture. What services? Why?"
   → Emphasize: service selection rationale, cost optimization, scalability design
2. "How did you get PageSpeed from <50 to >90? What were the biggest wins?"
   → Emphasize: performance bottleneck diagnosis, optimization hierarchy, measurement
3. "What's your AWS cost? How did you optimize for a side project budget?"
   → Emphasize: cost-consciousness, right-sizing, serverless vs. traditional decisions

### Competency Tags
- **Primary**: Technical Depth, Hands-on Building
- **Secondary**: Performance Optimization, Cloud Architecture

---

## S016 — Appliance Repair Restructuring: 3x Professional Income

**Source**: Urban Company, Senior PM (2019-2020)
**Rounds**: Business ★★★ | Product ★★ | Technical ★

### STAR Skeleton
- **Situation**: Appliance repair category was using an aggregator model. Professionals were underpaid, quality was inconsistent.
- **Task**: Restructure from aggregator to individual professional model to improve quality and economics.
- **Action**: [Candidate to detail: economic modeling, supply-side restructuring, training programs, quality metrics, pricing changes]
- **Result**: 3x professional income. Improved service quality. More sustainable business model.

### Earned Secret Prompt
"When is the aggregator model wrong, and how do you know before it's too late?"

### Follow-Up Trees

**Business Round:**
1. "How did you model the economics of aggregator vs. individual model?"
   → Emphasize: unit economics comparison, margin analysis, supply-side economics
2. "How did tripling professional income affect the business P&L?"
   → Emphasize: cost absorption, pricing pass-through, volume effects
3. "What was the transition plan? How did you avoid supply disruption?"
   → Emphasize: change management, phased rollout, risk mitigation
4. "What happened to the aggregators? How did you manage that relationship?"
   → Emphasize: stakeholder management, difficult conversations, business ethics

**Product Round:**
1. "How did the product experience change for customers?"
   → Emphasize: quality improvement, consistency, trust signals
2. "How did you measure service quality in the new model?"
   → Emphasize: quality metrics, review systems, training effectiveness

### Competency Tags
- **Primary**: Business Model Innovation, Marketplace Strategy
- **Secondary**: Supply-Side Economics, Change Management

---

## Story Seed Coverage Analysis

### Competency Coverage Map

| Competency | Stories | Coverage |
|---|---|---|
| P&L Ownership | S001, S002, S007, S008 | ★★★ Strong |
| 0-to-1 Building | S001, S008, S010 | ★★★ Strong |
| AI/ML Product Thinking | S003, S006, S013 | ★★★ Strong |
| C-Suite Influence | S005, S007, S011 | ★★★ Strong |
| Marketplace Strategy | S006, S009, S016 | ★★★ Strong |
| Platform Strategy | S004, S012 | ★★ Moderate |
| Strategic Thinking | S005, S011 | ★★ Moderate |
| Team Building / People Management | S014 | ★ Single Story — needs reinforcement |
| GTM Execution | S001, S008 | ★★ Moderate |
| Technical Product Leadership | S003, S004, S012 | ★★★ Strong |
| Pricing Strategy | S002, S007 | ★★ Moderate |
| Failure / Learning | — | ⚠️ GAP — need to develop |
| Conflict / Difficult Stakeholder | S007 (partial) | ★ Weak — need dedicated story |
| Influence Without Authority (peer-level) | — | ⚠️ GAP — C-suite stories exist but peer influence is thin |
| Customer Empathy / User Research | S006, S009 | ★★ Moderate |

### Critical Gaps to Address
1. **Failure/Learning Story** — No explicit failure story exists. Must develop at least one genuine failure with real consequences and real learning.
2. **Peer-Level Influence Without Authority** — C-suite influence is well-covered (S005, S007, S011) but influencing peers/cross-functional teams without authority needs a dedicated story.
3. **Team Building Depth** — Only one story (S014). Consider developing a second story about a specific difficult management situation (firing, underperformance, team conflict).
