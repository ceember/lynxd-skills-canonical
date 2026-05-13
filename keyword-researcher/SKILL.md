---
name: keyword-researcher
description: >
  Keyword research and topic clustering for SEO + GEO content strategy. Use when
  planning content calendars, finding keyword gaps, building topic clusters, mapping
  search intent, analyzing competitor keywords, creating keyword maps, doing keyword
  gap analysis, harvesting People Also Ask questions, classifying search intent,
  building content roadmaps, prioritizing keywords by revenue potential, auditing
  existing keyword coverage, finding long-tail opportunities, mapping keywords to
  content types, researching brand keyword defense, or creating keyword-to-content
  mapping tables for client websites. Triggers: "keyword research", "find keywords",
  "topic clusters", "content gaps", "search intent", "keyword map", "what should we
  write about", "keyword gap analysis", "People Also Ask", "long-tail keywords",
  "money keywords", "brand keywords", "keyword priority", "competitor keywords",
  "keyword-to-content map".
---

# Keyword Research Skill

Research keywords, cluster topics, map search intent, and build content strategies that rank on Google AND get cited by LLMs. Every output uses the 4-Tier Keyword Framework and includes priority scoring with hard numeric thresholds.

## Before You Start — Diagnostic Questions

Ask ALL 10 before starting research. Do not skip any. If the user cannot answer a question, use the default in brackets.

1. **Client name and website URL?** (required — no default)
2. **Industry/niche?** (e.g., ISP, auto parts, digital marketing — required)
3. **Target geography?** (default: South Africa, national)
4. **Who is the buyer?** Job title, role, or persona (e.g., "homeowner shopping for fibre", "fleet manager sourcing parts")
5. **Top 3-5 competitors?** Website URLs. If unknown, Claude finds them via industry + geo search.
6. **Primary goal?** Pick one: traffic | leads | sales | brand awareness | LLM visibility (default: leads)
7. **Existing content inventory?** URL of sitemap or list of current pages/posts. If none, state "greenfield".
8. **Monthly content capacity?** How many articles/pages can the client publish per month? (default: 4)
9. **Budget tier?** Startup (R0-5k/mo) | Growth (R5-20k/mo) | Scale (R20k+/mo) — affects volume targets and competition appetite.
10. **Any keywords already ranking?** Google Search Console access or known rankings. If none, state "no data".

## 4-Tier Keyword Framework

Every keyword MUST be classified into exactly one tier. This determines content type, priority, and expected ROI.

### Tier 1: Money Keywords (Bottom-of-funnel)

Keywords with direct purchase or signup intent. These drive revenue.

- **Signal words:** buy, price, pricing, cost, order, sign up, get, deal, package, plan, quote, apply, subscribe, hire, book
- **Content type:** Service pages, pricing pages, landing pages, product pages
- **Examples:** "fibre internet packages Johannesburg", "buy BMW brake pads online SA", "digital marketing agency pricing"
- **Target:** 15-25% of total keyword map
- **Priority:** Always P1. Create these pages FIRST.

### Tier 2: Educational Keywords (Top-of-funnel)

Keywords where the searcher wants to learn. Builds authority and trust.

- **Signal words:** how to, what is, why, guide, tutorial, explained, meaning, difference between, steps, tips
- **Content type:** Blog posts, guides, how-to articles, FAQ pages, pillar content
- **Examples:** "how fibre internet works", "what causes brake pad wear", "SEO vs PPC for small business"
- **Target:** 35-45% of total keyword map
- **Priority:** P2. High volume, builds topical authority, feeds pillar-cluster architecture.

### Tier 3: Long-Tail Keywords (Niche/specific)

3-6 word phrases with low competition and high specificity. Often convert well despite low volume.

- **Signal words:** specific product names, model numbers, location + service, "for [specific use case]"
- **Content type:** Targeted blog posts, niche landing pages, FAQ entries
- **Examples:** "uncapped fibre Bryanston 100mbps", "BMW E90 320d alternator price Kempton Park", "best SEO agency for dentists South Africa"
- **Target:** 20-30% of total keyword map
- **Priority:** P1-P2. Low effort, high conversion. Quick wins.

