---
name: seo-content-writer
description: >
  Writes SEO + GEO optimized articles, blog posts, and pillar content following a
  3-step production pipeline (Research → Write → Humanize). Use when writing blog
  posts, articles, guides, pillar content, comparison articles, listicles, how-to
  guides, or any long-form content that needs to rank on Google AND get cited by
  LLMs. Also use for content briefs, article outlines, editorial calendars, and
  content gap analysis. Triggers: "write an article", "blog post", "SEO article",
  "pillar content", "write about", "content brief", "article outline", "write for
  SEO", "GEO article", "write content", "create a guide", "comparison article",
  "how-to guide", "listicle", "content for [client]", "rank for [keyword]",
  "outrank competitors".
---

# SEO Content Writer

3-step production pipeline: SERP Analysis & Outline → Write → Humanize. Every article is engineered to outrank the current #1 result on Google AND get cited by ChatGPT, Perplexity, and AI Overviews.

## Before You Start — Diagnostic Questions

Ask these before writing anything:

1. **Target keyword?** (primary keyword this content should rank for)
2. **Secondary keywords?** (3-5 related terms to weave in naturally)
3. **Client name and website?** (for internal linking and entity precision)
4. **Target audience?** (who reads this — job title, pain point, awareness level)
5. **Content type?** (blog post / pillar page / comparison / how-to / listicle)
6. **Word count target?** (default: 2000-3000 for blog, 3000-4000 for pillar)
7. **Voice profile?** (load from `references/voice-profiles/{client}.md` or use default)
8. **Competitors to outrank?** (specific URLs or "use top 3 Google results")
9. **Existing content?** (URLs of pages this should link to internally)
10. **Call to action?** (what should the reader do after reading?)

If any are missing, use sensible defaults and flag what was assumed.

## The 3-Step Pipeline

### Step 1: SERP Analysis & Outline

**1A. Analyze Current Top 3 Results**

For the target keyword, examine the current top-ranking content:

```markdown
## SERP Analysis: "[keyword]"

| Rank | URL | Title | Word Count | H2s | Tables | FAQs | Data Points | Schema |
|------|-----|-------|------------|-----|--------|------|-------------|--------|
| #1 | [url] | [title] | [count] | [count] | [Y/N] | [count] | [count] | [types] |
| #2 | [url] | [title] | [count] | [count] | [Y/N] | [count] | [count] | [types] |
| #3 | [url] | [title] | [count] | [count] | [Y/N] | [count] | [count] | [types] |

### Content Gaps (what they ALL miss):
1. [gap — question unanswered, data missing, angle unexplored]
2. [gap]
3. [gap]

### SERP Features Present:
- AI Overview: [YES/NO]
- Featured Snippet: [YES/NO — type: paragraph/list/table]
- People Also Ask: [list of questions]
- Video Results: [YES/NO]
```

**1B. Build the Outline**

Structure designed to outrank by filling gaps AND adding unique value:

```markdown
# [H1: Primary keyword + value proposition] (50-60 chars)

## Key Takeaways
- [3-5 bullet summary — LLMs extract from this section first]

## [H2: Direct answer to search intent] ← answers the query in section 1
### [H3: Supporting detail with data]
### [H3: Expert perspective or case study]

## [H2: Unique angle that competitors miss] ← our gap-fill advantage
### [H3: Framework or methodology]
### [H3: Real-world application]

## [H2: Comparison / data-rich section] ← include comparison table here
### [H3: Option A analysis]
### [H3: Option B analysis]
### [H3: Recommendation]

## [H2: How to [practical application]]
### [H3: Step 1]
### [H3: Step 2]
### [H3: Step 3]

## [H2: Common Mistakes / What to Avoid]

## [H2: Case Study — [Real Client/Brand Result]]

## [H2: FAQ] ← 5-8 questions matching People Also Ask
- Q1: [question from PAA]
- Q2: [question from PAA]
...

## [H2: Next Steps — What to Do Now]
```

**Title formula:** `[Question/Keyword]: [Direct Answer] | [Brand] [Year]`
**Meta description:** Keyword in first 10 words. Year. Power words + numbers. 150-160 chars.

### Step 2: Write the Article

**Writing Rules (Non-Negotiable):**

