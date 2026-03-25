# Coaching State — Piyush Deveshwar
Last updated: 2026-03-25

## Profile
- Target role(s): Senior PM, Group PM, Staff PM, Principal PM, Business Head, Startup Operator
- Seniority band: Senior to Director
- Track: Full System
- Feedback directness: 5
- Interview timeline: ~2026-03-24 (7 days, intensive — willing to work day and night)
- Time-aware coaching mode: Focused (compressed full system given 7-day intensity)
- Interview history: Passed Amazon EMXO screening round (2026-03-20). Full loop upcoming. Previous Amazon loop rejected for technical depth.
- Biggest concern: Strong work stories, technical depth, understanding systems, standard business frameworks/case study
- Known interview formats: [unknown — to be populated by Format Discovery Protocol during prep/mock]
- Anxiety profile: unknown — set by hype
- Career transition: none — has been PM/operator throughout career
- Transition narrative status: not started

## Resume Analysis
- Positioning strengths:
  1. AI-native marketplace PM with real 0-to-1 P&L delivery — JD Xperts from concept to ₹4.8cr ARR with 5.4x unit economics. Rare to have both AI credibility AND business-outcome proof at this scale.
  2. LLM product deployed at production scale — 11% search failure → 90K daily leads. Not theoretical AI work.
  3. C-suite influencer + org builder — built PM org from scratch, invented KPIs adopted org-wide, influenced exec investment decisions. Shows operating level well above IC.
- Likely interviewer concerns:
  1. Never cleared an interview — diagnostic question pending: where exactly is he failing (first rounds / finals / no-callbacks)?
  2. India-market company experience — Justdial and Urban Company are respected but India-only; Amazon/Uber will probe scope transferability
  3. "Was this really P&L ownership?" — ₹4.8cr ARR (~$580K) real but small by global standards; will be probed on decision authority vs. visibility
  4. Jan 2026 departure — 2+ months gap, needs crisp rehearsed narrative
  5. Technical depth credibility — claims Python, LangChain, LlamaIndex, AWS; will be probed at Amazon/Uber
  6. Urban Company "Senior Manager Growth" — ambiguous title, could read as BizOps/growth-ops rather than PM; needs clear framing
- Career narrative gaps:
  - Why did he leave Justdial? (unexplained on resume — will be asked in every screen)
  - Urban Company "Senior Manager Growth" → GPM at Justdial: was this product-led or ops-led? Needs crisp bridge narrative.
- Story seeds: 22 full STAR stories in amazon-lp-stories-cheatsheet.md (S001, S003-S013, S015, S017-S026). All 16 Amazon LPs covered with 3+ stories each. S002 merged into S001. S014/S016 deprioritized. 6 new stories (S021-S026) add technical debugging depth for PM-T bar.