### Tier 4: Brand Keywords (Defensive)

Keywords containing the client's brand name, competitor brand names, or comparison terms.

- **Signal words:** [brand name], [brand] vs [competitor], [brand] review, [brand] alternative, is [brand] good
- **Content type:** Homepage, about page, comparison pages, testimonial pages, review response pages
- **Examples:** "InfiniFi reviews", "InfiniFi vs Afrihost", "is InfiniFi fibre reliable", "InfiniFi coverage areas"
- **Target:** 5-10% of total keyword map
- **Priority:** P1 for own-brand (defensive), P2 for competitor-brand (offensive).

## 8-Step Workflow

### Step 1: Scope Definition

Collect answers to all 10 diagnostic questions. Load client context from `context/` or `content/` if available. Check `data/content.db` for existing content ideas. Confirm scope before proceeding.

### Step 2: Seed Keyword Generation

Generate 80-120 seed keywords across the 4 tiers. Use these methods:

1. **Core terms** — What the business sells/does (8-12 seeds)
2. **Problem terms** — Pain points prospects search (8-12 seeds)
3. **Question terms** — Questions prospects ask (10-15 seeds)
4. **Comparison terms** — vs/alternative/review searches (8-12 seeds)
5. **Long-tail terms** — Specific location + service + modifier phrases (15-20 seeds)
6. **Brand terms** — Own brand + competitor brand queries (8-12 seeds)
7. **People Also Ask terms** — Extracted from PAA harvesting (Step 5) (10-15 seeds)
8. **Seasonal/trending terms** — Time-sensitive opportunities (5-10 seeds)

Minimum seed count: 80. If under 80, go back and expand the weakest category.

### Step 3: Search Intent Classification

Classify EVERY keyword by intent using this matrix:

| Intent | Signal Words | Content Type | Funnel Stage | Conversion Rate |
|--------|-------------|--------------|--------------|-----------------|
| Informational | how, what, why, guide, tutorial, explained | Blog post, guide, FAQ | Top | 1-3% |
| Commercial | best, top, review, compare, vs, alternatives | Comparison page, listicle, review | Middle | 3-8% |
| Transactional | buy, price, order, sign up, get, package, deal | Product/service page, landing page | Bottom | 8-15% |
| Navigational | [brand name], login, contact, support | Homepage, contact page | Bottom | Varies |
| Local | near me, in [city], [area], [suburb] | Location page, Google Business Profile | Bottom | 10-20% |

Rules:
- Every keyword gets exactly ONE primary intent
- If ambiguous, check Google results — the dominant content type reveals intent
- Local intent overrides other intents (e.g., "best fibre near me" = Local, not Commercial)

### Step 4: Topic Clustering

Group keywords into clusters around pillar topics using hub-and-spoke architecture.

Rules:
- 5-8 pillar topics per site (no more, no fewer for initial map)
- 8-15 cluster keywords per pillar
- Each cluster keyword maps to ONE page (no keyword cannibalization)
- Pillar page links to all cluster pages; cluster pages link back to pillar
- Cross-link between related clusters ONLY when topically adjacent

```
Pillar Topic: "[Primary Keyword]"
├── Cluster 1: [Subtopic]
│   ├── "[keyword]" (intent) — Tier X — Priority PX
│   ├── "[keyword]" (intent) — Tier X — Priority PX
│   └── "[keyword]" (intent) — Tier X — Priority PX
├── Cluster 2: [Subtopic]
│   ├── "[keyword]" (intent) — Tier X — Priority PX
│   └── "[keyword]" (intent) — Tier X — Priority PX
└── Cluster 3: [Subtopic]
    ├── "[keyword]" (intent) — Tier X — Priority PX
    └── "[keyword]" (intent) — Tier X — Priority PX
```

### Step 5: People Also Ask Harvesting

For each pillar topic's primary keyword, extract PAA questions using this method:

1. **Browse** the keyword on Google (use `/browse` skill if available)
2. **Extract** the first 4 PAA questions shown
3. **Click** each PAA to reveal 2-3 follow-up PAAs (yields 8-12 per keyword)
4. **Deduplicate** across all pillars
5. **Classify** each PAA by intent and tier
6. **Map** each PAA to either: FAQ schema on an existing page, a standalone blog post, or a subsection within a cluster article

