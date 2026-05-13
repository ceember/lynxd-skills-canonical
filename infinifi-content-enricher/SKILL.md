---
name: infinifi-content-enricher
description: >
  InfiniFi Pipeline Stage 4 — transforms SEO/GEO-optimised content into visually
  scannable web content with enrichment elements (tables, callout boxes, stat
  highlights, step blocks, pros/cons tables, key takeaway boxes, coverage tables,
  package widgets, author blocks). Takes post-GEO content and adds visual structure.
  Use when: enriching InfiniFi content, adding visual elements, running Stage 4,
  content enrichment, making content scannable, adding tables/callouts/widgets.
  Triggers: "enrich infinifi content", "infinifi enrichment", "stage 4 enrichment",
  "add visual elements", "enrich this infinifi piece", "make scannable",
  "pipeline stage 4", "add tables and callouts", "content enrichment infinifi".
  Do NOT trigger for: generic content formatting, Stage 1 audit (use infinifi-content-auditor),
  Stage 2 SEO (use seo-content-writer), Stage 3 GEO (use geo-optimizer),
  Stage 5 CRO (use cro-optimizer), non-InfiniFi client content.
---

# InfiniFi Content Enricher -- Pipeline Stage 4

Transform SEO/GEO-optimised Infini-Fi content into visually scannable web pages with enrichment elements. Runs after geo-optimizer (Stage 3), before cro-optimizer (Stage 5).

---

## FOR CLAUDE

### Behavior Rules
- Explain what enrichments you're adding and why BEFORE inserting them
- Do NOT duplicate GEO structure -- FAQ schema and HowTo schema are added by geo-optimizer (Stage 3). Never add these.
- Do NOT duplicate brand-voice-enforcer logic -- word bans, tone checks, etc. are not your job.
- Do NOT add CTAs -- cro-optimizer handles CTAs in Stage 5. You add visual structure, not sales elements.
- Be honest about what elements are applicable. If a piece has no comparison opportunity, do not force a comparison table.
- Use ONLY verified Infini-Fi stats (see InfiniFi Context below). Never fabricate numbers.
- Use ONLY verified coverage data from infinifi.co.za/coverage. Never fabricate suburb availability.
- Use ONLY verified package/pricing data from infinifi.co.za/deals. Never fabricate prices.
- When inserting HTML enrichment elements into markdown, use the templates from `references/enrichment-elements.md`
- Preserve all existing content structure (H2s, H3s, paragraphs). Enrichments are ADDITIONS, not replacements.

### Pacing Messages
1. After reading file: "Reading content... [filename] -- [word_count] words, identified as [content_type]."
2. After scanning: "Identifying enrichment opportunities... Found [N] applicable elements for this [content_type]."
3. During enrichment: "Adding [N] elements... [element_name_1], [element_name_2], ..."
4. After completion: "Done. [N]/[M] required elements added. Enrichment score: [score]. [PASS/FAIL]."

### Error Handling
| Error | Cause | Fix |
|-------|-------|-----|
| FILE_NOT_FOUND | Path doesn't exist | Check path. Files usually in `outputs/infinifi/`. |
| FILE_EMPTY | File has no content | File needs content before enrichment. |
| UNSUPPORTED_TYPE | File is not .md, .txt, or .html | Convert to supported format first. |
| NO_ENRICHMENTS_APPLICABLE | Content type has no applicable enrichments | Rare. Note in manifest and return content unchanged. |

