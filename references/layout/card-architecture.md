---
updated: 2026-05-21
source: serp-design-skill v2.1 wiki/Card-System.md
stability: beta
---

# Card Architecture

## Summary

Every card has two parts: **shell** (container) and **body** (content).
The shell controls visual treatment (background, border, radius, padding).
The body is the content slot. Cards do not size themselves — height comes
from zone/grid context.

## Anatomy

```
┌─────────────────────────────────────────┐
│ Card Shell (border-radius, bg)          │
│ ┌─────────────────────────────────────┐ │
│ │ CardTitle (optional, basic only)    │ │
│ └─────────────────────────────────────┘ │
│ ┌─────────────────────────────────────┐ │
│ │ CardBody (content slot)             │ │
│ └─────────────────────────────────────┘ │
└─────────────────────────────────────────┘
```

## Three shell types

| Shell Type | Background | Padding | Gap | Title | Use |
|---|:---:|:---:|:---:|:---:|---|
| **Basic** | Yes | 20px | 8px | Yes | Text-heavy content with title header |
| **No Title** | No | 20px | — | No | Structured data, no title needed |
| **No Deco** | No | 0px | — | No | Full-bleed content (images, videos, maps) |

Shell sizing behavior:
- **Basic**: body uses `flex: 1 0 0` to fill remaining space after title
- **No Title**: body fills all available space
- **No Deco**: body occupies 100% width and 100% height; body component handles its own background and padding

## Two card styles

| Style | Background Token | Border | Use |
|---|---|---|---|
| **Accent** (default) | `--bing-smtc-background-card-on-primary-alt-rest` | None | All cards by default |
| **Neutral** | `--smtc-background-card-on-primary-default-rest` | `1px solid var(--smtc-stroke-card-on-primary-rest)` | Algo cards or specifically designed |

**Critical:** Neutral cards **must** have the stroke border. Accent cards have **no** border.

## Shell → body mapping

| Shell | Body Types |
|---|---|
| Basic | text, algo |
| No Title | singleQuickFact, entities, listView, multiNews |
| No Deco | image, video, multiQuickFact, map, singleNews, singleLocation, multiLocation, shopping |

## 14 card body types

| Body Type | Shell | Description |
|---|---|---|
| `text` | Basic | Text-heavy content with optional small image |
| `algo` | Basic | Search result: favicon, title, URL, snippet |
| `singleQuickFact` | No Title | Short factual answer |
| `entities` | No Title | Related entities carousel |
| `listView` | No Title | Navigable list items |
| `multiNews` | No Title | Series of news items |
| `image` | No Deco | Visual content, photos, galleries |
| `video` | No Deco | Video thumbnail + play button + duration |
| `multiQuickFact` | No Deco | Collection of quick facts in a grid |
| `map` | No Deco | Full-bleed geographical display |
| `singleNews` | No Deco | Single headline news item |
| `singleLocation` | No Deco | Single place listing |
| `multiLocation` | No Deco | Multiple related locations |
| `shopping` | No Deco | Product listings with images + prices |

## Height system

Row height = **88px** (`--serp-row`), gap = **24px** (`--serp-gutter`).

| Tall Variant | Body Height | Rows | Section Height |
|---|---|:---:|---|
| `standard` | ~352px | 4 rows | 424px |
| `standard-small` | ~160px | 2 rows | 200px |

Height rules:
- 1 card in a standard section → `standard` (4-row)
- 2 cards stacked in a standard section → both `standard-small` (2-row each)
- 2-card stacking math: 200px + 24px gap + 200px = 424px（必须精确）

### CGM (Magazine) 特殊规则

CGM section 内**所有 card 强制 200px**，无论内容多少。Card 不可按内容撑高，
超出部分裁剪（`overflow: hidden`）。

### Text truncation

Card 固定高度意味着内容必须截断：

| Element | Max lines | Where |
|---|---|---|
| Card title | 1 line (nowrap) | Basic shell cards |
| Algo title | 1 line (nowrap) | All algo cards |
| Algo snippet | 2–4 lines | Depends on tall variant |
| News headline | 3 lines | News cards |

## Width × height matrix

Every card body has two layout axes:

| Dimension | Values | Determined by |
|---|---|---|
| **Width** | Wide / Narrow | Zone width at runtime (`@container zone`) |
| **Height** | Tall / Short | `tall` prop |

### Four layout modes

| Mode | When | Layout |
|---|---|---|
| Wide + Tall | span 6 + standard | V-stack: image top, text below |
| Wide + Short | span 6 + standard-small | H-strip: image left, text right |
| Narrow + Tall | span 2 + standard | Single column, stacked |
| Narrow + Short | span 2 + standard-small | Ultra-minimal, 1–2 items |

### Span → width mapping

- **span 6** → almost always **wide** (≥548px)
- **span 2** → almost always **narrow** (~180px)
- **span 3** → starts **narrow** (~242px) → becomes **wide** during zone reflow

### Width breakpoint thresholds

Width 由 `@container zone` 动态决定：

| Container width | Classification |
|---|---|
| ≥ 250px | **Wide** |
| 150–249px | Transitional |
| < 150px | **Narrow** — only critical content (P1) |

## Anchor and accessory cards

- **Anchor card**: primary (largest) card in a magazine grouping. Typically
  span 6, positioned in Zone A.
- **Accessory card**: secondary supporting cards. Typically span 2–3,
  positioned in Zone B or C.

Every design must provide both an anchor card and an accessory card variant.

## Do / Don't

- **Do:** always provide both anchor and accessory card variants.
- **Do:** test all 4 layout modes (wide/narrow × tall/short).
- **Do:** use `overflow: hidden` on all card shells.
- **Don't:** size cards explicitly — let zone/grid context determine height.
- **Don't:** let content push card beyond its fixed height — truncate text, clip overflow.
- **Don't:** use image aspect ratio to determine card height — images fill available space via `flex: 1` + `cover`.
- **Don't:** allow different cards in the same zone to have different heights.
- **Don't:** use Hug Contents on card frames — cards are fixed height or fill container.
- **Don't:** add borders to accent cards.
- **Don't:** omit the stroke border on neutral cards.

## Open questions

None.