Output PAA table:

| PAA Question | Source Keyword | Intent | Map To | Content Action |
|-------------|---------------|--------|--------|----------------|
| How fast is fibre in South Africa? | fibre internet SA | Informational | Pillar page FAQ | Add FAQ schema |
| Is 100mbps fibre fast enough? | fibre speed | Informational | New blog post | Write article |
| Which fibre provider is cheapest? | best fibre SA | Commercial | Comparison page | Existing page |

Minimum PAA harvest: 30 questions across all pillars. If under 30, expand to secondary keywords.

### Step 6: Competitor Keyword Gap Analysis

For each of the 3-5 competitors:

1. **Browse their sitemap** (`/sitemap.xml`) or crawl top-level navigation
2. **Map their content** — list every content page with its target keyword
3. **Identify 5 gap types:**

| Gap Type | Definition | Action |
|----------|-----------|--------|
| Content gap | Topics they cover that the client does NOT | Create content — highest priority |
| Quality gap | Topics both cover but competitor ranks higher | Rewrite/expand client content |
| Format gap | Topics where a different format would win (video > text, tool > article) | Create superior format |
| Freshness gap | Competitor content is outdated (12+ months old) | Create updated version |
| Entity gap | Competitor lacks structured data/schema markup | Add schema for advantage |

4. **Score each gap** by revenue potential (High/Medium/Low)
5. **Prioritize** content gaps and quality gaps as P1, format and freshness gaps as P2

Output: Competitor Gap Matrix

| Keyword/Topic | Competitor | Gap Type | Their Ranking | Revenue Potential | Priority |
|--------------|-----------|----------|--------------|-------------------|----------|
| fibre installation guide | Afrihost | Content gap | #3 | Medium | P1 |
| fibre vs LTE comparison | Rain | Quality gap | #1 | High | P1 |

### Step 7: GEO Keyword Signals

For every P1 keyword, check and flag GEO signals:

| GEO Signal | What It Means | How to Check | Content Implication |
|-----------|--------------|-------------|---------------------|
| AI Overview present | Google shows AI summary | Search the keyword | Structure content for extraction (lists, tables, definitions) |
| Featured snippet exists | Position zero available | Search the keyword | Format content to win snippet (40-60 word answer blocks) |
| PAA box appears | FAQ opportunity | Search the keyword | Add FAQ schema with exact PAA wording |
| Reddit/forum ranks | LLMs train on this | Check top 10 results | Create definitive answer content that surpasses forum quality |
| Wikipedia in results | Entity-linked topic | Check top 10 results | Use entity optimization, add schema markup |
| No AI Overview | Pure organic play | Search the keyword | Standard SEO approach, focus on backlinks |

Flag each keyword: GEO-HIGH (3+ signals), GEO-MED (1-2 signals), GEO-LOW (0 signals).

### Step 8: Priority Scoring & Final Map

Score each keyword cluster using this weighted formula:

| Factor | Weight | Score 1-10 | Guidance |
|--------|--------|-----------|----------|
| Revenue relevance | 30% | 10 = directly drives purchase, 1 = no revenue connection | Map to offer stack |
| Competition feasibility | 20% | 10 = no competition, 1 = dominated by authority sites | Check top 10 domain authority |
| Search volume estimate | 15% | 10 = high volume confirmed, 1 = negligible | Use autocomplete + PAA signals |
| GEO potential | 15% | 10 = GEO-HIGH, 5 = GEO-MED, 1 = GEO-LOW | From Step 7 |
| Content gap size | 10% | 10 = no competitor covers it, 1 = saturated | From Step 6 |
| Quick-win potential | 10% | 10 = can rank in 30 days, 1 = 12+ months | Based on competition + existing authority |

**Weighted score = (Revenue × 0.30) + (Competition × 0.20) + (Volume × 0.15) + (GEO × 0.15) + (Gap × 0.10) + (Quick-win × 0.10)**

## Quality Gates

Three mandatory checkpoints. ALL must pass before delivering the keyword map.

