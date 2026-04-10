# eBay Interview Prep — Product Manager, Product Knowledge
## Piyush Deveshwar | R1 + R2 | Tomorrow

> **Role in one line:** Own the AI-powered product knowledge system that makes eBay's 2 billion listings discoverable — taxonomy, ontology, knowledge graphs, LLM-based classification and enrichment.

---

## THE JOB IN PLAIN ENGLISH

eBay has a fundamental data quality problem. Unlike Amazon where brands control catalog data, eBay has ~2 billion listings created by individual sellers who write inconsistent, incomplete, unstructured descriptions. Bad data = broken discovery = lost GMV.

This PM owns the infrastructure that fixes that: structured taxonomy, attribute extraction, ML classification, entity resolution — all powered by AI. Every search result, every filter, every recommendation depends on product knowledge being accurate.

**Why this is hard:** You can't ask 135 million sellers to re-list their items. You have to infer structure from chaos, at scale, cheaply, without hallucinating.

---

## YOUR BACKGROUND FIT (USE THIS TO ANCHOR EVERY ANSWER)

| eBay needs | Your story | How it maps |
|-----------|-----------|------------|
| LLM-powered classification | S003 — Two-tier embedding+LLM pipeline for 93K failed searches | You literally built a classification system using the same architecture: embedding for high-confidence, LLM for <0.7 cases |
| Taxonomy + ontology | S003 + S006 — 5K-category pgvector catalog, Root→Branch→Leaf skill tree | You built and operated hierarchical taxonomies with embedding-based matching |
| Attribute extraction (NER) | S020 — spaCy NER extracting service_type, brand, location from call audio | Same problem: unstructured text → structured attributes |
| Cost-efficient LLM at scale | S020 — Three-level tiered processing, model distillation, 40% cost increase for 375% volume | Directly applicable to LLM classification at 2B listing scale |
| Entity resolution | S003 — "AC thik karo" → "Air Conditioner Repair Service" via semantic match | Same as matching "iphone 14 pro max 256 blk" → canonical eBay catalog entity |
| Metrics for search/discovery | S003/S005 — CTR, conversion, precision/recall, LPB | You've built and tracked exactly these metrics |

**Key narrative to weave in:** "I've actually built a smaller version of this exact system. The architecture challenges — when to use embedding vs. LLM, how to handle ambiguity, cost vs. accuracy trade-offs at scale — are the same ones eBay faces at 100x the volume."

---

## SECTION 1: EBAY PRODUCT KNOWLEDGE CONTEXT

### What "Product Knowledge" means at eBay

**Taxonomy:** The category tree that every listing belongs to. Example: Electronics > Phones & Accessories > Cell Phones & Smartphones > Apple. eBay has hundreds of thousands of leaf categories.

**Item Specifics / Attributes:** Structured fields within a category. For iPhones: Brand, Model, Storage Capacity, Color, Condition, Network. These power filters and faceted search.

**Ontology:** The relationships between concepts. "iPhone 14 Pro Max" IS-A "Smartphone" MADE-BY "Apple" SUCCESSOR-OF "iPhone 13 Pro Max." Ontologies enable reasoning, not just matching.

**Knowledge Graph:** A web of connected entities. Product knowledge graphs connect: item → brand → category → compatible items → successor/predecessor items → frequently co-purchased items.

**Entity Resolution:** Recognizing that "Apple iPhone 14 Pro Max 256GB Space Gray Unlocked," "iPhone 14 Pro Max - 256 - Space Gray" and "iphone 14 pro 256gb gry" are the same product. Critical for eBay because sellers each describe the same product differently.

### eBay's Specific Challenges vs. Amazon
| Dimension | Amazon | eBay |
|-----------|--------|------|
| Catalog ownership | Brand-controlled (Brand Registry) | Seller-controlled (anyone can list) |
| Data quality | High, standardized | Highly variable, often poor |
| Product type | New, brand-name goods primarily | New, used, refurbished, vintage, one-of-a-kind |
| Entity resolution | Easier (known brands, SKUs) | Harder (handmade items, unique collectibles) |
| Seller incentive to add data | High (Amazon pushes it) | Low (sellers list fast, move on) |

**eBay's moat opportunity:** Be the best at unstructured → structured at scale. If eBay can accurately classify and enrich listings that sellers don't fully describe, they win discovery without depending on seller behavior change.

---

## SECTION 2: LLM UNDERSTANDING (TAILORED TO THIS ROLE)

### How LLMs apply to Product Knowledge (know these cold)

