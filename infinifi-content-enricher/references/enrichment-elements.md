# InfiniFi Content Enrichment Elements -- HTML/Markdown Templates

Reference templates for Stage 4 content enrichment. All templates use InfiniFi brand colours:
- Teal: `#028090`
- Navy: `#0D2137`
- White: `#FFFFFF`
- Light grey (alternating rows): `#F5F5F5`
- Light teal background: `#f0fafa`

---

## 1. Key Takeaway Box

Use after the introduction paragraph. Replace placeholder bullets with actual content preview.

```html
<div style="border-left: 4px solid #028090; background: #f0fafa; padding: 16px 20px; margin: 24px 0; border-radius: 0 8px 8px 0;">
  <strong style="color: #0D2137; font-size: 1.1em;">In This Guide:</strong>
  <ul style="margin: 8px 0 0 0; padding-left: 20px; color: #333;">
    <li>[Bullet 1 -- what the reader will learn]</li>
    <li>[Bullet 2]</li>
    <li>[Bullet 3]</li>
    <li>[Bullet 4]</li>
    <li>[Bullet 5]</li>
  </ul>
</div>
```

---

## 2. Expert Tip Callout

Use mid-article where a valuable insight exists. Max 3 per article.

```html
<div style="border-left: 4px solid #028090; background: #f0fafa; padding: 14px 18px; margin: 20px 0; border-radius: 0 8px 8px 0;">
  <strong style="color: #028090;">Expert Tip:</strong>
  <span style="color: #333;"> [Tip text -- one to two sentences of actionable advice.]</span>
</div>
```

---

## 3. Stat Callout Box

Use near relevant paragraphs. Max 2 per page. ONLY verified stats.

```html
<div style="background: #f0fafa; border: 1px solid #028090; border-radius: 8px; padding: 20px 24px; margin: 24px 0; text-align: center;">
  <div style="font-size: 2.2em; font-weight: bold; color: #028090; line-height: 1.2;">[STAT NUMBER]</div>
  <div style="font-size: 0.95em; color: #0D2137; margin-top: 4px;">[Stat label / description]</div>
</div>
```

**Verified stats only:**
- `130K+` -- SADV subscribers
- `Netflix/Google/Meta` -- direct peering partners
- `Maziv Group` -- South Africa's largest open-access fibre network

---

## 4. Comparison Table

Use when comparing 2-4 options. Alternating row colours. Bold the winner column if applicable.

```html
<table style="width: 100%; border-collapse: collapse; margin: 24px 0; font-family: sans-serif; border: 1px solid #e0e0e0;">
  <thead>
    <tr style="background: #028090; color: white;">
      <th style="padding: 12px 16px; text-align: left;">Feature</th>
      <th style="padding: 12px 16px; text-align: center;">[Option 1]</th>
      <th style="padding: 12px 16px; text-align: center;">[Option 2]</th>
      <th style="padding: 12px 16px; text-align: center;">[Option 3]</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; color: #0D2137;">[Feature 1]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; color: #0D2137;">[Feature 2]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
    </tr>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; color: #0D2137;">[Feature 3]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
      <td style="padding: 12px 16px; text-align: center;">[Value]</td>
    </tr>
  </tbody>
</table>
```

**Winner column variant** -- add this style to the winning column header and cells:
```
style="padding: 12px 16px; text-align: center; background: #e6f5f7; font-weight: bold;"
```

---

## 5. Speed Tier Table

Use for speed guides and comparisons. Fixed rows for SA fibre tiers.

```html
<table style="width: 100%; border-collapse: collapse; margin: 24px 0; font-family: sans-serif; border: 1px solid #e0e0e0;">
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
      <td style="padding: 12px 16px; font-weight: bold; color: #0D2137;">5 Mbps</td>
      <td style="padding: 12px 16px;">1 person, light use</td>
      <td style="padding: 12px 16px; text-align: center;">1-2</td>
      <td style="padding: 12px 16px;">Email, browsing, SD streaming</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; font-weight: bold; color: #0D2137;">20 Mbps</td>
      <td style="padding: 12px 16px;">Small household</td>
      <td style="padding: 12px 16px; text-align: center;">3-5</td>
      <td style="padding: 12px 16px;">HD streaming, video calls, social media</td>
    </tr>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; font-weight: bold; color: #0D2137;">50 Mbps</td>
      <td style="padding: 12px 16px;">Medium household</td>
      <td style="padding: 12px 16px; text-align: center;">5-8</td>
      <td style="padding: 12px 16px;">4K streaming, gaming, work from home</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; font-weight: bold; color: #0D2137;">100 Mbps</td>
      <td style="padding: 12px 16px;">Large household</td>
      <td style="padding: 12px 16px; text-align: center;">8-12</td>
      <td style="padding: 12px 16px;">Multiple 4K streams, large downloads, cloud backup</td>
    </tr>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; font-weight: bold; color: #0D2137;">200 Mbps</td>
      <td style="padding: 12px 16px;">Power users</td>
      <td style="padding: 12px 16px; text-align: center;">12-15</td>
      <td style="padding: 12px 16px;">Competitive gaming, 4K streaming + uploads, smart home</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; font-weight: bold; color: #0D2137;">1 Gbps</td>
      <td style="padding: 12px 16px;">No compromises</td>
      <td style="padding: 12px 16px; text-align: center;">15+</td>
      <td style="padding: 12px 16px;">Everything at once, future-proof, content creators</td>
    </tr>
  </tbody>
</table>
```