## Storybank
| ID | Title | Primary Skill | Strength | Status |
|----|-------|---------------|----------|--------|
| S001 | Zero-to-One P&L: JD Xperts ₹4.8cr ARR (merged S002) | P&L Ownership | 4.5/5 | Full STAR + 4 layers |
| S003 | LLM Search Engine: 11%→2% failure | AI/ML Technical PM | 4.5/5 | Full STAR + 4 layers |
| S004 | Shared OMS: 3mo→3wk launches | Platform Strategy | 4/5 | Full STAR + 4 layers |
| S005 | Lost Potential Bookings KPI | Strategic Thinking | 4/5 | Full STAR + 4 layers |
| S006 | Cancellations 20%→3%, NPS turnaround | Problem Diagnosis | 4/5 | Full STAR + 4 layers |
| S007 | LTV → Delayed Launch for Trust | C-Suite Influence | 4.5/5 | Full STAR + 4 layers |
| S008 | AC Repairs: ₹1cr, 190K users | GTM Execution | 4/5 | Full STAR + 4 layers |
| S009 | Self-Serve Vendor Platform: ₹13cr | Marketplace Strategy | 4.5/5 | Full STAR + 4 layers |
| S010 | Frugal MVP Deals: 18K users/day | Frugal Innovation | 4/5 | Full STAR + 4 layers |
| S011 | Vertical Marketplace Vision | Strategic Thinking | 3.5/5 | Full STAR + 4 layers |
| S012 | Headless Booking Engine: 48% growth | System Design | 4.5/5 | Full STAR + 4 layers |
| S013 | CRM-Lite: -37% neg reviews | Frugal Innovation | 4/5 | Full STAR + 4 layers |
| S015 | Indian Music Diaries: 100K users | Technical Depth | 3.5/5 | Full STAR + 4 layers |
| S017 | Category Exploration: +59% leads | Product Discovery | 4/5 | Full STAR + 4 layers |
| S018 | Segmentation PMF: 4 segments | Customer Research | 4/5 | Full STAR + 4 layers |
| S019 | FAILURE: Phone Connect Rate | Intellectual Humility | 4/5 | Full STAR + 4 layers |
| S020 | Lead Salvaging AI: ₹15cr rescued | AI/ML Business Impact | 4.5/5 | Full STAR + 4 layers |
| S021 | Login Pop-up Debug (Marketing Conflict) | Technical Debugging | 3.5/5 | Full STAR + 4 layers |
| S022 | Merchant Metrics A/B Test | Data-Driven Prevention | 4/5 | Full STAR + 4 layers |
| S023 | Day Pass: 4G Performance Debug | Mobile Performance | 4/5 | Full STAR + 4 layers |
| S024 | OTP Failure → Notification Gateway | Platform Reliability | 4.5/5 | Full STAR + 4 layers |
| S025 | ML Lead Ranking (XGBoost) | ML/Data Science | 4/5 | Full STAR + 4 layers |
| S026 | Banner Targeting Bug (Silent) | Marketing Systems | 4.5/5 | Full STAR + 4 layers |
| S014 | Building PM Org (deprioritized — IC role) | Team Building | TBD | Seed |

### Story Details

---

#### S003 — Solving 11% Search Failure with LLM Engine
- Primary Skill: AI/ML Product Thinking / Technical PM
- Secondary Skill: Cross-Functional Leadership
- Strength: 4.5/5
- Round Type: Business ★★ | Product ★★★ | Technical ★★★
- Follow-up Readiness: High
- Deploy for: Technical depth, Invent & Simplify LP, "walk me through a technical architecture decision"
- Version history: 2026-03-18 — first full version

**Situation**
Justdial processed millions of searches daily, but 11% were failing — defined as either returning no results, or returning results the user didn't click on followed by a repeat search. At our scale that was ~80,000 dead searches daily, all from high-intent users. Failures clustered into four buckets: misspellings, colloquial/local language spellings, free-text natural language queries, and Hindi/Hinglish code-switched text.

**Task**
Fix search failure rate. I owned the end-to-end solution and led a cross-functional team of 8 across product, engineering, and data.

**Action**
We already had a rules-based spelling correction dictionary. It handled simple misspellings but Hinglish queries and free-text searches kept falling through. I evaluated three options:
1. Expand the rules-based dictionary — rejected. You can't enumerate all Hinglish variants or anticipate free-text phrasing. It would always be chasing the tail.
2. Google Vertex API — fast to market, strong quality, but the per-query cost at 80K+ daily failing searches made unit economics unworkable.
3. Fine-tune an in-house model — higher upfront investment, but full cost and quality control.

I chose option 3, but staged it. We had an existing internal LLM entity extraction service built for phone call audio transcripts — it parsed intent from unstructured spoken text. I proposed repurposing and scaling this as an independent search service rather than building from scratch.

The architecture we built: A user submitting a failing query would receive a "Did you mean ___?" prompt via text or WhatsApp. This served two functions simultaneously — it helped the user immediately, and the response became a ranked feedback signal we used to update corrections in our Elasticsearch layer. Under the hood, a LangChain semantic matching pipeline parsed intent from raw queries — handling Hinglish, misspellings, and free-text.

The core engineering challenge was latency. We couldn't process synchronously and respond in real time — so instead of forcing real-time, we built an async message queue with a pool of worker nodes. Queries were passed to the intent parsing service asynchronously, corrections delivered via SMS/WhatsApp.