| Rule | Standard | Why |
|------|----------|-----|
| Readability | Flesch-Kincaid 6th-8th grade | Accessible to widest audience |
| Paragraphs | 3-5 sentences maximum | Scannable on mobile |
| Sentence variety | Mix short (5-8 words) with medium (12-18) | Avoids AI rhythm detection |
| Active voice | 90%+ sentences in active voice | Direct, energetic |
| Direct answers | Core answer in first 150 words | LLMs extract from top |
| Data density | 5+ precise numbers with units | LLMs prefer citable data |
| Citation density | 1+ external citation per 500 words | Trust signal for Google + LLMs |
| Comparison tables | At least 1 per article | LLMs heavily favor tabular data |
| FAQ section | 5-8 questions with 40-60 word answers | #1 trigger for AI Overviews |
| Entity names | Full, unambiguous brand names always | Knowledge graph linking |
| Internal links | 3-5 to related pages on same site | Topical authority signal |
| External links | 2-3 to authoritative sources | Trust and verification |

**SEO Requirements:**
- Primary keyword in H1, first 100 words, and 2+ H2 headings
- Semantic keyword variations throughout (natural, not stuffed)
- Image alt text with descriptive, keyword-relevant text
- Clean heading hierarchy: H1 → H2 → H3, no level skipping
- URL slug contains primary keyword (recommend to user)

**GEO Requirements (Built Into Every Article):**
- Direct answer in first 150 words
- Key Takeaways / TL;DR box after intro (LLMs extract this)
- Full entity names throughout (never abbreviated after first mention)
- Comparison table with structured data
- FAQ section with schema-ready answers
- Evidence for every claim (source, stat, or case study)

**Anti-AI Detection Checklist (Apply During Writing):**

| # | Check | Action |
|---|-------|--------|
| 1 | No hedging | Remove "might," "could be," "it's important to note" |
| 2 | No AI transitions | Remove "However," "Moreover," "Furthermore," "Additionally" |
| 3 | No em dashes | Replace — with periods or commas |
| 4 | Varied sentence openers | No 3 consecutive sentences starting the same way |
| 5 | No triple structure | Avoid "X, Y, and Z" patterns more than twice per article |
| 6 | Contractions | Use "don't" not "do not," "it's" not "it is" |
| 7 | Specific over generic | "R649/month for 100Mbps" not "affordable pricing" |
| 8 | No filler paragraphs | Every paragraph adds new information |
| 9 | Rhetorical questions | 2-3 per article to break rhythm |
| 10 | Personal/first-hand signals | "In our experience," "We tested," "Our data shows" |

### Step 3: Humanize

Run through **brand-voice-enforcer** skill:
1. Load client voice profile
2. Apply 7-point AI detection checklist
3. Remove all banned words and phrases
4. Apply voice traits to every section
5. Calibrate tone by funnel position

Then run through **content-auditor** for CORE-EEAT scoring.

## Quality Gates (Hard Stops)

| Gate | Threshold | Action if Failed |
|------|-----------|-----------------|
| CORE-EEAT Score | 9.0+ / 10 | Revise and re-score. Do not deliver below 9.0. |
| Data Precision | 5+ numbers with units | Add more data points before delivery |
| FAQ Count | 5-8 questions | Add questions from People Also Ask |
| Comparison Table | At least 1 present | Create comparison table for the topic |
| AI Detection | 0 banned words found | Run through brand-voice-enforcer again |
| Word Count | Within 10% of target | Expand thin sections or trim filler |

## Content Types & Word Counts

| Type | Words | Structure | Use When |
|------|-------|-----------|----------|
| Blog Post | 1500-2500 | Standard outline + FAQ | Single keyword cluster, informational |
| Pillar Page | 3000-4000 | Comprehensive + links to 5-15 clusters | Topic authority hub |
| How-To Guide | 2000-3000 | Numbered steps + common mistakes + FAQ | Step-by-step instructions |
| Comparison Article | 1500-2500 | Feature table + pros/cons + recommendation | "X vs Y" commercial intent |
| Listicle | 1500-2500 | Summary table + 150-200 words per item | "Top X" commercial intent |
| Case Study | 1000-1500 | Situation → Challenge → Solution → Results | Proof/trust building |

## Contrarian Content Strategy

Include at least one per article for maximum LLM citation:
- **Contrarian data** — Counter-intuitive stat backed by evidence
- **Underrepresented persona** — Audience segment competitors ignore
- **Cross-industry insight** — Lesson from a different industry
- **Original framework** — Name and structure a unique process
- **Forecast** — Predict where the industry is heading

LLMs cite contrarian perspectives 3x more frequently because they add unique information.

