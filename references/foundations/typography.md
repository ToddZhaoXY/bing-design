---
updated: 2026-06-05
source: ACF Storybook foundations/typography
stability: stable
---

# Typography

## Summary

All text uses `--bing-smtc-text-global-*` shorthand tokens. The token
embeds font-style, weight, size/line-height, and family in one declaration
— always use `font: var(--bing-smtc-text-global-*)`, never set individual
properties. Body/3 (14px/22) is the default body size across the product.

## Font families

The token `--bing-smtc-text-style-default-regular-font-family` resolves
to different stacks per variant. ACF currently uses **variant04**.

| Variant | Font Stack | Use |
|---|---|---|
| default | Arial, Helvetica, Sans-Serif | Figma design rendering |
| mobile | "-apple-system", HelveticaNeue, Roboto, Arial, sans-serif | Mobile platforms |
| variant01 | "Amazon Ember", "Helvetica Neue", Helvetica, Arial, Sans-Serif | Amazon partner |
| variant02 | system-ui, sans-serif | System UI fallback |
| variant03 | "Segoe Sans Edge Text", Roboto, Helvetica, Sans-Serif | Edge browser |
| **variant04** | **Roboto, Helvetica, Sans-Serif** | **Current ACF default** |
| variant05 | "Segoe Sans Variable", Roboto, Helvetica, Sans-Serif | Segoe Sans flighting |

Segoe Sans is currently flighting as a replacement for the default font
family (variant05).

## Type scale

5 groups: display (2), title (3), subtitle (4), body (6), caption (4) = 19 styles.
All live under `--bing-smtc-text-global`.

### Display

| Token | Size/LH | Weight | Use |
|---|---|---|---|
| `display/1` | 54/64 | 700 | Hero display, single entity |
| `display/2` | 40/48 | 700 | Single entity |

### Title

| Token | Size/LH | Weight | Use |
|---|---|---|---|
| `title/1` | 36/48 | 700 | Page titles, single entity |
| `title/2` | 24/32 | 400 | Card titles, section headers |
| `title/2-strong` | 24/32 | 700 | Emphasized card titles, QuickFact |

### Subtitle

| Token | Size/LH | Weight | Use |
|---|---|---|---|
| `subtitle/1` | 20/26 | 400 | Whole page title, section title |
| `subtitle/1-strong` | 20/26 | 700 | Emphasized section title |
| `subtitle/2` | 18/22 | 400 | Algo title, sub-section |
| `subtitle/2-strong` | 18/22 | 700 | Answer section title |

### Body

| Token | Size/LH | Weight | Use |
|---|---|---|---|
| `body/1` | 18/28 | 400 | Single-answer body text outside a card |
| `body/1-strong` | 18/28 | 700 | Body emphasis/keywords, inline links |
| `body/2` | 16/26 | 400 | Short answer text in less-dense layouts |
| `body/2-strong` | 16/26 | 700 | Short answer emphasis, accent fact |
| `body/3` | 14/22 | 400 | **Default body text across the product** |
| `body/3-strong` | 14/22 | 700 | Default card title, keywords |

### Caption

| Token | Size/LH | Weight | Use |
|---|---|---|---|
| `caption/1` | 13/20 | 400 | Metadata, attribution, disclaimer |
| `caption/1-strong` | 13/20 | 700 | Item label, subtitle highlight |
| `caption/2` | 11/13 | 400 | Badge label, micro labels |
| `caption/2-strong` | 11/13 | 700 | Emphasized badge label |

## Card typography map

Canonical token usage for answer cards.

| Element | Typography | Color |
|---|---|---|
| Card title | body/3-strong | neutral/primary |
| Card body | body/3 | neutral/secondary |
| Card attribution | caption/2 | neutral/tertiary |
| List item label | caption/1 | neutral/secondary |
| Horizontal item title | caption/1-strong | neutral/primary |
| Video/image title | body/3-strong | neutral/primary |
| Row item title | body/3-strong | neutral/primary |
| Inline link | (inherits) | brand/rest |

## Body size decision guide

| Token | When to use |
|---|---|
| `body/3` | Standard body text — the baseline for most content |
| `body/3-strong` | Card titles, highlighted keywords, list titles |
| `body/2` | Short answers in less-dense card layouts |
| `body/1` | Single-answer experiences where one response needs to stand out |
| `body/1-strong` | Emphasis within body/1 text, commonly with inline hyperlinks |

## Do / Don't

- **Do:** always use `font: var(--bing-smtc-text-global-*)` shorthand — never set individual font-family, font-size, line-height, or font-weight.
- **Do:** start with `body/3` for any card body text; `body/3-strong` for card titles.
- **Do:** pair `caption/2` with `foreground/content/neutral/tertiary` for attribution.
- **Do:** use `body/3-strong` for clickable text elements (consistency rule).
- **Don't:** use `body/1` for general card text — reserved for single-answer hero.
- **Don't:** use caption styles as card titles — minimum is `body/3-strong`.
- **Don't:** hardcode font sizes, weights, or font-family.
- **Don't:** use `foreground/primary` color for body text — use `foreground/secondary`.

## Dark mode

Text color tokens auto-switch (white with opacity on dark). No special
dark overrides needed when tokens are used correctly.

## Open questions

None.