Unit economics evolved in three stages: external LLM provider APIs first (fast, expensive) → cheaper smaller hosted model → fully in-house fine-tuned model. Moving in-house also fixed our Hinglish quality issues because the general models handled code-switching poorly — fine-tuning on our own query corpus was the only way to get quality right.

Before live rollout, we ran the service on the previous week's failed queries in batch, manually QA'd outputs, and used that to seed initial ranking weights. Rollout was batched: small app traffic percentage first, then two cities.

**Result**
Search failure rate dropped from 11% to ~2% — rescuing ~65,000 searches daily. Generated ~90,000 high-intent leads daily from previously dead traffic. ~50,000 unique users captured from previously failed searches.

**Earned Secret**
"Most teams treat their LLM cost problem as a procurement problem — negotiate better API rates. We treated the model as a product we owned. Moving in-house gave us cost control and quality control simultaneously — the general models handled Hinglish badly because they'd never been trained on the specific code-switching patterns of India's local search queries. You can't buy your way to that. You have to build it."

---

#### S009 — Self-Serve Vendor Platform: ₹13cr Revenue Unlock
- Primary Skill: Marketplace Strategy / User Research
- Secondary Skill: Retention/Growth
- Strength: 3.5/5 (needs S001-style absolute metrics and timeline detail)
- Round Type: Business ★★★ | Product ★★★ | Technical ★
- Follow-up Readiness: Medium
- Deploy for: Mobile growth, self-serve marketplace, user segmentation insight, "Deliver Results" LP, Amazon EMXO domain match
- Version history: 2026-03-18 — first full version. Corrected from "19% QoQ" framing (single-quarter result, tapered) to structural ₹13cr unlock framing.

**Situation**
Justdial's apps had slightly lower engagement than web platforms. This was common knowledge internally but had never been worked as a problem statement. The org optimized for "users" as one undifferentiated segment. Meanwhile, all vendor advertising was sold through an offline sales team or direct sales. Product-driven advertising was 0.5% of total — approximately ₹1.5cr on a ~₹65cr app advertising base.

**Task**
Improve mobile monetization and unlock new revenue from the vendor segment.

**Action**
Reviewing engagement metrics, I noticed app and web engagement diverged in a way that didn't match the narrative. I went deeper: cohort analysis, behavioral segmentation, booking patterns. Found that 45-50% of app users were actually businesses — vendors tracking leads, responding to customers, managing their presence. Known anecdotally in the org. Never treated as a product opportunity.

This reframed the problem: not "why is app engagement lower?" but "why are we serving two completely different user types with one product?"

Built a set of self-serve capabilities for business users:
- On the search results page, vendors saw contextual prompts: "You can buy this position" with direct purchase flow
- Self-serve purchase of banners, trust badges, verified badges, sponsored positions — no sales call required
- Entry points throughout the app for vendors to manage and grow their presence
- Vendor marketplace for business services (being scaled further)

The structural insight was about long-tail categories. Justdial had chronically under-served them: sales-team cost-of-sale exceeded revenue per long-tail category, so sales teams skipped them. Digital self-serve removed this cost-of-sale barrier entirely. We actively drove traffic to long-tail categories, created advertising inventory that now had buyers, and unlocked revenue that structurally couldn't exist under a sales-led model.

**Result**
Grew app advertising revenue from ~₹65cr to ~₹78cr — a ₹13cr incremental unlock. Primary driver: long-tail categories that were previously unprofitable under a sales-led model. Platform infrastructure built is the foundation for ongoing scaling — the structural change is permanent even as initial low-hanging fruit was captured.

**Earned Secret**
"The insight wasn't new to the org — old hands knew half the app users were businesses. What was new was treating it as a product problem rather than a sales problem. When you remove the sales team as the intermediary, two things happen: cost-of-sale collapses, and the long tail becomes economically viable for the first time. That's not a growth hack — that's a structural shift in how the marketplace makes money. Amazon EMXO is building exactly this: self-serve capability for emerging market vendors who'd otherwise need a sales team to monetize."

