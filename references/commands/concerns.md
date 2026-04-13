# concerns — Concern Anticipation Workflow

### Sequence

1. Ask candidate what concerns they expect.
2. Validate correct concerns.
3. **Generate concerns from real data** — don't work in a vacuum. Pull from:
   - Resume analysis (career gaps, short tenures, domain switches, seniority mismatches — from kickoff)
   - Storybank gaps (competencies with no strong story)
   - Previous analyze results (patterns and weak dimensions)
   - The specific role/company (does the JD require something the candidate lacks?)
   - Career narrative gaps (transitions that need explaining)
   - **Default Candidate Context** (from SKILL.md) for pre-identified likely concerns
   - **Outcome Log** (if real interview outcomes exist): Use past rejections as counter-evidence for current concerns. If the candidate was previously rejected for "not enough leadership experience" but has since advanced at two other companies on leadership questions, that outcome data weakens this concern. Conversely, if the same concern has driven 2+ rejections, it's confirmed — escalate its severity.
4. Add any concerns the candidate missed.

**PM/BizOps-Specific Concern Templates:**

Prioritize these concerns when coaching for PM, Business Operator, Strategy, and GM roles:

| Concern Category | Typical Trigger | Counter Strategy |
|---|---|---|
| **"Was this really P&L ownership?"** | Resume says "P&L owner" but interviewers suspect it was visibility, not authority | Be specific about decisions YOU made: pricing, headcount, budget allocation, kill decisions. Name what you could do without approval vs. what needed sign-off. |
| **Marketplace experience transferability** | Heavy marketplace background, targeting non-marketplace role | Reframe marketplace skills as universal: supply-demand balancing = resource allocation, network effects = growth thinking, liquidity = market-making. Pull from specific transferable stories. |
| **Technical credibility as a PM** | No engineering background, targeting technical PM or AI/ML PM role | Lead with technical product decisions you made (build vs. buy, architecture trade-offs, model selection). Show you can communicate with engineers as equals without claiming to BE an engineer. |
| **India market experience relevance** | All experience in India, targeting global or US-market roles | Focus on problem complexity, scale, and decision frameworks — not geography. "I scaled a marketplace to X users in a market with Y unique constraints" is universally impressive. |
| **Multiple transitions narrative** | 3+ companies in 5 years, or frequent moves | Each move needs a 1-sentence intentional narrative. "I went to UC for marketplace scale, then to JD for P&L ownership, then to [next] for [reason]." The through-line must be clear. |
| **Domain breadth vs. depth** | Experience across many domains (marketplace, consumer, B2B) | Frame as pattern recognition: "I've seen what works across marketplace, consumer, and B2B contexts — and I can tell you what transfers and what doesn't." |
| **C-suite influence vs. execution** | Heavy on strategy/influence stories, interviewer worried about execution chops | Balance every strategy story with execution detail: timelines, sprint mechanics, how you unblocked teams, what you shipped. |
| **Team size / org scale** | Led 6 PMs, interviewer wonders about readiness for 20+ | Show org design thinking, hiring philosophy, management systems you built — not just headcount. "I designed the team for X, and here's what I'd change at 3x the scale." |

5. **Rank by severity**: Not all concerns are equal. Assign each one:
   - **Dealbreaker**: This could single-handedly end the candidacy if not addressed well (e.g., missing a core required skill, a very short recent tenure that looks like termination)
   - **Significant**: Will come up and needs a strong counter, but won't kill the candidacy alone (e.g., no direct industry experience, a slightly junior background)
   - **Minor**: Might come up as a probe but unlikely to be decisive (e.g., a 2-year-old role change, a less prestigious school)
6. Attach counter strategies — **with multiple framings** for each significant+ concern:
   - **The direct question**: How to answer "Why did you leave after 8 months?" head-on
   - **The subtle probe**: How to handle "Tell me about a time things didn't work out" when they're really asking about the short tenure
   - **The follow-up challenge**: How to handle "But wouldn't that be a risk in this role too?" after your initial counter

#### Scripting Difficult Moments

Executive coach Alisa Cohn (top 50 coaches in the world per Thinkers50, via Lenny's Podcast) emphasizes that the key to handling difficult interview moments is preparation — not just knowing the strategy but wrapping your mouth around the actual words beforehand. Her framework for difficult conversations:
1. **Identify what's uncomfortable** — what meaning are you adding on top of the facts?
2. **Get your mindset right** — you're addressing this to help them understand, not to apologize or defend
3. **Prepare a script** — practice the exact words, not just the concept
4. **Prepare for the reaction** — know how you'll respond if the interviewer pushes back or looks skeptical

For the most common difficult interview moments:
- **Explaining a gap or firing**: Lead with what you learned, not the circumstances. Use Cohn's structure: observable fact + forward momentum. "I left [Company] because [brief honest reason]. What I took from that experience was [specific lesson], which directly shaped how I approach [relevant skill] now."
- **Addressing a short tenure**: Don't over-explain or get defensive. If the interviewer probes, use Cohn's pause technique — recognize the temperature change, acknowledge it, and redirect: "I understand that looks unusual on paper. Here's what actually happened, and here's what I learned."
- **When you freeze or get flustered**: As Cohn notes, "the importance is not even what you say, but that you have prepared and are prepared for if someone has that kind of reaction and that you don't have to, yourself, react to it." Preparation neutralizes the freeze response.

### Output Schema

```markdown
## Likely Interviewer Concerns (ranked by severity)

### Dealbreakers
1. Concern:
   Severity: Dealbreaker
   Source: [resume / storybank gap / JD mismatch / etc.]
   Counter (direct question): [how to answer if asked head-on]
   Counter (subtle probe): [how to address if it comes up indirectly]
   Counter (follow-up challenge): [how to handle pushback on your counter]
   Best story:

### Significant
2. Concern:
   Severity: Significant
   Source:
   Counter (direct question):
   Counter (subtle probe):
   Counter (follow-up challenge):
   Best story:

### Minor
3. Concern:
   Severity: Minor
   Source:
   Counter (one-liner):

**Recommended next**: `practice pushback` — drill your top concern under pressure. **Alternatives**: `prep [company]`, `mock [format]`
```

### Immediate Practice Option

After generating concerns, offer to drill the top concern right now:
"Your biggest concern is [X]. Want to practice handling it? I'll throw the direct question, then the subtle probe version, and we'll see how you do."

If they accept, run a mini pushback drill (2-3 rounds) focused on the top 1-2 concerns:
- Round 1: Direct question version
- Round 2: Subtle probe version
- Round 3: Follow-up challenge after their counter
Score each round and add to Score History in `coaching_state.md` (Type: practice). Update Session Log with the concern-focused drill.

### Concern Tracking

After generating, save the ranked concerns to `coaching_state.md` (in the Interview Loops section under the relevant company's Concerns surfaced field, or in Active Coaching Strategy if general). This allows:
- `prep` to pull from previously generated concerns instead of re-deriving them
- `hype` to reference the top concern + counter in the 3x3
- `progress` to track whether concerns are being addressed over time
- `mock` to include questions targeting known concerns
