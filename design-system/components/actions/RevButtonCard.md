# RevButtonCard

## When to use

A card-shaped interactive container where the entire surface is clickable. Use when a card represents a single action or navigation target.

Do not use when a card contains multiple independent interactive elements — use `RevCard` with explicit buttons or links inside instead. Do not nest `RevButtonCard` inside another card.

Lives in `actions/` because it is fundamentally an action primitive. The `cards/` category references it from there.

## Dependencies

- `RevSpinner` — `guidelines/components/feedback/RevSpinner.md`

Must be implemented before building RevButtonCard.

## Variants

None. RevButtonCard has a single visual style.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `disabled` | `boolean` | `false` | Disables interaction and desaturates content |
| `loading` | `boolean` | `false` | Shows a centred spinner and hides content. Layout dimensions are preserved. |
| `loadingAlternativeText` | `string` | `'Loading'` | Accessible label for the loading spinner |
| `to` | `object` | — | Route object — delegates to navigation context |
| `href` | `string` | — | URL string — renders as a hyperlink |
| `replace` | `boolean` | `false` | Replaces the current history entry instead of pushing a new one |
| `type` | `'button' \| 'submit' \| 'reset'` | `'button'` | Button type. Set to `'submit'` when the card sits inside a form and should submit it. |
| `children` | `node` | — | Card content |

When neither `to` nor `href` is set, renders as a button.

## Structure

```
┌──────────────────────────────────────────┐
│                                          │
│              [Children]                  │
│                                          │
└──────────────────────────────────────────┘
```

When `loading` is true, children are hidden and a centred spinner is shown; layout dimensions are preserved.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Background | base | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Background | hover | `background.float.default.low` (hover state) | — see `background.json` |
| Background | disabled | `background.float.default.low` (disabled state) | — see `background.json` |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| base | `elevation.short` | `0px 2px 4px 0px rgba(0, 0, 0, 0.05)` |
| hover | `elevation.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |
| disabled | no elevation | — |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Card container | `radius.lg` | 12px |

## Accessibility

- Always provide a descriptive label for the card's action — either via visible content inside or via `aria-label` on the component.
- When `loading` is true, content is visually hidden but retains its layout dimensions so the card does not collapse.
- When `disabled` is true on a button, the element is natively non-interactive. When rendered as a link, `aria-disabled` is set.
- Focus ring: `focus.default-hi` — color `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