#### S001 — Zero-to-One P&L: JD Xperts to ₹4.8cr ARR
- Primary Skill: P&L Ownership / 0-to-1 Building
- Secondary Skill: GTM Execution, Marketplace Strategy
- Strength: 4.5/5
- Round Type: Business ★★★ | Product ★★ | Technical ★
- Follow-up Readiness: High
- Deploy for: P&L ownership, 0-to-1 building, "Ownership" LP, "Deliver Results" LP, "Tell me about a time you built something from scratch"
- Version history: 2026-03-19 — first full version (rebuilt from lost session)

**Situation**
In 2020, Justdial's advertising revenues dropped suddenly. Leadership wanted to diversify beyond ad tech into extensions of their business that were similar and more direct to execute. They invested in service-based verticals. JD Xperts was a home services vertical — users had a clear use case: finding high-quality, trusted, verified vendors for home services. For the business, this meant diversifying revenues away from ad tech. For high-quality, high-agency vendors, this acted as a better marketing spend than traditional advertising.

**Task**
I was the first hire. I negotiated my role from a business lead to a product + business lead. I hired engineers, product managers, and operators for all other roles. I reported to the CPO. For the first phase — when we needed to prove the model, bring traffic, and serve users — we were part of the same org with no separate funding. I had to prove the model before earning dedicated investment.

**Action**
Three core decisions drove the outcome:

1. **Model shift: handshake → completion.** In the traditional business, vendors bought listing positions on local search results pages or ad banners. When a user enquired, Justdial connected them to multiple vendors — some paid, some not. Revenue came from the connection event (~₹50/connection). In the new model, we charged the vendor a percentage commission on their billing. Since vendors didn't have to compete in this model and had more assured returns, they were happy to participate. With average ticket sizes of ₹1,100–1,200 per order, we achieved a blended revenue of ₹270 per order — 5.4x the legacy model.

2. **Matchmaking algorithm — quality foundation.** The commission-on-completion model only works if matches are good. We built a matchmaking algorithm that cut cancellations from 20% to 3% and flipped NPS from -12 to +28. This was the quality foundation the commission model required — every bad match, every cancellation was now our economic problem too.

3. **Shared OMS — scaling infrastructure.** I foresaw that each new category would need ~3 months to build standalone order management. Built abstracted, shared OMS infrastructure: new verticals could launch in 3 weeks instead of 3 months. This enabled 4 new business lines without proportional engineering investment.

**Result**
₹4.8cr ARR (~$580K) over ~2.5 years. 5.4x unit economics (₹270/order vs. ₹50 legacy). Proved the model to the exec team. OMS enabled 4 verticals at dramatically reduced launch time.

**Earned Secret**
"When you flip to commission-on-completion, every bad match, every cancellation, every poor NPS score becomes your problem economically. That alignment is what makes the product better. We didn't just build a new revenue line — we built a fundamentally different relationship between platform quality and platform revenue."

---

## Score History
### Historical Summary
[Empty]

### Recent Scores
| Date | Type | Context | Sub | Str | Rel | Cred | Diff | Hire Signal | Self-Δ |
|------|------|---------|-----|-----|-----|------|------|-------------|--------|

## Outcome Log
| Date | Company | Role | Round | Result | Notes |
|------|---------|------|-------|--------|-------|
| ~2025 | Amazon | Senior PM-T | Full loop | Rejected | Completed full loop. Feedback: "fit for Senior PM but not Senior PM-T." Cleared business/product bars. Failed specifically on technical depth bar. |
| 2026-03-20 | Amazon | Sr. PM Mobile Growth EMXO | Screening | Passed | Passed screening round. Full loop upcoming. HM shared: marketing team, Meta/Google for app downloads, data sharing constraint. |
| ~2025 | Uber | Senior PM | Round 1 | Closed | Position closed, internal hire. Not a performance signal. |
| ~2024 | Uber | Senior PM | Round 1 | Closed | Position closed. Not a performance signal. |

## Interview Intelligence

### Question Bank
| Date | Company | Role | Round Type | Question | Competency | Score | Outcome |

### Effective Patterns (what works for this candidate)
[Empty — to be populated by analyze/debrief]

### Ineffective Patterns (what keeps not working)
[Empty — to be populated. Key hypothesis: stories lack STAR structure and specificity when delivered live. To be confirmed via first practice session.]