| Gate | Checkpoint | Threshold | Action if Failed |
|------|-----------|-----------|-----------------|
| QG1: Coverage | Total keywords in final map | Minimum 80 keywords | Go back to Step 2 and expand seed generation |
| QG2: Tier Balance | Money keywords as % of total | 15-25% (not below 15%, not above 25%) | Rebalance — add money keywords if under, reclassify if over |
| QG3: Priority Score | Average P1 cluster score | Minimum 6.5 weighted score | Rescore or replace low-scoring P1 keywords with higher-scoring alternatives |
| QG4: PAA Coverage | PAA questions harvested | Minimum 30 across all pillars | Expand PAA harvesting to secondary keywords |
| QG5: Competitor Gaps | Content gaps identified | Minimum 10 actionable gaps | Add more competitors or dig deeper into existing competitor content |

## Keyword-to-Content Mapping Table

Every keyword map MUST include this mapping table. It is the bridge between research and execution.

| Keyword | Tier | Intent | Priority | Content Type | Target URL | Word Count | Pillar Link | Status |
|---------|------|--------|----------|-------------|-----------|-----------|-------------|--------|
| [keyword] | Money/Edu/LT/Brand | Info/Comm/Trans/Nav/Local | P1/P2/P3 | Blog/Landing/Service/FAQ | /existing-url or "CREATE" | 1500-4000 | /pillar-url | Not started/Draft/Live |

Rules:
- Every P1 keyword has a row
- Every P2 keyword has a row
- P3 keywords listed in appendix only
- "Target URL" must be specific — either an existing URL or "CREATE: /suggested-slug"
- Word count based on content type: Service page 800-1500, Blog post 1500-2500, Pillar page 2500-4000, FAQ page 500-1000

## Complete Example: InfiniFi ISP

**Input from user:** "Do keyword research for InfiniFi, a fibre ISP in Johannesburg. Website: infinifi.co.za. Competitors: Afrihost, Rain, Vuma, Cool Ideas. Goal: leads. Budget: Growth tier. Greenfield content — no existing blog."

**Output (abbreviated — full output follows this structure):**

### Executive Summary
- Total keywords identified: 94
- Topic clusters: 6 pillars, 38 clusters
- Tier breakdown: 19 money (20%), 38 educational (40%), 28 long-tail (30%), 9 brand (10%)
- PAA questions harvested: 42
- Competitor content gaps: 14
- P1 keywords (this month): 12 across 4 clusters
- Content needed: 6 articles month 1, 6 month 2, 6 month 3

### Pillar 1: Fibre Internet Johannesburg

**Primary keyword:** "fibre internet Johannesburg" — Intent: Local — GEO: HIGH

| Keyword | Tier | Intent | Score | GEO | Content Type | Priority |
|---------|------|--------|-------|-----|-------------|----------|
| fibre internet packages Johannesburg | Money | Transactional | 8.2 | HIGH | Service page | P1 |
| best fibre provider Johannesburg | Money | Commercial | 7.8 | HIGH | Comparison page | P1 |
| how to get fibre installed in Joburg | Edu | Informational | 7.1 | MED | Blog post | P1 |
| fibre coverage check Johannesburg | Money | Transactional | 7.5 | MED | Tool/landing page | P1 |
| cheapest fibre deals 2026 | Long-tail | Commercial | 6.8 | HIGH | Blog post | P2 |
| Vuma fibre vs InfiniFi | Brand | Commercial | 6.5 | LOW | Comparison page | P2 |
| fibre installation cost South Africa | Edu | Informational | 6.9 | HIGH | Blog post | P2 |
| is 100mbps fibre fast enough for gaming | Long-tail | Informational | 5.8 | MED | Blog post | P3 |

### PAA Harvest (Sample)

| PAA Question | Source Keyword | Intent | Map To | Action |
|-------------|---------------|--------|--------|--------|
| Which fibre provider is best in Joburg? | best fibre Johannesburg | Commercial | Comparison page | New page |
| How long does fibre installation take? | fibre installation Joburg | Informational | Installation guide FAQ | FAQ schema |
| Is fibre better than LTE for working from home? | fibre vs LTE | Commercial | New comparison post | Write article |
| What speed fibre do I need? | fibre speed guide | Informational | Speed guide blog | Write article |

