---
updated: 2026-06-05
source: ACF Storybook foundations/color
stability: stable
---

# Color

## Summary

The ACF color system is fully token-driven using semantic variables that
auto-switch between light/dark mode and across themes. Never hardcode hex
values — always use `var(--token-name)`.

## Token namespaces

```
--smtc-* (shared/base)
  → --mai-smtc-* (MAI design)
    → --bing-smtc-* (Bing product)
      → --bing-static-* (SDL static)
```

Naming pattern: `--{prefix}-{layer}-{element}-{variant}-{state}`

## Token architecture

```
Base variables (internal only)
├── Bing/Root Token (225 items)    — All root values used in SERP
├── Bing/Responsive (43 items)     — Device control
├── Bing/Mode (316 items)          — Light and Dark mode control
└── Bing/Theme (31 items)          — Legacy accent color control
         │
         ▼
MAI Collection (consumer-facing)
├── SNR [consumer ready]           — Aligns to current code token JSON
├── fallback [fading out]          — Legacy ACF token value mapping
└── MAI value [consumer ready]     — Value directly from MAI design system
         │
         ▼
Partner tokens (70 items)          — Bing partner team extensions
```

## Background tokens

### Card backgrounds

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bing-smtc-background-card-on-primary-alt-rest` | #f8f4f1 | #232738 | Accent card (rest) |
| `--bing-smtc-background-card-on-primary-alt-hover` | #efeae7 | theme-dep | Accent card (hover) |
| `--smtc-background-card-on-primary-default-rest` | #ffffff | #1b1a19 | Neutral card (rest) |
| `--smtc-background-card-on-primary-default-hover` | #f5f5f5 | #262626 | Neutral card (hover) |
| `--smtc-background-card-on-secondary-default-rest` | #ffffff | #1b1a19 | Nested card |

### Page & container

| Token | Light | Dark | Use |
|---|---|---|---|
| `--smtc-background-web-page-primary` | #ffffff | rgba(27,26,25,1) | Page background |
| `--bing-smtc-background-container` | #ffffff | rgba(41,40,39,1) | Container |
| `--bing-smtc-background-container-alt` | rgba(0,0,0,0.03) | #3b3a39 | Container alt |

### Control backgrounds

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bing-smtc-background-ctrl-brand-rest` | #4f6bed | #d9dffb | Brand control |
| `--bing-smtc-background-ctrl-subtle-rest` | #f8f4f1 | #232738 | Subtle control |
| `--bing-smtc-background-ctrl-neutral-rest` | #d9dffb | #2c3459 | Neutral (soft btn) |
| `--smtc-background-ctrl-outline-rest` | #ffffff | #1b1a19 | Outline control |

### Status backgrounds

| Token | Light | Dark | Use |
|---|---|---|---|
| `--smtc-status-informative-tint-background` | #f5f5f5 | #262626 | Info tint |
| `--smtc-status-success-background` | #2c8147 | #2c8147 | Success solid |
| `--smtc-status-danger-background` | #d2393d | #d2393d | Danger solid |
| `--smtc-status-warning-background` | #b95700 | #b95700 | Warning solid |

## Foreground tokens

| Token | Light | Dark | Use |
|---|---|---|---|
| `--smtc-foreground-content-neutral-primary` | rgba(0,0,0,1) | rgba(255,255,255,1) | Primary text |
| `--smtc-foreground-content-neutral-secondary` | rgba(0,0,0,0.8) | rgba(255,255,255,0.8) | Body text |
| `--bing-smtc-foreground-content-neutral-tertiary` | rgba(0,0,0,0.6) | rgba(255,255,255,0.6) | Caption / meta |
| `--bing-smtc-foreground-content-brand-rest` | #4f6bed | #d9dffb | Brand / accent |
| `--smtc-ctrl-link-foreground-brand-rest` | #4007a2 | #82c7ff | Links |
| `--smtc-foreground-ctrl-on-brand-rest` | #ffffff | #3c51b4 | On brand surface |
| `--smtc-status-success-tint-foreground` | #006d21 | #60bd84 | Success text |
| `--smtc-status-danger-tint-foreground` | #c80000 | #ff6666 | Danger text |
| `--smtc-status-warning-tint-foreground` | #be5a00 | #ecc26e | Warning text |

## Stroke / divider tokens

| Token | Light | Dark | Use |
|---|---|---|---|
| `--smtc-stroke-divider-default` | rgba(0,0,0,0.10) | rgba(255,255,255,0.10) | Divider |
| `--smtc-stroke-divider-subtle` | rgba(0,0,0,0.08) | rgba(255,255,255,0.08) | Divider subtle |
| `--smtc-stroke-divider-strong` | rgba(0,0,0,0.20) | rgba(255,255,255,0.20) | Divider strong |
| `--smtc-stroke-card-on-primary-rest` | rgba(0,0,0,0.10) | rgba(255,255,255,0.10) | Neutral card border |
| `--bing-smtc-stroke-ctrl-default` | rgba(0,0,0,0.1) | rgba(255,255,255,0.1) | Control border |

## Card color rules

- **Accent cards**: use `--bing-smtc-background-card-on-primary-alt-*`. No border.
- **Neutral cards**: use `--smtc-background-card-on-primary-default-*`. Always apply
  `1px solid var(--smtc-stroke-card-on-primary-rest)` border.

## Common mistakes

| Scenario | Wrong | Correct |
|---|---|---|
| Accent card bg | `--smtc-background-card-on-primary-alt-rest` | `--bing-smtc-background-card-on-primary-alt-rest` |
| Neutral card bg | `--bing-smtc-background-card-on-primary-default-rest` | `--smtc-background-card-on-primary-default-rest` (no `bing-`) |
| Neutral card border | No border | `border: 1px solid var(--smtc-stroke-card-on-primary-rest)` |
| Text on brand button | `foreground/content/brand` | `foreground/ctrl/on-brand/rest` |
| Divider line | `stroke/ctrl/neutral/rest` | `stroke/divider/default` |

## Do / Don't

- **Do:** use semantic token variables — never hardcode hex.
- **Do:** pair foreground/primary with background/web-page or background/card for standard text.
- **Do:** use foreground/secondary for supporting metadata and footnotes.
- **Do:** use status tokens only for status-related UI (success, danger, warning).
- **Do:** provide fallback values: `var(--token, #fallback)`.
- **Do:** test all token pairs in both light and dark mode.
- **Don't:** hardcode hex values (#FFFFFF, #000000) — use tokens.
- **Don't:** mix `--bing` and `--smtc` namespaces for the same role.
- **Don't:** use foreground/primary on background/web-page without checking contrast.
- **Don't:** rely on color alone to convey meaning — pair with text or icon.
- **Don't:** repurpose status colors for decorative use.
- **Don't:** assume a token looks the same in all 4 themes.

## Accessibility

All foreground/background pairs must meet WCAG 2.1 AA contrast (4.5:1 for
text, 3:1 for large text). Status tokens are AA validated at the token
layer. Never rely on color alone to convey meaning.

## Dark mode

All semantic tokens auto-swap via `.dark` class on `<html>`. Dark accent
card background is theme-dependent (`#232738` for copilotNeutral). Never
hardcode dark hex values.

## Open questions

None.