### Recruiter/Interviewer Feedback
| Date | Company | Source | Feedback | Linked Dimension |

### Company Patterns (learned from real experience)
[Empty — to be populated by analyze/debrief. Target companies: Amazon, Uber, Indian tech startups]

### Historical Intelligence Summary
[Empty]

## Drill Progression
- Current stage: 1
- Gates passed: []
- Revisit queue: []

## Interview Loops (active)

### Amazon — Sr. Product Manager - Mobile Growth, EMXO PLX
- Job ID: 3182350 | Location: Bengaluru, IND, KA
- Team: Emerging Marketplaces Cross Org (EMXO), Prime/Lifecycle/XCM — covers 10 emerging countries (India, Brazil, Mexico, AU, SG, UAE, Egypt, SA, Turkey, South Africa)
- Category: Product Management — Technical (T-bar applies)
- **Status: PASSED SCREENING (2026-03-20). Full loop upcoming (5 rounds).**
- Role context from HM: Marketing team works with Meta, Google for app downloads in emerging markets. Key constraint: cannot share data with these third-party companies (rival tech giants). Working with very little data is the core challenge.
- Round formats (assumed standard Amazon 5-round loop):
  - Round 1: LP/Behavioral — S001, S009, S006 (backup: S005)
  - Round 2: LP/Behavioral — S007, S022, S011 (backup: S017)
  - Round 3: Technical — S003, S024, S012 (backup: S004)
  - Round 4: Product Sense — S018, S026, S025 (backup: S021)
  - Round 5: Bar Raiser — S019, S008, S023 (backup: S010, S015)
- Stories available: 22 full STAR with Technical Architecture + LP Flex + EMXO Connection + Quick Revision Anchors
- Key JD competencies (priority order): (1) Technical Product Ownership / System Architecture for mobile growth stack, (2) Mobile Growth / AARRR, (3) Cross-functional stakeholder influence, (4) Emerging market customer insight, (5) Data-driven / experimentation, (6) Working with limited data from third parties
- Prep brief generated: 2026-03-18 | Stories enhanced: 2026-03-25
- Next action: Practice delivering stories out loud, focusing on "What I Actually Built" sections. Run LP drills using Quick Revision Anchors. Do mock interviews per round type.

## Active Coaching Strategy
- Primary bottleneck: Technical depth credibility — confirmed by Amazon feedback ("fit for Senior PM, not Senior PM-T"). Business/product bars are being cleared.
- Current approach: (1) ALL 22 stories now have "What I Actually Built" technical architecture sections. (2) 6 new stories (S021-S026) are specifically technical debugging stories — exactly what PM-T bar requires. (3) Every story has LP Flex notes, EMXO role framing, and Quick Revision Anchors for rapid study. (4) Round allocation maps 15 stories to 5 rounds with no repeats.
- Rationale: He completed a full Amazon loop and nearly passed. The gap was technical depth. Now every story answers "what did you actually build?" with specific systems, tech stacks, architecture patterns, and trade-off decisions. The 6 new debugging stories (login bugs, 4G performance, notification systems, marketing targeting pipelines, ML lead ranking) give him a rich arsenal of technical depth stories that directly align with the EMXO marketing technology role.
- Next phase: Delivery practice. Stories are built — need verbal practice, especially "What I Actually Built" sections and LP pivoting.

## Calibration State
- Calibration Status: uncalibrated
- Last calibration check: never
- Data points available: 0

