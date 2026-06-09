---
updated: 2026-06-05
source: ACF Storybook foundations/elevation
stability: stable
---

# Elevation

## Summary

Elevation uses shadow tokens to create visual depth hierarchy. Cards at
rest are flat (Level 0); hover lifts to Level 1. Higher levels are for
overlays and system UI. Use shadow tokens — never hardcode `box-shadow`.

## Shadow tokens

| Level | Token | Use |
|---|---|---|
| 0 — Card rest | `--smtc-shadows-card` | Cards at rest, page content |
| 1 — Card hover (light) | `--bing-smtc-shadows-card-hover-1` | Card hover, subtle lift |
| 1 — Card hover (strong) | `--bing-smtc-shadows-card-hover-3` | Card hover, prominent lift |
| 2 — Flyout | `--smtc-shadows-flyout` | Flyout, dropdown, tooltip, menu |
| 3 — Overlay | `--bing-smtc-shadows-overlay` | Overlay, modal, drawer |

### Specialized shadows

| Token | Use |
|---|---|
| `--smtc-shadows-button-brand` | Solid primary button |
| `--smtc-shadows-button-neutral` | Soft, outline, secondary buttons (inner shine) |
| `--smtc-shadows-tooltip` | Tooltip bubble |
| `--smtc-shadows-avatar` | Avatar image |

### Search box shadows

| State | Token |
|---|---|
| Rest | `--bing-smtc-shadows-search-box-rest` |
| Hover | `--bing-smtc-shadows-search-box-hover` |
| Active | `--bing-smtc-shadows-search-box-active` |

## Component → elevation mapping

| Component | Level | Notes |
|---|---|---|
| Card (rest) | 0 | No shadow — relies on background color or subtle border |
| Card (hover) | 1 | Subtle lift on interaction |
| Flyout | 2 | Panel hovering over content |
| Dropdown | 2 | Selection panel |
| Tooltip | 2 | Floating info bubble |
| Menu | 2 | Contextual menu panel |
| Overlay / Modal | 3 | Full overlay dialog |
| Drawer | 3 | Side panel |
| Toast | 4 | Top-priority notification |

## Z-index guidance

| Layer | Z-Index | Elements |
|---|---|---|
| Content | 0 | Cards, sections, body content |
| Dropdown | 100 | Dropdown panels, menus, flyouts |
| Overlay backdrop | 200 | Dimming layer behind modal |
| Overlay / Modal | 300 | Dialog content, Drawer |
| Toast | 400 | Notification toasts |

## Do / Don't

- **Do:** use shadow tokens — never hardcode `box-shadow` values.
- **Do:** apply card hover shadow only on interactive cards.
- **Do:** use the inner-shine token for material-style buttons.
- **Do:** test shadows in both light and dark mode.
- **Don't:** add shadows to rest-state cards (use stroke instead).
- **Don't:** use overlay-level shadows on inline elements.
- **Don't:** hardcode dark mode shadow values — they auto-switch.
- **Don't:** stack multiple shadow tokens on one element.

## Dark mode

Shadow tokens auto-switch via `.dark` class. Dark mode shadows are
typically more subtle (reduced opacity) since dark backgrounds already
imply depth. The neutral button inner-shine switches from white inset to
reduced-opacity white inset. Search box shadows drop the warm amber glow
in dark mode.

## Open questions

None.