**1. Automated Classification**
Input: listing title + description → Output: category path
- Challenge: ambiguous listings ("Sony 16-70mm f/4" → Camera Lens OR Camcorder Lens?)
- Your architecture: embedding model for high-confidence (>0.7 similarity to known category), LLM only for ambiguous cases
- Cost reality: LLM per call costs matter at 2B listings. Same three-tier approach you built for S020.

**2. Attribute Extraction (Structured Enrichment)**
Input: "Vintage 1965 Fender Stratocaster sunburst finish, all original, plays perfectly" → Output: `{brand: Fender, model: Stratocaster, year: 1965, color: Sunburst, condition: Good, era: Vintage}`
- This is NER at eBay scale. Your S020 NER pipeline is exactly this.
- Challenge: domain-specific vocabulary per category (guitar specs ≠ phone specs ≠ sneaker specs)
- Solution: category-specific entity schemas + fine-tuned NER per vertical

**3. Entity Resolution**
Input: many listings → Output: clusters of listings that represent the same real-world product
- LLMs help with fuzzy matching + context understanding
- Embedding similarity to find candidates, LLM to confirm/reject matches
- Your pgvector + two-tier approach directly applies

**4. Taxonomy Evolution**
LLMs can suggest new leaf categories when they detect clusters of listings that don't fit existing taxonomy well. Think Big use case — the taxonomy becomes self-improving.

**5. Title/Description Quality Improvement**
Given a weak listing title, LLM suggests a better one. Seller-facing tool. Increases item specifics fill rate without requiring seller effort.

### Key LLM trade-offs to discuss fluently

| Challenge | How to handle it |
|-----------|-----------------|
| Hallucination in attributes | Confidence thresholds + taxonomy whitelist (only return attributes that exist in category schema) |
| Cost at 2B listing scale | Two-tier: embedding for common, LLM for ambiguous (same as your S003 architecture) |
| Latency on new listing ingestion | Async enrichment — list immediately, enrich within 5 min in background |
| Ground truth for evaluation | Human-labeled sample per category + precision/recall by category |
| Domain vocabulary gaps | Fine-tune on eBay-specific listing corpus; RAG against category-specific attribute dictionaries |

---

## SECTION 3: PRODUCT SENSE QUESTION BANK

*These will come in the form of: "How would you improve X?" or "Design a product for Y."*

### Likely Question 1: "How would you improve eBay's product listing quality?"

**Framework to use:** Problem → User → Solution → Metrics → Trade-offs

**Your answer structure:**
1. **Clarify scope:** Are we talking about structured attributes (item specifics fill rate), category accuracy, or listing title quality? I'll focus on item specifics fill rate since it most directly impacts discovery.
2. **Why it matters:** A listing with 80%+ item specifics filled has 3-5x higher click-through than one with <40%. Every missing attribute is a filter that buyer can't use, a search that returns nothing.
3. **User pain:** Seller's pain: filling in specifics takes time, sellers don't see direct GMV feedback. Buyer's pain: filters don't work, comparisons are impossible.
4. **Solution — three layers:**
   - **Auto-inference:** LLM extracts attributes from existing title/description. Pre-fill item specifics on the seller's behalf. Seller confirms in one click (not 20 fields).
   - **Smart prompting:** For the 20% that LLM can't extract confidently, show sellers a single "most impactful missing attribute" prompt after listing goes live. "Adding storage capacity for your iPhone listing gets 2.3x more buyers."
   - **Taxonomy feedback loop:** Track which attributes buyers use in filters but that sellers don't fill → prioritize extraction model improvements there.
5. **Metrics:** Item specifics fill rate (%), listing-to-click conversion rate, search abandonment rate (proxy for "couldn't find what I wanted").
6. **Trade-off:** Auto-inference can be wrong. Wrong attribute (e.g., wrong storage capacity) is worse than missing attribute — it destroys buyer trust. Need confidence threshold + easy seller correction flow.

---

### Likely Question 2: "How would you prioritize eBay's taxonomy improvement roadmap?"

**Framework:** Identify the business problem, segment impact, sequence by dependency + value.

**Your answer structure:**
1. **The core problem:** Taxonomy is both a classification system AND a discovery interface. A bad taxonomy node costs you on both ends — misclassified listings AND buyers who can't find the right filter.
2. **Prioritization axes:**
   - **GMV impact:** Which categories have the highest transaction volume? Start there.
   - **Classification error rate:** Which categories have the highest misclassification rate? Those are discovery failures.
   - **Attribute coverage gap:** Which categories have the lowest item specifics fill rate? Those have the highest enrichment opportunity.
3. **Sequence:** Electronics > Fashion > Home (GMV-ordered), but within each: fix taxonomy structure before improving attribute extraction (taxonomy errors upstream corrupt everything downstream).
4. **How to measure:** Precision/recall for category classification (ML metric), buyer filter usage rate (product metric), search → purchase conversion by category (business metric).

