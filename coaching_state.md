# Coaching State — Piyush Deveshwar
Last updated: 2026-03-17

## Profile
- Target role(s): Senior PM, Group PM, Staff PM, Principal PM, Business Head, Startup Operator
- Seniority band: Senior to Director
- Track: Full System
- Feedback directness: 5
- Interview timeline: ~2026-03-24 (7 days, intensive — willing to work day and night)
- Time-aware coaching mode: Focused (compressed full system given 7-day intensity)
- Interview history: Active but not advancing — has been interviewing, never cleared an interview
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
- Story seeds: 16 pre-mapped in references/story-seeds.md (S001–S016). Top priority: S001 (JD Xperts P&L), S003 (LLM search), S005 (Lost Potential Bookings KPI), S007 (LTV → C-suite pricing), S011 (C-suite vertical marketplace pitch). Critical gaps: failure/learning story (none exists), peer influence without authority (thin), team management depth (only one story).

## Storybank
| ID | Title | Primary Skill | Secondary Skill | Earned Secret | Strength | Use Count | Last Used |
|----|-------|---------------|-----------------|---------------|----------|-----------|-----------|
| S001 | Zero-to-One P&L: JD Xperts to ₹4.8cr ARR | P&L Ownership / 0-to-1 Building | GTM Execution | seed only | TBD | 0 | — |
| S002 | 5.4x Unit Economics Transformation | Unit Economics / Financial Acumen | Pricing Strategy | seed only | TBD | 0 | — |
| S003 | Solving 11% Search Failure with LLM Engine | AI/ML Product Thinking / Technical PM | Cross-Functional Leadership | seed only | TBD | 0 | — |
| S004 | Foreseeing the Bottleneck: Shared OMS Architecture | Platform Strategy / System Design | Influence Without Authority | seed only | TBD | 0 | — |
| S005 | Inventing "Lost Potential Bookings" KPI | Strategic Thinking / C-Suite Influence | Data-Driven Decision Making | seed only | TBD | 0 | — |
| S006 | Cancellations 20% → 3% / NPS -12 → +28 | Problem Diagnosis / Marketplace Strategy | AI/ML Product Thinking | seed only | TBD | 0 | — |
| S007 | LTV Analysis → C-Suite Pricing Decision | C-Suite Influence / Pricing Strategy | Data-Driven Decision Making | seed only | TBD | 0 | — |
| S008 | Scaling AC Repairs to ₹1cr Revenue in 6 Months | 0-to-1 Building / GTM Execution | Marketplace Strategy | seed only | TBD | 0 | — |
| S009 | 19% QoQ Revenue: Mobile Merchant Strategy | Marketplace Strategy / User Research | Retention/Churn | seed only | TBD | 0 | — |
| S010 | Frugal MVP: Deals & Offers → 160K Daily Users | 0-to-1 Building / Product Sense | Frugal Innovation | seed only | TBD | 0 | — |
| S011 | Influencing C-Suite for Vertical Marketplace | C-Suite Influence / Strategic Thinking | Business Case Building | seed only | TBD | 0 | — |
| S012 | Headless Booking Engine: 48% Volume Growth | Platform Strategy / System Design | Technical Product Leadership | seed only | TBD | 0 | — |
| S013 | Automated Complaint Resolution: -37% Reviews | Operations Strategy / AI/ML | Customer Experience | seed only | TBD | 0 | — |
| S014 | Building PM Org from Scratch (6 PMs, 15+ XFN) | Team Building / People Management | Org Design | seed only | TBD | 0 | — |
| S015 | Indian Music Diaries: WordPress → AWS Migration | Technical Depth / Hands-on Building | Performance Optimization | seed only | TBD | 0 | — |
| S016 | Appliance Repair Restructure: 3x Professional Income | Business Model Innovation / Marketplace | Supply-Side Economics | seed only | TBD | 0 | — |

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
- Status: Screening round scheduled — 2 days out (~2026-03-20)
- Round formats:
  - Round 1: Behavioral screen, ~45min (format: recruiter or HM TBD). LP-focused. Format Discovery not yet run.
- Stories used in this loop: none yet
- Key JD competencies (priority order): (1) Technical Product Ownership / System Architecture for mobile growth stack, (2) Mobile Growth / AARRR, (3) Cross-functional stakeholder influence, (4) Emerging market customer insight, (5) Data-driven / experimentation
- Prep brief generated: 2026-03-18
- Next action: Finish S003, build S009 and S001 before screen. Prep "Why Amazon / Why this role" and Justdial gap narrative.

## Active Coaching Strategy
- Primary bottleneck: Technical depth credibility — confirmed by Amazon feedback ("fit for Senior PM, not Senior PM-T"). Business/product bars are being cleared.
- Current approach: (1) Build technical stories with real depth — S003, S004, S012, S015 need architecture-level detail. (2) Practice verbal system design / technical decision walkthroughs. (3) Build business/product storybank in parallel to stay sharp on what's already working.
- Rationale: He completed a full Amazon loop and nearly passed. He is not a weak interviewer. The gap is specific: technical peer-level conversations with SDMs and bar-raisers. Fix that one dimension and he clears.

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

## Session Log
| Date | Commands | Key Outcomes | Next Action |
|------|----------|--------------|-------------|
| 2026-03-17 | kickoff | Full system setup. Profile loaded. 16 story seeds pre-mapped. Diagnostic question asked: where exactly is candidate failing in interviews? | `stories` — STAR-structure top 5 priority stories |

## Coaching Notes
- 2026-03-17: Completed full Amazon loop. Rejected specifically for Senior PM-T (technical) — passed all business/product bars. Gap is technical depth credibility, not general interview performance. This is a targeted fix, not a full rebuild.
- 2026-03-17: Two Uber positions closed (internal hires/freezes) — not performance failures. He has been in the right rooms; he's not getting filtered out at screen stage when the resume lands.
- 2026-03-17: Explicitly concerned about stories, technical depth, systems understanding, and business frameworks/case study — suggests he's reaching rounds where these matter (not just being filtered at resume/screen stage).
- 2026-03-17: Willing to work day and night for 7 days. High motivation. Needs structure and ruthless prioritization.
- 2026-03-17: Feedback directness 4 (not 5) — direct but not brutal. Preserve self-reflection before critique in most cases.
- 2026-03-17: Jan 2026 departure from Justdial — currently ~2.5 months without a role. This "why did you leave" question will fire in every interview screen and needs a rehearsed answer immediately.
- 2026-03-17: Targeting Amazon (LP-heavy format), Uber (case study + operator-focused), and Indian tech startups (varied formats). Each requires different prep emphasis.
