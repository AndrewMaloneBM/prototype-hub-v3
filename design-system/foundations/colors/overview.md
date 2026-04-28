# Colors overview

Raw palette: [`raw.json`](raw.json) — functional scales: [`functional.json`](functional.json)

## Mood system

Two mood contexts are supported: **default** (light) and **inverse** (dark). Every semantic token has a resolved value for each. Mood is applied at the section or container level — it shifts all token values within that context simultaneously. Never override individual token values to create a theme shift.

Two mood contexts are supported: **default** and **mood-inverse**.

## Token anatomy

```
color.[usage].[type].[level]
```

Examples:
- `color.background.surface.low`
- `color.text.static.default.hi`
- `color.border.action.default.hi`
- `color.focus.default.hi`

Resolved values for each token are in the corresponding JSON file under `default` and `mood-inverse` keys.

## Semantic layers

| Layer | Guidance | Resolved values | Purpose |
|-------|----------|-----------------|---------|
| `background` | `background.md` | `background.json` | Fill colors for surfaces and actions |
| `text` | `text.md` | `text.json` | Text and label colors |
| `border` | `border.md` | `border.json` | Borders and outlines |
| `functional` | `functional.md` | `functional.json` | Feedback state palette (danger, success, warning, info) |
| `artwork` | `artwork.md` | `artwork.json` | Illustration and decorative colors |

Never use `color.raw.*` tokens directly in components or layouts. They are the primitive palette that semantic tokens reference internally.

## Static color pairing rules

For non-interactive surfaces, pair tokens within the same surface level:

| Background | Text (primary) | Text (secondary) | Border/divider |
|------------|---------------|-----------------|----------------|
| `background.surface.low` | `text.static.default.hi` | `text.static.default.mid` | `border.static.default.low` |
| `background.surface.mid` | `text.static.default.hi` | `text.static.default.mid` | `border.static.default.low` |
| `background.surface.hi` | `text.static.default.hi` | `text.static.default.mid` | `border.static.default.low` |
| `background.surface.inverse` | `text.onaction.default.hi` | — | — |

All pairings pass WCAG AA contrast.

## Action color pairing rules

Interactive elements use `action` tokens. Match level (`hi`, `min`) and function (`default`, `danger`, `success`) consistently across all states.

### Filled actions — `hi` level

| State | Background | Text | Border |
|-------|-----------|------|--------|
| base | `background.action.default.hi` | `text.onaction.default.hi` | — |
| hover | `background.action.default.hi` (hover state) | `text.onaction.default.hi` | — |
| pressed | `background.action.default.hi` (pressed state) | `text.onaction.default.hi` | — |
| disabled | `background.action.default.hi` (disabled state) | `text.onaction.default.hi` (disabled state) | — |

Focus must additionally apply the `focus.default-hi` token as a focus indicator. See `focus.json`.

### Outlined actions — `min` level

| State | Background | Text | Border |
|-------|-----------|------|--------|
| base | `background.action.default.min` | `text.action.default.hi` | `border.action.default.hi` |
| hover | `background.action.default.min` (hover state) | `text.action.default.hi` | `border.action.default.hi` |
| pressed | `background.action.default.min` (pressed state) | `text.action.default.hi` | `border.action.default.hi` |
| disabled | `background.action.default.min` (disabled state) | `text.action.default.hi` (disabled state) | `border.action.default.hi` (disabled state) |

### Destructive — replace `default` with `danger`

Use `background.action.danger.*`, `text.onaction.danger.*`, `border.action.danger.*` following the same hi/min pattern. Disabled state always uses the generic disabled values regardless of function.

### Success — replace `default` with `success`

Use `background.action.success.*`, `text.onaction.success.*`, `border.action.success.*` following the same pattern.