### Competitor Gap Matrix (Sample)

| Topic | Competitor | Gap Type | Priority |
|-------|-----------|----------|----------|
| Fibre installation step-by-step guide | Afrihost has one, InfiniFi doesn't | Content gap | P1 |
| Fibre vs LTE vs 5G comparison | Rain dominates this | Quality gap | P1 |
| Area-specific coverage pages | Cool Ideas has per-suburb pages | Format gap | P2 |
| Fibre gaming performance guide | No competitor covers this well | Content gap | P1 |

### 90-Day Content Calendar

**Month 1 (6 articles):**
1. "Fibre Internet Packages in Johannesburg — Compare Plans & Prices" (Money, P1)
2. "Best Fibre Providers in Johannesburg 2026 — Honest Comparison" (Money, P1)
3. "How to Get Fibre Installed — Complete SA Guide" (Edu, P1)
4. "Fibre vs LTE vs 5G — Which Is Best for Your Home?" (Edu, P1)
5. "InfiniFi Coverage Areas — Check If You Can Get Fibre" (Money, P1)
6. "What Fibre Speed Do I Need? A Simple Guide" (Edu, P1)

**Month 2 (6 articles):** [P1 remaining + top P2 keywords]
**Month 3 (6 articles):** [P2 keywords, long-tail quick wins]

## Edge Cases

| Scenario | How to Handle |
|----------|--------------|
| Client has no competitors (new niche) | Use adjacent-industry competitors. E.g., for a new AI tool, use existing SaaS competitors in the same problem space. Flag as "low competition opportunity — move fast." |
| Client is in a regulated industry (medical, legal, financial) | Add YMYL (Your Money Your Life) flag to all keywords. Prioritize E-E-A-T signals: author bios, citations, credentials. Avoid making claims — use "may", "consult a professional". |
| Client targets multiple cities/regions | Create location keyword clusters for EACH target area. Do NOT combine — "fibre Cape Town" and "fibre Johannesburg" are separate clusters with separate pages. |
| Client has existing content that ranks | Run cannibalization check: if two pages target the same keyword, merge or redirect. Never create new content that competes with existing ranking content. |
| Bilingual market (English + Afrikaans) | Research Afrikaans keyword variants separately. Create Afrikaans content only if volume justifies it (minimum 20 searches/month estimated). Map Afrikaans keywords to English pillar for internal linking. |
| Seasonal or trending keywords | Flag with [SEASONAL] tag. Include in calendar for the relevant month only. Add "publish by" deadline — seasonal content published late has zero value. |
| No search volume data available | Use proxy signals: Google Autocomplete (appears = medium+), PAA (appears = medium), Reddit threads with 50+ comments (high interest), competitor has dedicated page (worth targeting). Document estimation method for each keyword. |

## South African Market Specifics

### Local Search Patterns
- **Suffix patterns:** "in South Africa", "in SA", "in Joburg", "in CPT", "in Durbs" — all are separate keywords
- **Price format:** Users search with "R" or "rand", never "$" — e.g., "fibre R500 per month"
- **Comparison sites:** MyBroadband, Hippo, HelloPeter, TrustPilot ZA rank prominently — earning reviews/listings on these is a keyword strategy
- **Township and suburb names:** Soweto, Khayelitsha, Sandton, Bryanston — location pages for each target suburb/area
- **Afrikaans variants:** "beste" (best), "goedkoop" (cheap), "naby my" (near me), "prys" (price), "vergelyking" (comparison)

### SA-Specific Seasonal Spikes
- **Load shedding:** Spikes for generators, UPS, inverters, solar — track Eskom schedule
- **Back to school (January):** Education, stationery, uniforms, student deals
- **Black Friday (November):** "Black Friday deals SA" is massive — plan content 6 weeks ahead
- **Tax season (July-November):** Tax software, accountant queries spike
- **Payday (25th-1st):** Data, airtime, shopping queries spike cyclically
- **Matric results (January):** University, bursary, career keywords spike