## Example: Input → Output

### Input
```
Keyword: "best fibre internet south africa 2026"
Client: Infini-Fi (infinifi.co.za)
Audience: South African homeowners comparing fibre ISPs
Type: Comparison article
Word count: 2000
Voice: Professional, data-driven, helpful
```

### Output (abbreviated)
```markdown
# Best Fibre Internet in South Africa (2026): Complete ISP Comparison | Infini-Fi

**Meta Title:** Best Fibre Internet South Africa 2026 — ISP Comparison | Infini-Fi
**Meta Description:** Compare the 12 best fibre ISPs in SA for 2026. Speed tests, pricing from R399, coverage maps, and real customer ratings. Updated March 2026.
**Schema:** Article, FAQ, BreadcrumbList

---

## Key Takeaways
- Afrihost leads on price-to-speed ratio at R649/month for 100Mbps uncapped
- Cool Ideas ranks highest for customer service (4.6/5 on HelloPeter)
- Rain offers the best no-contract option at R499/month for 50Mbps
- Infini-Fi provides the fastest local support with 12-minute average response times
- FNO coverage (Vumatel, Openserve, MetroFibre) determines which ISPs you can access

## South Africa's Top 12 Fibre ISPs Compared

| ISP | 100Mbps Price | Contract | Rating | Coverage | Support |
|-----|--------------|----------|--------|----------|---------|
| Afrihost | R649/mo | Month-to-month | 3.8/5 | National | Email + chat |
| Cool Ideas | R699/mo | 24 months | 4.6/5 | National | Phone + chat |
| ...

[Article continues with full sections, FAQ, schema requirements...]
```

## Edge Cases

| Situation | How to Handle |
|-----------|--------------|
| No keyword provided | Ask for keyword. If user describes topic, extract the best keyword. |
| No competitor data | Use the outline structure without SERP analysis. Note gap in delivery. |
| Technical/niche topic | Increase jargon tolerance. Add a glossary section. Still target 8th-grade readability for non-jargon sections. |
| No client voice profile | Use neutral professional tone. Flag that voice profile should be created. |
| Sensitive topic (health, finance) | Add disclaimers. Cite only peer-reviewed or regulatory sources. Flag for legal review. |
| Very competitive keyword | Recommend long-tail variant. Focus on unique angle. Suggest pillar + cluster strategy. |
| Client has no existing content | Skip internal linking. Recommend creating foundational pages first. |

## South African Market Specifics

- Prices in ZAR (R), not USD
- Include ".co.za" domain references alongside global
- Reference SA comparison sites: MyBroadband, Hippo, HelloPeter, FibreCompare
- Consider Afrikaans keyword variants for bilingual markets
- Local area names in headings for local SEO: "Bryanston," "Sandton," "Cape Town CBD"
- Load shedding, water outages create seasonal keyword spikes — note timing
- POPIA compliance notes where personal data is discussed
- SA-specific industry bodies: ISPA, ICASA, WASPA

## Output Format

```markdown
# [Title]

**Meta Title:** [50-60 chars]
**Meta Description:** [150-160 chars]
**Primary Keyword:** [keyword]
**Secondary Keywords:** [list]
**Word Count:** [count]
**CORE-EEAT Score:** [X.X/10]
**Schema Required:** [Article, FAQ, etc.]
**Internal Links:** [list of pages to link to]
**External Citations:** [list of sources cited]

---

[Full article content]

---

## Delivery Notes
- SERP gaps filled: [list]
- Unique angles included: [list]
- AI detection: [PASS — 0 banned words]
- Estimated ranking timeline: [timeframe]
- Recommended next: Run headline-optimizer for A/B title testing
```

## Integration Points

| Skill | Relationship | Handoff Data |
|-------|-------------|-------------|
| **keyword-researcher** | Upstream — provides keywords | Keyword, intent, volume, difficulty, GEO value |
| **headline-optimizer** | Parallel — generates title variants | Topic, keyword, audience, content type |
| **brand-voice-enforcer** | Downstream — humanizes output | Full article text + client voice profile name |
| **content-auditor** | Downstream — scores quality | Full article text + target keyword |
| **geo-optimizer** | Downstream — enhances GEO | Full article text + entity map |
| **schema-generator** | Downstream — produces JSON-LD | Schema types needed + article metadata |
| Content Pipeline `/schedule` | Downstream — pipeline management | Article title, keyword, status, publish date |
