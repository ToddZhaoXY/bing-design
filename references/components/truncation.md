---
updated: 2026-06-30
source: ACF Storybook content update report 2026-06-30
stability: beta
---

# Truncation

**Figma Node ID:** `20492:9956` · **Group:** Display · **Tier:** Dependency · **Variants:** 4 · **Dependencies:** Focus outline · **Consumed by:** Card components, text content areas within card body elements

## Summary

Truncation is a text overflow indicator and control component. It is an internal dependency inside Card Body Elements, appearing at the end of overflowing card content as a "Continue reading →" navigation link. The 4 variants cover the interaction states of this navigation link.

Note: The current Storybook guidance treats the trigger as a navigation link that opens the full source page in a new browser tab, not as inline expansion. If a consumer uses an expand/collapse truncation pattern, expanded content must reflow inside its container and be re-collapsible.

This component is appropriate when text content may exceed available space (card descriptions, answer text) and users should be able to navigate to the full source. It is not for section-level expand/collapse (use Section Footer "Expansion" action) or when text should always be fully visible.

---

## Variants / States

| state | Description |
|-------|-------------|
| **rest** (default) | Link is visible; no hover treatment |
| **hover** | Link shows hover state styling |
| **pressed** | Active click/tap in progress |
| **focus** | Keyboard focus ring visible on the link |

---

## Anatomy

1. **Navigation link** — "Continue reading →" text link; opens the full source detail page in a new tab

---

## Visual States

The 4 variants represent the 4 interaction states of the "Continue reading →" navigation link. The component is a text link with standard link styling, positioned after the ellipsis that clips the card content.

---

## Usage Rules

- Truncation is placed at the end of the card body text, after the ellipsis ('…') that clips the content.
- The trigger ("Continue reading →") opens the full source page in a **new tab** — it does NOT expand text inline.
- Truncation stacks vertically within the card body with no extra spacing gap.
- Card body spacing tokens are followed — Truncation itself does not add additional padding.
- The card body may continue below the Truncation component (e.g., source attribution row).
- Truncation occurs at a maximum line count that preserves meaning (typically 2–3 lines).
- Truncation occurs at natural word boundaries — never mid-word.
- Titles are not truncated — titles are generally fully visible.
- Critical information is kept in the visible (non-truncated) portion.
- Max visible lines may change across breakpoints (e.g., 3 lines desktop → 2 lines mobile).
- Expanded content, when used, must reflow properly within its container and should not push critical mobile content excessively below the fold.

---

## Do / Don't

### Do
- Truncate at a maximum line count that preserves meaning (typically 2–3 lines).
- Make truncation feel deliberate — the ellipsis should suggest "more content available."
- Keep the most important information in the visible (non-truncated) portion.
- Make navigation-link behavior explicit to assistive technology (for example, "opens in new tab").
- Ensure expanded text is re-collapsible if the consumer uses an expand/collapse truncation pattern.

### Don't
- Don't truncate titles — they should generally be fully visible.
- Don't truncate text mid-word — cut at word boundaries.
- Don't hide critical information behind truncation with no navigation option.
- Don't use truncation as a lazy layout fix — design for the expected content volume.

---

## Dark Mode Notes

Navigation link text must meet WCAG AA contrast in both light and dark themes. The link is visually distinct as an interactive element (color, underline on hover) in both themes.

---

## Related Components

| Component | Relationship |
|-----------|-------------|
| **Card body elements** | Parent — Truncation is a dependency inside card body templates, shown at the end of the card |
| **Section / footer** | Related — section-level expand/collapse uses a different pattern (inline expand, not new-tab navigation) |

---

## Open questions

None.