---

## 6. Step-by-Step Block

Use for how-to content. Must map 1:1 to HowTo schema steps (added by geo-optimizer).

```html
<div style="margin: 24px 0;">
  <div style="display: flex; align-items: flex-start; margin-bottom: 16px;">
    <div style="min-width: 36px; height: 36px; background: #028090; color: white; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 1.1em; margin-right: 14px; flex-shrink: 0;">1</div>
    <div>
      <strong style="color: #0D2137; font-size: 1.05em;">[Action Verb Title]</strong>
      <p style="margin: 4px 0 0 0; color: #444; line-height: 1.5;">[1-3 sentence explanation of this step.]</p>
    </div>
  </div>
  <div style="display: flex; align-items: flex-start; margin-bottom: 16px;">
    <div style="min-width: 36px; height: 36px; background: #028090; color: white; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 1.1em; margin-right: 14px; flex-shrink: 0;">2</div>
    <div>
      <strong style="color: #0D2137; font-size: 1.05em;">[Action Verb Title]</strong>
      <p style="margin: 4px 0 0 0; color: #444; line-height: 1.5;">[1-3 sentence explanation of this step.]</p>
    </div>
  </div>
  <div style="display: flex; align-items: flex-start; margin-bottom: 16px;">
    <div style="min-width: 36px; height: 36px; background: #028090; color: white; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 1.1em; margin-right: 14px; flex-shrink: 0;">3</div>
    <div>
      <strong style="color: #0D2137; font-size: 1.05em;">[Action Verb Title]</strong>
      <p style="margin: 4px 0 0 0; color: #444; line-height: 1.5;">[1-3 sentence explanation of this step.]</p>
    </div>
  </div>
</div>
```

---

## 7. Pros/Cons Table

Use for comparison pages. Green checkmarks / red X. Max 6 items per column.

```html
<div style="display: flex; gap: 16px; margin: 24px 0; flex-wrap: wrap;">
  <div style="flex: 1; min-width: 260px; border: 1px solid #e0e0e0; border-radius: 8px; overflow: hidden;">
    <div style="background: #028090; color: white; padding: 10px 16px; font-weight: bold; text-align: center;">Pros</div>
    <ul style="list-style: none; padding: 12px 16px; margin: 0;">
      <li style="padding: 6px 0; color: #333;"><span style="color: #2e7d32; margin-right: 8px;">&#10004;</span>[Pro 1]</li>
      <li style="padding: 6px 0; color: #333;"><span style="color: #2e7d32; margin-right: 8px;">&#10004;</span>[Pro 2]</li>
      <li style="padding: 6px 0; color: #333;"><span style="color: #2e7d32; margin-right: 8px;">&#10004;</span>[Pro 3]</li>
    </ul>
  </div>
  <div style="flex: 1; min-width: 260px; border: 1px solid #e0e0e0; border-radius: 8px; overflow: hidden;">
    <div style="background: #0D2137; color: white; padding: 10px 16px; font-weight: bold; text-align: center;">Cons</div>
    <ul style="list-style: none; padding: 12px 16px; margin: 0;">
      <li style="padding: 6px 0; color: #333;"><span style="color: #c62828; margin-right: 8px;">&#10008;</span>[Con 1]</li>
      <li style="padding: 6px 0; color: #333;"><span style="color: #c62828; margin-right: 8px;">&#10008;</span>[Con 2]</li>
      <li style="padding: 6px 0; color: #333;"><span style="color: #c62828; margin-right: 8px;">&#10008;</span>[Con 3]</li>
    </ul>
  </div>
</div>
```

---

## 8. Coverage Area Table

Use for area pages ONLY. Data MUST be verified from infinifi.co.za/coverage.