---

### Likely Question 3: "Design a system that automatically tags eBay listings."

**This is your home turf — walk them through the architecture you actually built.**

**Your answer:**
"I've actually built something very similar for a different domain, so I'll ground this in real decisions I've made."

1. **Input:** Listing title + description + seller-selected category (as a signal, not gospel)
2. **Stage 1 — Pre-processing:** NER to extract candidate entities (brand, model, color, size). This is cheap, runs synchronously, handles the 60-70% of structured cases.
3. **Stage 2 — Embedding-based matching:** Map the listing to the most similar known product entities in the catalog via cosine similarity (pgvector equivalent). If confidence ≥0.7, accept the match.
4. **Stage 3 — LLM enrichment (for <0.7 confidence):** Pass listing + top candidate matches to LLM. Ask: "Is this listing [Product X]? Extract the following attributes: [category-specific schema]." Constrain output to taxonomy whitelist to prevent hallucination.
5. **Stage 4 — Quality gate:** Any attribute where LLM confidence < threshold → mark as "unverified," don't surface to buyer, queue for human review sample.
6. **Async architecture:** New listing goes live immediately. Enrichment happens in background within 5 minutes (batch for cost). High-value categories (Electronics, Fashion) get real-time enrichment.
7. **Metrics:** Tagging precision (% correct auto-tags), recall (% of taggable listings that got tagged), latency (time from listing to enriched), cost per enrichment.

---

## SECTION 4: PRODUCT STRATEGY QUESTION BANK

### Likely Question: "Where do you see AI taking product knowledge at eBay in 3 years?"

**Framework:** Current state → inflection points → destination → eBay's moat

**Your answer:**
"I think there are three inflection points, and they compound on each other."

1. **Year 1 — From manual to automated enrichment.** LLMs can now auto-extract 80% of item specifics from listing text with acceptable accuracy. The win here is operational: you stop depending on seller behavior change. The metric is fill rate.