### Context Awareness
Before enriching, load these if not already in context:
- `references/enrichment-elements.md` (this skill's HTML/markdown templates)
- InfiniFi pipeline context from the auditor skill's `references/infinifi-facts.md`
Do NOT ask the user for information that exists in these files.

---

## Input

| Field | Type | Required | Example |
|-------|------|----------|---------|
| file_path | string | YES | `outputs/infinifi/guides/what-speed-do-i-need.md` |
| content_type | enum | YES | `blog_post` \| `educational_guide` \| `area_page` \| `faq` \| `comparison_page` \| `tool_page` |
| enrichment_level | enum | NO | `full` \| `minimal` (default: `full`) |

If `content_type` not provided: infer from path and content. If ambiguous, ask.

**Supported file types:** .md, .txt, .html

**Input validation:** Normalise path. Reject paths outside workspace root.

---

## Process

### Step 1: Read and Classify
1. Read the file content
2. Confirm content_type matches actual content (warn if mismatch)
3. Count words, count H2 sections, detect existing enrichment elements (to avoid duplicates)

### Step 2: Scan for Enrichment Opportunities
1. Load the enrichment requirements matrix (see Enrichment Elements by Content Type below)
2. Identify which required elements apply to this content_type
3. For each element, check if data is available:
   - Stat Callout: are there verified stats relevant to the topic?
   - Coverage Table: is there suburb/area data to include?
   - Package Widget: does the content reference deals or packages?
   - Comparison Table: are there 2+ options being compared?
   - Step Block: are there sequential instructions?
4. Build the enrichment plan

### Step 3: Add Enrichment Elements
1. Insert elements at appropriate positions in the content:
   - **Key Takeaway Box**: after the introduction (first H2 or first paragraph)
   - **Stat Callout Boxes**: near relevant paragraphs, max 2 per page
   - **Comparison Tables**: within the section comparing options
   - **Speed Tier Tables**: within sections discussing speed options
   - **Step Blocks**: within how-to sections (must map 1:1 to any existing HowTo schema steps)
   - **Pros/Cons Tables**: within sections evaluating a product/service
   - **Coverage Area Tables**: within area-specific sections
   - **Package Widgets**: within sections referencing deals or pricing
   - **Author + Trust Block**: at the end of the article (blog posts only)
2. Use HTML templates from `references/enrichment-elements.md`
3. Fill templates with content-specific data
4. If `enrichment_level` is `minimal`: add only Key Takeaway Box and Author Block (if blog)

### Step 4: Generate Output
1. Write enriched content back (or to new file with `-enriched` suffix)
2. Generate enrichment manifest JSON
3. Calculate enrichment score

---

## Enrichment Elements by Content Type

| Element | blog_post | educational_guide | area_page | faq | comparison_page | tool_page |
|---------|-----------|-------------------|-----------|-----|-----------------|-----------|
| Key Takeaway Box | REQUIRED | REQUIRED | optional | skip | REQUIRED | optional |
| Stat Callout Box | REQUIRED | REQUIRED | REQUIRED | skip | optional | optional |
| Comparison Table | optional | REQUIRED | skip | skip | REQUIRED | optional |
| Speed Tier Table | optional | REQUIRED (speed guides) | skip | skip | REQUIRED (speed comparisons) | skip |
| Step-by-Step Block | optional | REQUIRED (how-to guides) | skip | skip | skip | REQUIRED |
| Pros/Cons Table | optional | optional | skip | skip | REQUIRED | skip |
| Coverage Area Table | skip | skip | REQUIRED | skip | skip | skip |
| Package Widget | optional | optional | optional | skip | REQUIRED (deals refs) | skip |
| Author + Trust Block | REQUIRED | optional | skip | skip | skip | skip |

**Legend:**
- **REQUIRED** = must be present for PASS. Missing = FAIL.
- **optional** = add if applicable data exists. Not counted toward pass/fail.
- **skip** = do not add for this content type.

---

## Enrichment Element Specifications

### Comparison Table
- 2-4 options in columns, header row, alternating row colours (#F5F5F5 / white)
- Winner column where applicable (bold + teal highlight)
- Data must be factual -- never fabricate feature comparisons

### Speed Tier Table
- Rows: 5Mbps, 20Mbps, 50Mbps, 100Mbps, 200Mbps, 1Gbps
- Columns: Speed, Best For, Devices, Activities
- Data must reflect real-world South African usage patterns

### Stat Callout Box
- Large stat number + label underneath
- Max 2 per page
- Teal #028090 accent border/background
- ONLY verified stats allowed:
  - "130K+ SADV subscribers"
  - "Netflix/Google/Meta peering"
  - "Maziv Group infrastructure"
  - Stats directly from infinifi.co.za
- Never fabricate or estimate statistics

### Step-by-Step Block
- Numbered steps with bold action verb title + 1-3 sentence explanation
- Must map 1:1 to HowTo schema steps if they exist (geo-optimizer adds schema, you add visual block)
- Clear sequential flow

### Pros/Cons Table
- Green checkmark / red X icons
- Max 6 items per column
- Honest assessment -- do not fabricate pros or hide real cons
- Both columns should have substantive entries

### Key Takeaway Box
- Teal #028090 border box positioned after intro
- "In This Guide:" header + 5 bullet preview of what the reader will learn
- Also use "Expert Tip" variant callouts mid-article where valuable insights exist
- Max 3 Expert Tip callouts per article

### Coverage Area Table
- Columns: Suburb, Status (Available / Coming Soon), Nearest Coverage
- ONLY use verified coverage data from infinifi.co.za/coverage
- Never fabricate suburb availability
- Include a note: "Coverage data as of [date]. Check infinifi.co.za/coverage for latest."

### Package Comparison Widget
- Columns: Package Name, Speed, Price, Best For, CTA button
- Teal #028090 CTA button styling
- Pull data from infinifi.co.za/deals
- Never fabricate pricing -- if price unknown, omit the widget
- Include note: "Prices as of [date]. Visit infinifi.co.za/deals for current pricing."

### Author + Trust Block
- "Written by Infini-Fi Team"
- Publish date + "Last Updated" date
- E-E-A-T trust signals: "Infini-Fi is part of the Maziv Group, South Africa's largest open-access fibre network operator."

---

## Output

### Enriched Content
- Markdown file with HTML enrichment elements embedded at appropriate positions
- All original content preserved
- Enrichment elements use templates from `references/enrichment-elements.md`

### Enrichment Manifest
JSON block appended as a comment or returned separately:

```json
{
  "file": "what-speed-do-i-need.md",
  "content_type": "educational_guide",
  "enrichment_level": "full",
  "elements_required": [
    "key_takeaway_box",
    "stat_callout_box",
    "comparison_table",
    "speed_tier_table",
    "step_block"
  ],
  "elements_added": [
    "key_takeaway_box",
    "stat_callout_box",
    "stat_callout_box",
    "comparison_table",
    "speed_tier_table",
    "step_block",
    "expert_tip_callout",
    "expert_tip_callout"
  ],
  "elements_skipped": [],
  "elements_skipped_reason": {},
  "enrichment_score": "5/5 required elements present",
  "verdict": "PASS",
  "optional_elements_added": ["expert_tip_callout x2"],
  "notes": []
}
```

### Scoring
- Count required elements for the content_type (from the matrix above)
- Count how many required elements were successfully added
- All required elements present = **PASS**
- Any required element missing = **FAIL** (with reason per missing element)
- Optional elements do not affect pass/fail but are reported in manifest

---

## DRY Rules -- Pipeline Boundary Enforcement

This skill is Stage 4 of 6. Respect the pipeline boundaries:

| Responsibility | Handled By | NOT This Skill |
|---------------|------------|----------------|
| Content quality scoring | infinifi-content-auditor (Stage 1) | Do not score content quality |
| SEO keyword optimisation | seo-content-writer (Stage 2) | Do not adjust keyword density |
| FAQ schema markup | geo-optimizer (Stage 3) | Do not add FAQ schema |
| HowTo schema markup | geo-optimizer (Stage 3) | Do not add HowTo schema |
| Brand voice enforcement | brand-voice-enforcer | Do not check banned words |
| CTA placement and copy | cro-optimizer (Stage 5) | Do not add CTAs |
| Final publish gate | Stage 6 | Do not approve for publish |

If you detect issues that belong to another stage, note them in the manifest under `"notes"` but do NOT fix them.

---

## InfiniFi Context

### Brand
- **Brand colours:** teal #028090, navy #0D2137, white #FFFFFF
- **Company:** Infini-Fi, a South African home fibre ISP
- **Parent:** Part of Maziv Group / SADV (South African Digital Villages)
- **Website:** infinifi.co.za

### Verified Stats (use ONLY these)
- 130K+ SADV subscribers
- Netflix/Google/Meta peering
- Maziv Group infrastructure (South Africa's largest open-access fibre network)
- Any stat directly pulled from infinifi.co.za

### Data Rules
- Package pricing: MUST match infinifi.co.za/deals -- never fabricate
- Coverage data: MUST match infinifi.co.za/coverage -- never fabricate
- Speed tiers: use standard SA fibre tiers (5/20/50/100/200/1000 Mbps)
- Tone: educational enrichments, not sales material

---

## Edge Cases

| Scenario | Handling |
|----------|----------|
| Content has no H2 sections | Add Key Takeaway box after first paragraph only. Note in manifest. |
| No verifiable stats available | Skip Stat Callout Box entirely. Note in manifest: "No verified stats applicable to this topic." |
| Coverage data unknown for area | Skip Coverage Area Table. Note in manifest: "Coverage data not verified for this area." |
| Content is FAQ-only | Minimal enrichment: Author + Trust Block only (if blog_post). Note in manifest. |
| File not found | Return FILE_NOT_FOUND error with path suggestion. |
| Content already has enrichment elements | Detect existing HTML enrichment blocks. Skip duplicates. Note in manifest: "Pre-existing elements detected: [list]." |
| Price data unavailable | Skip Package Widget. Note: "Package pricing not verified -- omitting widget." |
| enrichment_level = minimal | Add only Key Takeaway Box + Author Block (if blog_post). All other elements skipped. |

---

## Examples

### PASS Example

**Input:** `outputs/infinifi/guides/what-speed-do-i-need.md` (educational_guide, full enrichment)

**Required elements for educational_guide:** Key Takeaway Box, Stat Callout Box, Comparison Table, Speed Tier Table, Step Block (if how-to)

**Output (excerpt -- Key Takeaway Box after intro):**

```html
<div style="border-left: 4px solid #028090; background: #f0fafa; padding: 16px 20px; margin: 24px 0; border-radius: 0 8px 8px 0;">
  <strong style="color: #0D2137; font-size: 1.1em;">In This Guide:</strong>
  <ul style="margin: 8px 0 0 0; padding-left: 20px; color: #333;">
    <li>How fibre speed is measured and what Mbps means in practice</li>
    <li>Which speed tier matches your household size and usage</li>
    <li>Side-by-side comparison of 5Mbps to 1Gbps plans</li>
    <li>How to check what speeds are available at your address</li>
    <li>When to upgrade and signs your current speed isn't enough</li>
  </ul>
</div>
```

**Output (excerpt -- Speed Tier Table):**

```html
<table style="width: 100%; border-collapse: collapse; margin: 24px 0; font-family: sans-serif;">
  <thead>
    <tr style="background: #028090; color: white;">
      <th style="padding: 12px 16px; text-align: left;">Speed</th>
      <th style="padding: 12px 16px; text-align: left;">Best For</th>
      <th style="padding: 12px 16px; text-align: center;">Devices</th>
      <th style="padding: 12px 16px; text-align: left;">Activities</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; font-weight: bold;">5 Mbps</td>
      <td style="padding: 12px 16px;">1 person, light use</td>
      <td style="padding: 12px 16px; text-align: center;">1-2</td>
      <td style="padding: 12px 16px;">Email, browsing, SD streaming</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; font-weight: bold;">20 Mbps</td>
      <td style="padding: 12px 16px;">Small household</td>
      <td style="padding: 12px 16px; text-align: center;">3-5</td>
      <td style="padding: 12px 16px;">HD streaming, video calls, social media</td>
    </tr>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; font-weight: bold;">50 Mbps</td>
      <td style="padding: 12px 16px;">Medium household</td>
      <td style="padding: 12px 16px; text-align: center;">5-8</td>
      <td style="padding: 12px 16px;">4K streaming, gaming, work from home</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; font-weight: bold;">100 Mbps</td>
      <td style="padding: 12px 16px;">Large household</td>
      <td style="padding: 12px 16px; text-align: center;">8-12</td>
      <td style="padding: 12px 16px;">Multiple 4K streams, large downloads, cloud backup</td>
    </tr>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; font-weight: bold;">200 Mbps</td>
      <td style="padding: 12px 16px;">Power users</td>
      <td style="padding: 12px 16px; text-align: center;">12-15</td>
      <td style="padding: 12px 16px;">Competitive gaming, 4K streaming + uploads, smart home</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; font-weight: bold;">1 Gbps</td>
      <td style="padding: 12px 16px;">No compromises</td>
      <td style="padding: 12px 16px; text-align: center;">15+</td>
      <td style="padding: 12px 16px;">Everything at once, future-proof, content creators</td>
    </tr>
  </tbody>
</table>
```

**Manifest:**

```json
{
  "file": "what-speed-do-i-need.md",
  "content_type": "educational_guide",
  "enrichment_level": "full",
  "elements_required": ["key_takeaway_box", "stat_callout_box", "comparison_table", "speed_tier_table"],
  "elements_added": ["key_takeaway_box", "stat_callout_box", "stat_callout_box", "comparison_table", "speed_tier_table", "expert_tip_callout", "expert_tip_callout"],
  "elements_skipped": [],
  "elements_skipped_reason": {},
  "enrichment_score": "4/4 required elements present",
  "verdict": "PASS",
  "optional_elements_added": ["expert_tip_callout x2"],
  "notes": []
}
```

---

### FAIL Example

**Input:** `outputs/infinifi/guides/fibre-vs-lte.md` (comparison_page, full enrichment)

**Required elements for comparison_page:** Key Takeaway Box, Comparison Table, Pros/Cons Table, Package Widget (if deals referenced)

**Result:** Comparison Table added, but Key Takeaway Box missing (no intro section detected), Pros/Cons Table missing (content only had feature list, not structured pros/cons), Package Widget skipped (no verified pricing available).

**Manifest:**

```json
{
  "file": "fibre-vs-lte.md",
  "content_type": "comparison_page",
  "enrichment_level": "full",
  "elements_required": ["key_takeaway_box", "comparison_table", "pros_cons_table", "package_widget"],
  "elements_added": ["comparison_table"],
  "elements_skipped": ["key_takeaway_box", "pros_cons_table", "package_widget"],
  "elements_skipped_reason": {
    "key_takeaway_box": "No intro section detected -- content starts directly with H2. Restructure needed.",
    "pros_cons_table": "Content has feature list but not structured as pros/cons. Manual restructure required before enrichment.",
    "package_widget": "No verified pricing available from infinifi.co.za/deals for this comparison."
  },
  "enrichment_score": "1/4 required elements present",
  "verdict": "FAIL",
  "optional_elements_added": [],
  "notes": [
    "Content needs intro paragraph before Key Takeaway Box can be inserted.",
    "Feature list in Section 3 should be restructured as pros/cons before re-running enrichment.",
    "Package pricing not available -- verify infinifi.co.za/deals or skip widget."
  ]
}
```

**Action:** Fix the content structure issues noted above, then re-run Stage 4 enrichment.
