---
updated: 2026-06-30
source: ACF Storybook content update report 2026-06-30
stability: beta
---

# ML Body / Q&A Answer

**Group:** Layout · **Tier:** Section (ML Body module) · **Consumed by:** Section body / algo — Zone A; Section body / Q&A — Zone A

## Summary

ML Body / Q&A Answer is the Copilot-style generated answer module used inside answer-first SERP experiences. It combines a section title, a collapsible answer body, and a compact source-card row so generated content and attribution remain connected.

This component is appropriate for Copilot AI-generated answers with source attribution, when answer content is long enough to need expand/collapse, and when source cards should appear in a compact row below the answer. It is not for standard algorithm results (use ML Body / Basic Algo), People Also Ask lists (use ML Body / PAA Answer), or full section layout decisions (use Section body / Q&A).

---

## Structure

```
ML Body / Q&A Answer
├── Section / title
│   └── Copilot Search logo + title end props (thumbs, copy, info)
├── Answer body
│   ├── Title — title/2-strong
│   ├── Content paragraphs — headings + body text
│   └── Gradient fade + "Show more" button in collapsed state
└── Source card row
    ├── Source card x 2+ — favicon + site name + title
    └── "Show all" card — navigates to full sources
```

---

## Properties / Behaviors

| Property | Default | Description |
|---|---|---|
| **column** | `12` | Grid column context; controls footer block behavior and responsive layout |
| **title** | — | Main answer title |
| **expanded** | `false` | Whether the answer body is expanded |
| **onToggleExpanded** | — | Called when expand/collapse is toggled |
| **source row content** | — | Source cards and "Show all" action |

The collapsed answer body uses a 424px max-height with gradient fade and an explicit "Show more" affordance. Expanded content must reflow within its parent container instead of forcing page-level layout breaks.

---

## Anatomy

1. **Section title** — Identifies the generated answer and hosts end props such as feedback/copy/info controls.
2. **Answer body** — Collapsible text container for the generated answer.
3. **Gradient fade** — Indicates additional hidden answer content in collapsed state.
4. **Show more / show less control** — Toggles the expanded state.
5. **Source card row** — Horizontal attribution area with individual sources and "Show all".

---

## Usage Rules

- Use the Q&A answer body for generated answers that need attribution and controlled expansion.
- Keep the collapsed state meaningful: users should understand the answer gist before expanding.
- Use source cards directly below the answer body so attribution remains visually connected.
- The "Show all" source card opens or navigates to the full source list; do not overload the source row with too many visible cards.
- In column `2`, footer/block behavior may change; verify the module at all Page breakpoints.
- Do not use this component as a standalone section outside the Section body system.

---

## Do / Don't

### Do

- Use a clear title and preserve the Copilot source attribution pattern.
- Keep expansion controls keyboard-focusable and screen-reader understandable.
- Test the collapsed 424px state and the expanded state at each column context.
- Preserve source-card row alignment and spacing.

### Don't

- Don't hide critical attribution behind unrelated controls.
- Don't force the answer body to a custom fixed height other than the system collapsed behavior.
- Don't use this component for PAA question lists.
- Don't place source cards far from the answer they support.

---

## Dark Mode Notes

Generated answer text, gradient fade, source cards, and controls must use semantic tokens and meet WCAG AA contrast in both light and dark themes.

---

## Related Components

| Component | Relationship |
|---|---|
| **Section body / Q&A** | Section-level layout that can host this module in Zone A |
| **ML Body / PAA Answer** | Different Q&A pattern for People Also Ask lists |
| **Citation** | Related attribution mechanism for generated answers |
| **Section / title** | Provides title and end props |
| **Transition** | May be used for smooth expand/collapse behavior |

---

## Open questions

- Confirm full prop names from the current Figma/Storybook source beyond the visible report summary.
