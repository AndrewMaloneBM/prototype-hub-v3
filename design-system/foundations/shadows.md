# Shadows

Resolved token values: [`shadows.json`](shadows.json)

Elevation tokens. Each level carries a `shadow` value (the drop shadow) and a `fill` value (the surface fill for neutral surfaces that need visual separation from their surroundings).

Shadows can be combined with any background token. However, when a surface is neutral (no distinct colour to visually separate it from its surroundings), shadow alone is not sufficient — it must be paired with the corresponding `float`, `overlap`, or `raised` background token to establish separation.

## Tokens

| Token | Offset | Required background for neutral surfaces | Use |
|-------|--------|------------------------------------------|-----|
| `elevation.short` | ~2px | `background.float.*` | Cards resting on a surface |
| `elevation.middle` | ~4px | `background.overlap.*` | Popovers, menus, hover-raised cards |
| `elevation.long` | ~8px | `background.raised.*` | Drawers, tooltips |

For modals and dialogs: use the highest elevation token, `background.overlay.hi` or `background.overlay.low` as the backdrop, and `RevBackdrop` to render it.

## Elevation hierarchy

```
Modals / dialogs    → elevation.long  + background.overlay.hi  (+ RevBackdrop)
Drawers / tooltips  → elevation.long  + background.raised.default.low
Popovers / menus    → elevation.middle + background.overlap.default.low
Cards (hover)       → elevation.middle + background.float.default.*
Cards (resting)     → elevation.short  + background.float.default.*
Base surfaces       → no shadow        + background.surface.*
```

## Rules

- Do not apply shadows to flat or inline elements (text, dividers, inline labels).
- Do not skip elevation levels — step up one level at a time.
- Do not use a shadow without its paired background token, and vice versa.
- Shadows are colour-aware: alpha values adapt across moods. Do not override shadow colours directly.
