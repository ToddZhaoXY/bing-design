---
updated: 2026-06-05
source: ACF Storybook foundations/shape
stability: stable
---

# Corner Radius

## Summary

Corner radius is determined by usage first, element size second. All radii
use dedicated semantic tokens from the MAI corner collection. Tokens auto-scale
on mobile (responsive values noted below). Never hardcode pixel values.

## Hierarchy principle

| Value | Use |
|---|---|
| 4px | Small controls, checkboxes, list items, favicons |
| 8px | Standard controls (buttons, inputs, badges, flyouts) |
| 16px | Large controls, popovers, extra-large controls |
| 24px | Cards and major containers |
| 9999px | Circular (pills, avatars, full-round) |

## Token reference

### Card & container

| Token | Value | Responsive | Use |
|---|---|---|---|
| `--mai-smtc-corner-card-default` | 24px | 24 → 24 | Cards, major containers |
| `--mai-smtc-corner-list-card-default` | 8px | 8 → 6 | List card surfaces |

### Control (standard)

| Token | Value | Responsive | Use |
|---|---|---|---|
| `--smtc-corner-ctrl-rest` | 8px | 8 → 6 | Control at rest |
| `--smtc-corner-ctrl-hover` | 8px | 8 → 6 | Control on hover |
| `--smtc-corner-ctrl-pressed` | 8px | 8 → 6 | Control when pressed |

### Control (small)

| Token | Value | Responsive | Use |
|---|---|---|---|
| `--smtc-corner-ctrl-sm-rest` | 4px | 4 → 3 | Small control at rest |
| `--smtc-corner-ctrl-sm-hover` | 4px | 4 → 3 | Small control on hover |
| `--smtc-corner-ctrl-sm-pressed` | 4px | 4 → 3 | Small control when pressed |
| `--smtc-ctrl-badge-corner` | 8px | 8 → 6 | Badge (md) |
| `--smtc-ctrl-badge-sm-corner` | 4px | 4 → 3 | Badge (sm) |
| `--smtc-ctrl-choice-checkbox-corner` | 4px | 4 → 3 | Checkbox |
| `--smtc-ctrl-list-corner-rest` | 4px | 4 → 3 | List item at rest |
| `--smtc-ctrl-list-corner-hover` | 4px | 4 → 3 | List item on hover |
| `--smtc-ctrl-list-corner-pressed` | 4px | 4 → 3 | List item when pressed |
| `--mai-smtc-corner-favicon` | 4px | 4 → 3 | Favicon thumbnail |

### Control (large)

| Token | Value | Responsive | Use |
|---|---|---|---|
| `--mai-smtc-corner-ctrl-xlg-rest` | 16px | 16 → 12 | Extra-large control |
| `--smtc-corner-ctrl-lg-rest` | 8px | 8 → 6 | Large control at rest |
| `--smtc-corner-ctrl-lg-hover` | 8px | 8 → 6 | Large control on hover |
| `--smtc-corner-ctrl-lg-pressed` | 8px | 8 → 6 | Large control when pressed |

### Flyout & popover

| Token | Value | Responsive | Use |
|---|---|---|---|
| `--smtc-corner-flyout-rest` | 8px | 8 → 6 | Flyout panel |
| `--bing-smtc-corner-flyout-popover-rest` | 16px | 16 → 12 | Popover container |

### Special

| Token | Value | Use |
|---|---|---|
| `--smtc-corner-circular` | 9999px | Pills, avatars, full-round |
| `--bing-ads-smtc-ad-slug-corner` | 6px | Ad slug badge |

## Decision guide

**Step 1:** Does a dedicated token exist?
- Card → `corner-card-default` (24px)
- Control → `corner-ctrl-rest` (8px)
- Pill → `corner-circular` (9999px)

**Step 2:** Where is the element?
- Outer (on page) → use `ctrl-xlg` or `ctrl-lg`
- Inner (inside card) → use `ctrl` or `ctrl-sm`

**Step 3:** What size?
- 88px+ → `ctrl-xlg`
- Medium → `ctrl-lg`
- >21px → `ctrl`
- ≤20px → `ctrl-sm`

## Common mistakes

| Mistake | Fix |
|---|---|
| Hardcode `border-radius: 8px` | Use `var(--smtc-corner-ctrl-rest, 8px)` |
| Use card radius (24px) for small controls | Use `ctrl-sm` (4px) or `ctrl` (8px) |
| Use control radius for card containers | Use `corner-card-default` (24px) |
| Forget circular for pills/avatars | Use `corner-circular` (9999px) |
| Skip state tokens on interactive elements | Use rest/hover/pressed variants |

## Do / Don't

- **Do:** check for a dedicated token first (card, badge, pill).
- **Do:** use inner vs outer tokens based on nesting depth.
- **Do:** use state tokens (rest/hover/pressed) for interactive elements.
- **Do:** let tokens auto-scale on mobile — no manual overrides.
- **Don't:** hardcode border-radius — use tokens.
- **Don't:** use card radius (24px) for small controls.
- **Don't:** use control radius (8px) for cards.
- **Don't:** forget circular token for pills/avatars.

## Accessibility

Focus rings inherit the element's border-radius — ensure they remain visible.
Circular elements (pills, avatars) should maintain minimum touch target (44×44px).

## Open questions

None.