```html
<table style="width: 100%; border-collapse: collapse; margin: 24px 0; font-family: sans-serif; border: 1px solid #e0e0e0;">
  <thead>
    <tr style="background: #028090; color: white;">
      <th style="padding: 12px 16px; text-align: left;">Suburb</th>
      <th style="padding: 12px 16px; text-align: center;">Status</th>
      <th style="padding: 12px 16px; text-align: left;">Nearest Coverage</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background: #ffffff;">
      <td style="padding: 12px 16px; color: #0D2137;">[Suburb Name]</td>
      <td style="padding: 12px 16px; text-align: center;"><span style="background: #028090; color: white; padding: 2px 10px; border-radius: 12px; font-size: 0.85em;">Available</span></td>
      <td style="padding: 12px 16px;">--</td>
    </tr>
    <tr style="background: #F5F5F5;">
      <td style="padding: 12px 16px; color: #0D2137;">[Suburb Name]</td>
      <td style="padding: 12px 16px; text-align: center;"><span style="background: #FFA726; color: white; padding: 2px 10px; border-radius: 12px; font-size: 0.85em;">Coming Soon</span></td>
      <td style="padding: 12px 16px;">[Nearest available suburb]</td>
    </tr>
  </tbody>
</table>
<p style="font-size: 0.85em; color: #666; margin-top: 4px;">Coverage data as of [DATE]. Check <a href="https://infinifi.co.za/coverage" style="color: #028090;">infinifi.co.za/coverage</a> for the latest availability.</p>
```

---

## 9. Package Comparison Widget

Use when content references deals or pricing. Data MUST match infinifi.co.za/deals.

```html
<div style="display: flex; gap: 16px; margin: 24px 0; flex-wrap: wrap;">
  <div style="flex: 1; min-width: 220px; border: 1px solid #e0e0e0; border-radius: 8px; padding: 20px; text-align: center;">
    <div style="font-size: 1.1em; font-weight: bold; color: #0D2137;">[Package Name]</div>
    <div style="font-size: 2em; font-weight: bold; color: #028090; margin: 8px 0;">[Speed]</div>
    <div style="font-size: 1.3em; color: #0D2137; margin-bottom: 4px;">R[Price]/mo</div>
    <div style="font-size: 0.9em; color: #666; margin-bottom: 16px;">Best for: [use case]</div>
    <a href="https://infinifi.co.za/deals" style="display: inline-block; background: #028090; color: white; padding: 10px 24px; border-radius: 6px; text-decoration: none; font-weight: bold;">View Deal</a>
  </div>
  <div style="flex: 1; min-width: 220px; border: 1px solid #e0e0e0; border-radius: 8px; padding: 20px; text-align: center;">
    <div style="font-size: 1.1em; font-weight: bold; color: #0D2137;">[Package Name]</div>
    <div style="font-size: 2em; font-weight: bold; color: #028090; margin: 8px 0;">[Speed]</div>
    <div style="font-size: 1.3em; color: #0D2137; margin-bottom: 4px;">R[Price]/mo</div>
    <div style="font-size: 0.9em; color: #666; margin-bottom: 16px;">Best for: [use case]</div>
    <a href="https://infinifi.co.za/deals" style="display: inline-block; background: #028090; color: white; padding: 10px 24px; border-radius: 6px; text-decoration: none; font-weight: bold;">View Deal</a>
  </div>
</div>
<p style="font-size: 0.85em; color: #666; margin-top: 4px;">Prices as of [DATE]. Visit <a href="https://infinifi.co.za/deals" style="color: #028090;">infinifi.co.za/deals</a> for current pricing.</p>
```

---

## 10. Author + Trust Block

Use at the end of blog posts. E-E-A-T trust signals.

```html
<div style="border-top: 2px solid #028090; margin-top: 40px; padding-top: 20px; display: flex; align-items: flex-start; gap: 16px;">
  <div style="min-width: 48px; height: 48px; background: #028090; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-weight: bold; font-size: 1.2em; flex-shrink: 0;">IF</div>
  <div>
    <div style="font-weight: bold; color: #0D2137; font-size: 1.05em;">Written by Infini-Fi Team</div>
    <div style="color: #666; font-size: 0.9em; margin-top: 2px;">Published: [YYYY-MM-DD] | Last Updated: [YYYY-MM-DD]</div>
    <div style="color: #444; font-size: 0.9em; margin-top: 6px; line-height: 1.4;">Infini-Fi is part of the Maziv Group, South Africa's largest open-access fibre network operator, connecting over 130,000 SADV subscribers nationwide.</div>
  </div>
</div>
```

---

## Usage Notes

- All templates use inline styles for maximum compatibility across CMS platforms and email renders.
- Replace all `[placeholder]` values with actual content-specific data.
- Never fabricate stats, pricing, or coverage data. Use only verified information from infinifi.co.za.
- Templates can be combined freely within a single article -- just maintain logical reading order.
- The Key Takeaway Box should always appear first (after intro), Author Block should always appear last.
