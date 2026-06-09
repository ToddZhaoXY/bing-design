---
updated: 2026-06-05
source: ACF Storybook foundations/spacing
stability: stable
---

# Spacing

## Summary

Spacing uses semantic `--smtc-gap-between-content-*` tokens that
automatically resolve to smaller values on mobile via `desktopMobileValue`.
Never hardcode pixel values — tokens auto-scale on mobile (~70–75% of desktop).

## Gap tokens

| Token | Desktop | Mobile | Use |
|---|---|---|---|
| `--smtc-gap-between-content-xx-small` | 4px | 3px | Micro: favicon-to-source, attribution lines |
| `--smtc-gap-between-content-x-small` | 8px | 6px | Default inner gap — structure body content |
| `--smtc-gap-between-content-small` | 12px | 9px | Between-content gap |
| `--smtc-gap-between-content-medium` | 16px | 12px | Smaller section gap, generous text gap |
| `--smtc-gap-between-content-x-large` | 24px | 16px | Section-level separation, between cards/modules |
| `--smtc-gap-between-content-xx-large` | 36px | 26px | Major section breaks |

## Content padding scale

| Token | Value |
|---|---|
| `--smtc-padding-content-xxx-small` | 2px |
| `--smtc-padding-content-xx-small` | 4px |
| `--smtc-padding-content-x-small` | 8px |
| `--smtc-padding-content-small` | 12px |
| `--smtc-padding-content-medium` | 16px |
| `--smtc-padding-content-large` | 20px |
| `--smtc-padding-content-x-large` | 24px |
| `--smtc-padding-content-xx-large` | 48px |
| `--smtc-padding-content-xxx-large` | 80px |

## Card padding tokens

| Token | Value | Use |
|---|---|---|
| `--mai-smtc-padding-card-default` | 20px | Card internal padding |
| `--mai-smtc-padding-card-nested-default` | 12px | Nested card padding |
| `--mai-smtc-padding-card-nested-xs-default` | 8px | Compact nested card |
| `--mai-smtc-padding-list-card-default` | 8px | List card padding |

## Control & component spacing

| Token | Value | Use |
|---|---|---|
| `--smtc-padding-ctrl-horizontal-default` | 12px | Default control horizontal padding (md) |
| `--smtc-padding-ctrl-sm-horizontal-default` | 8px | Small control horizontal padding |
| `--smtc-padding-ctrl-lg-horizontal-default` | 16px | Large control horizontal padding |
| `--smtc-padding-ctrl-text-side` | 2px | Label text-side padding inside controls |
| `--smtc-ctrl-badge-padding` | 8px | Badge horizontal padding (md) |
| `--smtc-ctrl-badge-sm-padding` | 4px | Badge horizontal padding (sm) |
| `--smtc-gap-inside-ctrl-to-secondary-icon` | 4px | Icon-to-label gap inside controls |
| `--smtc-gap-inside-ctrl-lg-to-secondary-icon` | 6px | Icon-to-label gap (large controls) |

## Page-level spacing

| Element | Value | Breakpoint |
|---|---|---|
| Body padding (XL ≥1392px) | `clamp(48px, calc(50cqi - 600px), 160px)` | Fluid 48–160px |
| Body padding (L 1025–1391px) | `clamp(48px, calc(13cqi - 85px), 96px)` | Fluid 48–96px |
| Body padding (M ≤1024px) | 36px fixed | — |
| Body padding (S ≤640px) | 24px fixed | — |
| Body gap (desktop) | 36px | Between sections |
| Body gap (mobile) | 24px | ≤640px |
| Grid gutter | 24px | All breakpoints |

## Decision guide

| Spacing need | Token |
|---|---|
| Between sections / cards / modules | x-large (24px) |
| Smaller section gap, generous text gap | medium (16px) |
| Between content elements (default) | x-small (8px) |
| Dense layouts, attribution lines | xx-small (4px) |
| Between related items | small (12px) |

## Do / Don't

- **Do:** always use gap/padding tokens — never hardcode pixels.
- **Do:** use `x-small` (8px) as the default inner gap.
- **Do:** use `x-large` (24px) between cards/sections.
- **Do:** let tokens auto-scale on mobile — no manual overrides needed.
- **Don't:** hardcode `margin: 16px` — use `var(--smtc-gap-between-content-medium)`.
- **Don't:** use large spacing for closely-related items.
- **Don't:** mix gap and padding for the same spacing role.
- **Don't:** override mobile token values manually.

## Open questions

None.
