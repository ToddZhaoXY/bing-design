---
updated: 2026-06-05
source: ACF Storybook foundations/visual-quality
stability: stable
---

# Visual Quality Checklist

## Summary

QA rubric for evaluating ACF component and card designs across 3
categories and 31 dimensions. Scoring: Pass / Fail per dimension. All
designs must pass in both light and dark mode.

---

## Structure (11 dimensions)

| # | Dimension | Pass | Fail |
|---|---|---|---|
| 1 | Grid Fidelity | Layout stays true to assigned grid spans across breakpoints | Content stretches, clips, or shifts off-grid |
| 2 | Balance | Content distributes evenly; visually stable at a glance | Sections look cramped or whitespace dominates |
| 3 | Alignment | Text, imagery, icons align on grid and baseline | Elements float, misalign, or break baseline rhythm |
| 4 | Theme Cohesion | Background follows palette, reinforces unified content | Background strays from palette or distracts |
| 5 | Contrast | Text/UI legible under all backgrounds (AA level) | Text blends into background, washed out |
| 6 | Imagery Treatment | Full-bleed images maintain aspect ratio | Images stretch, pixelate, or crop key subjects |
| 7 | Typography Hierarchy | Headline, subtext, metadata clearly distinguished | Styles collapse, unclear primary vs secondary |
| 8 | Readability | Font sizes maintain hierarchy, proportional line height | Sizes collapse, tight line height, uneven wrapping |
| 9 | Consistency | Font weights/sizes scale proportionally across cards | Mismatched size/weight, responsive scaling breaks |
| 10 | Content Hierarchy | Primary/secondary/supplementary tiers visually clear | Users can't distinguish what's most important |
| 11 | Content Truncation | Truncation feels deliberate, doesn't obscure meaning | Cropping breaks readability or hides critical info |

## Expression (10 dimensions)

| # | Dimension | Pass | Fail |
|---|---|---|---|
| 12 | Image Quality | Crisp, high-res, no pixelation on any device | Blurry, pixelated, compressed |
| 13 | Framing | Key focal points intact across crops | Important subjects cut off or awkwardly positioned |
| 14 | Image Harmony | Tone complements card's palette and purpose | Color grading clashes or makes text hard to read |
| 15 | Color Harmony | Accents, neutrals, surfaces feel cohesive | Colors compete, uneven contrast |
| 16 | Accents | Highlights guide focus subtly | Accent colors dominate or pull from content |
| 17 | Mood | Tone matches intent (informative, celebratory, etc.) | Wrong emotional cue |
| 18 | Icon Consistency | All icons share visual weight and style | Icons differ in weight, stroke, or style |
| 19 | Icon Purpose | Decorative elements enhance clarity | Patterns/borders distract from content |
| 20 | Icon Meaning | Icons accurately support content/actions | Mismatched, vague, or unclear |
| 21 | Localization | Translated content fits without truncation | Overflow, misalignment, or tone mismatch |

## Craft & Interaction (10 dimensions)

| # | Dimension | Pass | Fail |
|---|---|---|---|
| 22 | Density | Content well-paced and balanced | Visually heavy, chaotic, or large voids |
| 23 | Whitespace | Content never cramped or scattered | Uneven, inconsistent, elements merge |
| 24 | Flow | Scan path predictable, headline → metadata | Confusing, forces users to jump around |
| 25 | Feedback | Hover/click states distinct and purposeful | Too subtle or overly aggressive |
| 26 | Affordance | Users intuit where to click | Can't distinguish static vs interactive |
| 27 | Contrast (A11y) | Readability holds in light and dark modes | Below AA standards or relies solely on color |
| 28 | Focus Indicators | Visible but unobtrusive keyboard focus | Missing, overly bright, or misaligned |
| 29 | A11y Readiness | Alt text, semantic structure, ARIA roles | Non-visual users can't access content |
| 30 | Loading States | Smooth skeleton screens, consistent feedback | Missing, abrupt, or visually jarring |
| 31 | Error States | Error messages clear, integrated with card style | Broken layouts or confusing gaps |

---

## Card variant requirement

All designs must provide two layouts for the same query intent:

- **Anchor Card** — primary, large-sized card in answer experiences.
  Should be ready for resizing/trimming (wider <-> narrower).
- **Accessory Card** — smaller, supporting card. Should consider medium +
  small sizes with responsive-friendly design.

## Accessibility standard

WCAG AA is the baseline requirement:
- Contrast ratios must meet AA for text and key UI elements
- Focus indicators must be visible without visual noise
- Screen reader compatibility required (alt text, semantic structure, ARIA)
- Don't rely solely on color to convey meaning

## Open questions

None.