## LinkedIn Analysis
[Empty — run `linkedin` to populate. LinkedIn: https://www.linkedin.com/in/piyushdeveshwar]

## Resume Optimization
[Empty — run `resume` to populate]

## Positioning Statement
[Empty — run `pitch` to populate]

## Outreach Strategy
[Empty — run `outreach` to populate]

## Comp Strategy
[Empty — run `salary` to populate]

## Standing Narratives

### Why I Left Justdial (30–45 seconds)
"I'd been at Justdial for nearly 5 years — built JD Xperts from zero, then led the mobile product org. By late 2025 I'd accomplished what I came to do: proved the new business model, scaled the LLM search engine, built the PM org. Two things converged: a leadership transition was underway, and the role I wanted next — something more technically forward, closer to the AI and platform frontier — wasn't going to be created there. I decided this was the right moment to deliberately invest in being closer to where technology is moving. That's what has me here talking to Amazon."

### Why Amazon / Why This Role (60–90 seconds)
"The EMXO charter maps almost exactly to the problems I've been working on — mobile-first users, emerging market dynamics, self-serve vendor growth, long-tail monetization. At Justdial, I discovered that nearly half our app users were actually businesses. When we built self-serve monetization flows for them — removing the sales team as the intermediary — we unlocked ₹13cr in revenue in categories that were structurally unprofitable under a sales-led model. The insight was the same one Amazon is building on: in emerging markets, you can't scale a sales team to match the long tail. You need product-led self-serve. The EMXO mission is to make Amazon work for merchants and customers across 10 markets where the friction looks very different than North America. I've lived that friction — building products where Hinglish queries break your search engine, where trust signals matter more than price, where mobile is the only screen. That's not context I'd need to learn here. I'd be walking in with it."

### Tell Me About Yourself (2-minute opener, calibrated for EMXO)
"I'm Piyush — I've spent the last 6+ years building marketplace products in India, most recently as GPM at Justdial where I led a team of 6 PMs and 15+ cross-functional members.

Three things define my work: First, I've built from zero. I took JD Xperts — a home services vertical — from concept to ₹4.8cr ARR with 5.4x unit economics. I was the first hire, built the team, proved the business model. Second, I've shipped AI at production scale. Our LLM-powered search engine cut search failures from 11% to 2%, rescuing 65,000 searches daily — handling Hinglish, misspellings, and free-text queries that rules-based systems couldn't touch. Third, I understand the emerging market merchant. I discovered that nearly half our app users were actually businesses, built self-serve monetization for them, and unlocked ₹13cr in revenue from categories that were structurally unprofitable under a sales-led model.

That last insight — that in emerging markets, you need product-led self-serve because you can't scale a sales team to match the long tail — is exactly what EMXO is building. I've lived the friction this role is designed to solve: mobile-only users, trust-driven purchase decisions, multilingual search, and vendors who need simple self-serve tools to grow. That's the context I'd bring on day one."

## Session Log
| Date | Commands | Key Outcomes | Next Action |
|------|----------|--------------|-------------|
| 2026-03-17 | kickoff | Full system setup. Profile loaded. 16 story seeds pre-mapped. Diagnostic question asked: where exactly is candidate failing in interviews? | `stories` — STAR-structure top 5 priority stories |
| 2026-03-18 | stories | Built S003 (LLM Search) and S009 (Self-Serve Vendor Platform) full STAR stories. Fixed S003 metric (2%→3%). | Build S001, prep narratives |
| 2026-03-19 | stories, narratives | Rebuilt S001 (JD Xperts P&L) full STAR. Added "Why I Left Justdial", "Why Amazon", and 2-min opener. Created LP revision cheatsheet. | Practice delivery out loud. LP drills. |

## Coaching Notes
- 2026-03-17: Completed full Amazon loop. Rejected specifically for Senior PM-T (technical) — passed all business/product bars. Gap is technical depth credibility, not general interview performance. This is a targeted fix, not a full rebuild.
- 2026-03-17: Two Uber positions closed (internal hires/freezes) — not performance failures. He has been in the right rooms; he's not getting filtered out at screen stage when the resume lands.
- 2026-03-17: Explicitly concerned about stories, technical depth, systems understanding, and business frameworks/case study — suggests he's reaching rounds where these matter (not just being filtered at resume/screen stage).
- 2026-03-17: Willing to work day and night for 7 days. High motivation. Needs structure and ruthless prioritization.
- 2026-03-17: Feedback directness 4 (not 5) — direct but not brutal. Preserve self-reflection before critique in most cases.
- 2026-03-17: Jan 2026 departure from Justdial — currently ~2.5 months without a role. This "why did you leave" question will fire in every interview screen and needs a rehearsed answer immediately.
- 2026-03-17: Targeting Amazon (LP-heavy format), Uber (case study + operator-focused), and Indian tech startups (varied formats). Each requires different prep emphasis.