2. **Year 2 — From static taxonomy to living ontology.** Right now, taxonomy is maintained by humans who propose → review → ship changes on a slow cycle. LLMs can detect emerging category clusters (new product types that don't fit existing taxonomy) and propose taxonomy updates. A "taxonomy assistant" that surfaces "there are 2,000 listings about AI smart glasses that currently split across 4 categories" → PM reviews → new node created. Taxonomy becomes adaptive, not brittle.

3. **Year 3 — From product data to product intelligence.** The knowledge graph becomes a competitive moat: eBay knows not just what an item is, but how it relates to everything else. Successor/predecessor chains ("iPhone 14 buyers also buy MagSafe cases from that era"), compatibility graphs ("this lens fits Canon EOS R5"), seasonal context ("this ski jacket was popular 2019-2021"). No competitor has this for used/unique items. The moat: Amazon's knowledge is brand-controlled. eBay's is the only knowledge graph that covers the long tail of unique, vintage, and used goods.

**The key differentiator:** Amazon wins on new goods. eBay's AI opportunity is owning the knowledge graph for the circular economy — the 90% of stuff that Amazon's catalog can't describe because it's not new.

---

## SECTION 5: PRODUCT EXECUTION & METRICS

### Likely Question: "How would you execute a taxonomy revamp for Electronics?"

**Your answer structure (execution focus):**
1. **Scope definition:** How many leaf nodes? Which subcategories? What does "done" look like?
2. **Discovery phase:** Audit current misclassification rate by node (ML metrics). Identify the 20% of nodes causing 80% of the errors. Interview top sellers in the category: where do they get confused when listing?
3. **Design:** Don't redesign the whole tree. Surgical changes to the worst-performing nodes. New nodes for emerging product types. Merge redundant nodes that cause splits.
4. **Data migration:** New taxonomy = existing listings need re-classification. Run ML reclassification on affected listings. Sample 1K for human review. Acceptable threshold: <2% incorrect reclassification.
5. **Rollout:** Shadow mode first — new taxonomy runs in parallel, compare search results. Gradual rollout with monitoring. Rollback plan if CTR drops.
6. **Metrics:** Classifier accuracy (pre/post), item specifics fill rate (pre/post), buyer filter usage rate, search-to-purchase conversion in affected categories.

### Core Metrics Framework (memorize this)

**North Star:** Listing discovery rate — % of active listings that receive at least 1 click within 7 days of listing (proxy for "does product knowledge make listings findable?")

**Leading indicators:**
- Item specifics fill rate (completeness of structured data)
- Category classification accuracy (ML metric — precision/recall)
- Entity resolution recall (% of same-product listings that are correctly grouped)

**Business outcomes:**
- Search-to-purchase conversion rate by category
- Buyer filter engagement rate (are buyers using the structured data?)
- Seller re-listing rate (do sellers come back? bad discovery = demotivated sellers)

**Guardrail metrics:**
- Wrong attribute rate (auto-tagging error → buyer trust)
- Listing-to-live latency (enrichment must not slow listing creation)

---

## SECTION 6: ECOMMERCE FOUNDATIONS (QUICK REFERENCE)

**Search relevance:** How well search results match buyer intent. LLM-extracted attributes directly improve this because structured data beats keyword matching for complex queries ("blue size 10 Nike running shoe under ₹5000").

**Faceted search / filtering:** Buyers narrow results by structured attributes. Zero item specifics = zero filter utility. This is why attribute extraction has direct GMV impact.

**Personalization:** Product knowledge enables "buyers who viewed X also viewed Y" and compatibility recommendations. Knowledge graph is the substrate.

**Long-tail discovery:** eBay's unique advantage — 2B listings, many unique. LLMs can describe and categorize one-of-a-kind items (vintage, handmade, collectible) that don't exist in any brand catalog. Amazon can't do this.

**Seller experience:** Anything that adds friction to listing reduces supply. Auto-enrichment increases supply quality without increasing seller effort. Win-win framing: "We improve your listing quality for you."

---

## SECTION 7: QUESTIONS TO ASK THEM

**On the product:**
- "What's the current item specifics fill rate in your top 3 categories, and where's the biggest gap?"
- "Is the taxonomy maintained by a dedicated team, or is it distributed across category PMs?"
- "What does the ML classification pipeline currently look like — rule-based, ML, or LLM-based?"

**On the team:**
- "What does the PM → data science collaboration model look like here — are PMs expected to write SQL, define ML metrics, or both?"
- "What does a 'launch' look like for a taxonomy change — how much of the process is automated vs. manual review?"

**On the opportunity:**
- "Where do you think the biggest leverage point is right now — improving taxonomy structure, increasing attribute coverage, or entity resolution?"

---

## SECTION 8: WATCH-OUTS

1. **Don't pitch Amazon's approach.** eBay is not Amazon. Brand Registry, seller control, brand-owned catalog — none of that is eBay's model. eBay's challenge is inferring structure from seller-generated content. Acknowledge this explicitly.

2. **LLM hallucination is the #1 risk.** Every LLM answer should mention confidence thresholds, whitelist constraints, and human review samples. Show you've thought about this in production (you have — S003 taxonomy whitelist, S020 double-rejection queue).

3. **Cost at 2B listing scale is real.** Your three-tier optimization story (S020) is directly relevant. Don't pitch "just use LLMs for everything." Show cost-aware architecture.

4. **Metrics must be bidirectional.** Always pair ML metrics (precision/recall) with product metrics (CTR, conversion, fill rate). Shows you bridge the two worlds.

5. **Execution = stakeholders, not just tech.** Taxonomy changes affect sellers (their listings get re-categorized), search teams (ranking logic changes), and ML teams (training data shifts). Mention cross-functional impact.

---

## SECTION 9: QUICK-FIRE ANSWERS

**"What is entity resolution?"**
Recognizing that multiple different text representations refer to the same real-world product. "iPhone 14 Pro 256" and "Apple iPhone14Pro 256gb" are the same entity. Critical for eBay because sellers don't follow a standard naming convention.

**"How would you evaluate an LLM-based classification system?"**
Precision (of things it classified, how many were correct), recall (of all classifiable things, how many did it catch), F1 (balance). Then: coverage (% of listings it attempted vs. passed to human review), latency, cost per classification. Track these per category, not in aggregate — a 95% overall accuracy can hide a 60% accuracy in a high-GMV category.

**"What's a knowledge graph?"**
A network of entities and relationships. At eBay: products, brands, categories, attributes, and their relationships (IS-A, MADE-BY, COMPATIBLE-WITH, SUCCESSOR-OF). Enables reasoning beyond keyword search — "show me cases compatible with this phone" requires knowing the phone model, case compatibility specs, and which listings describe compatible cases.

**"How is eBay's catalog different from Google Shopping or Amazon?"**
Google Shopping and Amazon are primarily brand-controlled catalogs — brands submit structured data. eBay's catalog is seller-generated — 135 million sellers each describing items in their own words, including millions of unique, used, and vintage items that don't exist in any brand catalog. eBay's AI challenge is unique: inferring structure from unstructured content at massive scale.

---

*Last updated: Day before R1/R2 | Branch: ebay-prep*