### SA Domain Authority Considerations
- `.co.za` domains get a ranking boost for SA queries over `.com` domains
- South African hosting/CDN improves local page speed scores
- Google Business Profile is critical for local service businesses — always include in keyword strategy
- News24, IOL, MyBroadband, BusinessTech dominate informational queries — competing requires superior content depth

## Cross-Skill Integration

This skill produces structured output consumed by other skills. Use exact formats below for clean handoffs.

| Receiving Skill | What It Needs | Handoff Format | When to Trigger |
|----------------|--------------|----------------|-----------------|
| **seo-content-writer** | Target keyword, secondary keywords, intent, word count, audience | `PRIMARY: [keyword], SECONDARY: [kw1, kw2, kw3], INTENT: [type], WORDS: [count], AUDIENCE: [persona]` | After keyword map is approved, for each P1 keyword |
| **headline-optimizer** | Keyword + intent + audience | `KEYWORD: [keyword], INTENT: [type], AUDIENCE: [persona], CONTENT_TYPE: [type]` | When writing titles for keyword-targeted content |
| **geo-optimizer** | Entity list, keyword clusters, GEO signals | `ENTITIES: [list], CLUSTERS: [pillar→keywords], GEO_SIGNALS: [keyword→signal level]` | After keyword map is complete, before content creation |
| **landing-page-writer** | Money keyword, audience, offer, competitors | `KEYWORD: [money keyword], AUDIENCE: [persona], OFFER: [product/service], COMPETITORS: [list]` | For each Tier 1 (Money) keyword mapped to a landing page |
| **content-auditor** | Published URL + target keyword | `URL: [url], TARGET_KEYWORD: [keyword], INTENT: [type]` | After content is published, to verify keyword targeting |
| **schema-generator** | PAA questions, keyword entities | `FAQS: [question→answer pairs], ENTITIES: [name, type, properties]` | After PAA harvesting, for FAQ schema on existing pages |
| **Content Pipeline** (`/capture`) | Keyword + content type + priority | Use `/capture` directly with keyword as the idea | After keyword map is approved, to populate content pipeline |

## Output Format Template

Every keyword research delivery MUST follow this structure:

```markdown
# [Client Name] Keyword Research — [Date]

## Executive Summary
- Total keywords: [number] (must be 80+)
- Pillars: [number] (5-8)
- Tier breakdown: [X] money ([%]), [X] educational ([%]), [X] long-tail ([%]), [X] brand ([%])
- PAA questions harvested: [number] (must be 30+)
- Competitor gaps identified: [number] (must be 10+)
- P1 content needed: [X] articles/pages
- Estimated timeline: [X] months at [X] articles/month

## Quality Gate Results
- QG1 Coverage: [PASS/FAIL] — [X] keywords (threshold: 80)
- QG2 Tier Balance: [PASS/FAIL] — Money keywords at [X]% (threshold: 15-25%)
- QG3 Priority Score: [PASS/FAIL] — Average P1 score [X] (threshold: 6.5)
- QG4 PAA Coverage: [PASS/FAIL] — [X] PAAs (threshold: 30)
- QG5 Competitor Gaps: [PASS/FAIL] — [X] gaps (threshold: 10)

## Pillar [N]: [Topic]
### Primary Keyword: [keyword] — Intent: [type] — GEO: [HIGH/MED/LOW]
### Cluster Keywords:
[Keyword table with Tier, Intent, Score, GEO, Content Type, Priority, Target URL]

## People Also Ask Harvest
[PAA table with Question, Source Keyword, Intent, Map To, Action]

## Competitor Gap Matrix
[Gap table with Topic, Competitor, Gap Type, Revenue Potential, Priority]

## Keyword-to-Content Mapping
[Full mapping table — every P1 and P2 keyword with Target URL, Word Count, Status]

## 90-Day Content Calendar
### Month 1: [X articles — titles and target keywords]
### Month 2: [X articles — titles and target keywords]
### Month 3: [X articles — titles and target keywords]

## Appendix: P3 Keywords
[Low-priority keywords for future consideration]
```

Save output as DOCX to `outputs/{client-slug}/seo/keyword-research.docx` using the execution engine.

## References

- See `references/keyword-frameworks.md` for advanced clustering methods, volume estimation techniques, and competitive gap analysis framework
