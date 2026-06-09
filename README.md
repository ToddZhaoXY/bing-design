# bing-design

Bing Design System (ACF) reference skill — neutral, standardized, single source of truth for the Answer Card Framework design rules, tokens, layout system, and components.

## Update history

| Date | Scope | Source |
|---|---|---|
| 2026-05-21 | Initial build — full skill structure, 83 components, layout, foundations, patterns | serp-design-skill v2.1 |
| 2026-06-05 | Foundations & visual quality update — typography, color, spacing, radius, elevation, motion, grid, VQ rubric promoted to stable | ACF Storybook (vibehub) |

## What this is

A **reference-type skill** that makes Bing design system rules available to any consuming agent or human. It describes the system; it does not perform generation or review on its own.

## Structure

```
bing-design/
├── SKILL.md                    # Entry point — principles, glossary, navigation
├── assets/                     # Token JSON catalogs
│   ├── token-catalog.json
│   ├── color-lookup.json
│   └── component-catalog.json
└── references/
    ├── foundations/             # Tokens & design foundations
    │   ├── typography.md
    │   ├── color.md
    │   ├── spacing.md
    │   ├── radius.md
    │   ├── elevation.md
    │   ├── motion.md
    │   ├── iconography.md
    │   ├── tokens-overview.md
    │   └── accessibility.md
    ├── layout/                 # Grid, zones, sections, card architecture
    │   ├── grid.md
    │   ├── zones.md
    │   ├── sections.md
    │   └── card-architecture.md
    ├── components/             # 83 component reference docs
    │   ├── index.md
    │   └── *.md
    ├── patterns/               # Cross-cutting patterns
    │   ├── index.md
    │   ├── visual-quality.md
    │   └── implementation-traps.md
    └── glossary.md             # Central glossary
```

## How to use

1. Read `SKILL.md` for the system overview, non-negotiable principles, and navigation table.
2. Drill into `references/` based on your task.
3. Pull pattern examples only when concrete visual comparisons are needed.
