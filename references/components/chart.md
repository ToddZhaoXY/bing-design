---
updated: 2026-06-30
source: ACF Storybook content update report 2026-06-30
stability: beta
---

# Chart

**Figma Node ID:** `144696:24051` · **Type:** `COMPONENT_SET` · **Group:** Display · **Tier:** Composite / Assembly · **Variants:** 4

## Summary

Chart is a composite display component for lightweight data visualization inside SERP cards and card body templates. It provides standardized chart assemblies so data-heavy answer cards can communicate trends, proportions, progress, or comparisons without inventing custom visuals.

Chart is appropriate when a card needs a compact visual summary of structured data, when the visual helps users compare values faster than reading text, or when a Card Body Elements template calls for a chart slot. It is not appropriate for decorative visuals, dense analytics dashboards, or data that cannot be understood at card scale.

---

## Variants / Types

The Storybook update identifies Chart as a 4-variant component set. The exact Figma variant labels should be treated as source-owned, but the supported chart patterns map to the data-visualization templates already exposed in Card Body Elements:

| Pattern | Use |
|---|---|
| Gauge / radial value | Single metric against a target or threshold |
| Donut / proportion | Part-to-whole comparison with a small number of categories |
| Range bar | Value within a bounded interval |
| Line / bar trend | Compact trend or category comparison |

---

## Anatomy

1. **Chart visual** — The data mark area: gauge, ring, bar, line, or comparable visualization.
2. **Value label** — Primary number or status the chart represents.
3. **Context label** — Short descriptor, unit, or category label.
4. **Container** — Slot-aware assembly that inherits card spacing and color tokens from its parent.

---

## Usage Rules

- Use Chart only when the visual adds comprehension beyond the text label.
- Keep chart data simple enough to be legible inside a card. Prefer one primary takeaway over dense multi-series data.
- Pair charts with text labels; do not rely on color alone to communicate meaning.
- Use semantic color tokens and data-color tokens where available. Do not hardcode chart colors.
- Place charts inside a card body or chart-capable template; do not use them as standalone page structure.
- Ensure the chart responds to the parent card slot and does not force card height or width.

---

## Do / Don't

### Do

- Use charts for compact answer summaries, progress, proportions, or comparisons.
- Label the represented metric clearly.
- Preserve sufficient contrast in both light and dark themes.
- Provide a textual equivalent for accessibility.

### Don't

- Don't use charts as decorative art.
- Don't pack dense dashboards into a SERP card.
- Don't use color as the only differentiator between data series.
- Don't override the parent card's tokenized spacing, typography, or surface colors.

---

## Dark Mode Notes

Chart colors must resolve through theme-aware semantic or data-color tokens. Axis, label, and value text must meet WCAG AA contrast in both light and dark themes.

---

## Related Components

| Component | Relationship |
|---|---|
| **Card Body Elements** | Provides chart templates that may consume Chart patterns |
| **Answer Card** | Common parent card for chart-based answers |
| **Label** | Supplies text labels and values around the chart |
| **Splits / structured data patterns** | Use structured text/table patterns when chart density would be too high |

---

## Open questions

- Confirm the exact 4 Figma variant labels and whether each maps directly to the chart patterns listed above.
