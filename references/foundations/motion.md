---
updated: 2026-06-05
source: ACF Storybook foundations/motion
stability: stable
---

# Motion

## Summary

Animation timing and easing tokens for consistent, purposeful motion
across all ACF components. 200ms is the baseline for most transitions.
Motion is purposeful and minimal — animate only to provide interaction
feedback. Respect `prefers-reduced-motion`.

## Principles

- **Purposeful** — animate only to provide feedback or guide attention
- **Quick** — 200ms baseline; users should not wait for animations
- **Consistent** — same easing curve everywhere, no bouncing/spring
- **Reducible** — respect `prefers-reduced-motion`

## Duration tokens

| Token | Value | Use |
|---|---|---|
| `--smtc-duration-micro-01` | 50ms | Click state changes, tap feedback |
| `--smtc-duration-short-01` | 100ms | Underline animation, hover color |
| `--smtc-duration-short-02` | 200ms | **Default** — hover transitions, button feedback, card states |
| `--smtc-duration-medium-01` | 300ms | Image zoom, scale transforms |
| `--smtc-duration-medium-02` | 400ms | Default entrance with easing, modal/drawer |
| `--smtc-duration-mega-01` | 1000ms | Non-interactive elements, shimmer |

## Easing curves

| Token | Value | Use |
|---|---|---|
| `--smtc-entrance-01` | `cubic-bezier(0, 0, 0, 1)` | Default entrance translation/scaling |
| `--smtc-exit-01` | `cubic-bezier(0.6, 0, 0.75, 0.4)` | Exit scaling and translation |
| `--smtc-persistent-01` | `cubic-bezier(0.33, 0, 0, 1)` | On-screen translation and scaling |
| `--smtc-elastic-01` | `cubic-bezier(0.2, 1.5, 0.4, 1)` | Dropdown/popup menus, Copilot composer |
| `--smtc-linear` | `cubic-bezier(0, 0, 1, 1)` | Opacity and color/tonal shifts |
| `--bing-smtc-animation-ease-default` | `cubic-bezier(0.3, 0, 0.3, 1)` | Default easing for all ACF transitions |

## Component motion patterns

| Component | Trigger | Animation | Duration |
|---|---|---|---|
| Card (themed) | hover | Background color shift | 200ms |
| Card (neutral) | hover | Background + shadow lift | 200ms |
| Button | hover/pressed | Background + border color | 200ms |
| Toggle | click | Thumb slide position | 200ms |
| Accordion | expand/collapse | Height + opacity | 200ms |
| Drawer | open/close | Slide from edge | 400ms |
| Overlay | open/close | Fade backdrop + scale | 400ms |
| Toast | appear/dismiss | Slide in from edge | 400ms |
| Flyout | open/close | Scale + opacity | 200ms |
| Tooltip | show/hide | Opacity fade | 200ms |

## Choosing duration

| Behavior | Example | Token |
|---|---|---|
| Interaction feedback | Tap, hover, button press, switch toggle | micro-01 (50ms) |
| Visual accents | Hover color, underline grow, shimmer | short-01 (100ms) |
| UI element transitions | Tooltip, popover, toast, dropdown | short-02 (200ms) |
| Scaling / transform | Card scale on hover, zoom, rotate | short-02 (200ms) |
| Navigation / page swap | Tab switch, page change, side nav | medium-02 (400ms) |
| Modal / drawer | Slide-in panels, full-screen modals | medium-02 (400ms) |

## Choosing easing

| Motion type | Easing token | Why |
|---|---|---|
| Elements entering the screen | entrance-01 | Starts fast, decelerates — draws attention |
| Elements leaving the screen | exit-01 | Starts slow, accelerates — feels natural |
| Moving on screen | persistent-01 | Smooth, balanced curve |
| Dropdown / popup menus | elastic-01 | Slight overshoot — playful, draws attention |
| Opacity / color changes | linear | Constant rate — subtle changes don't need easing |

## Standard transition pattern

```css
.element {
  transition:
    background-color var(--smtc-duration-short-02, 200ms) var(--bing-smtc-animation-ease-default),
    box-shadow var(--smtc-duration-short-02, 200ms) var(--bing-smtc-animation-ease-default);
}
```

## Reduced motion

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## Common mistakes

| Mistake | Fix |
|---|---|
| Using generic `ease` or `ease-in-out` | Use `--bing-smtc-animation-ease-default` or specific tokens |
| Animation longer than 400ms for UI transitions | Keep most at 200ms, only modals at 400ms |
| Bounce/spring physics | Only elastic-01 has overshoot — use sparingly for dropdowns |
| Animating layout properties (width, height) | Prefer `transform` and `opacity` for performance |
| No `prefers-reduced-motion` support | Always include the `@media` query to disable motion |

## Do / Don't

- **Do:** animate `background-color` and `box-shadow` on hover/state changes at 200ms.
- **Do:** include a `prefers-reduced-motion` override that collapses all durations.
- **Do:** use `transform` and `opacity` for performance.
- **Don't:** use bouncing, spring physics, or variable easing curves (except elastic-01 for dropdowns).
- **Don't:** add decorative animations with no interaction feedback purpose.
- **Don't:** exceed 400ms for any UI transition.

## Open questions

None.
