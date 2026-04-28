# RevChip

## When to use

Interactive pill-shaped filter button. Use for toggling filter states, triggering dropdowns, and selecting from a set of options in compact layouts.

Do not use for read-only labels — use RevTag. Keep labels short. Chip sets must wrap gracefully rather than overflow a single line.

## Dependencies

- `RevSpinner` — `guidelines/components/feedback/RevSpinner.md`

Must be implemented before building RevChip.

## Variants

Visual state is driven by `isActive` and `isOpen` rather than a `variant` prop.

| State | Description |
|-------|-------------|
| inactive | Default resting state |
| active | `isActive` or `isOpen` is true — pressed appearance |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | required | Chip label |
| `size` | `'small' \| 'medium' \| 'large'` | `'medium'` | Dimensions |
| `isActive` | `boolean` | `false` | Selected/pressed visual state |
| `isOpen` | `boolean` | `false` | Open state (e.g. dropdown is open). Also applies active styling. |
| `isLoading` | `boolean` | `false` | Shows spinner and blocks interaction |
| `disabled` | `boolean` | `false` | Disables interaction |
| `startIcon` | `component` | — | Leading icon |
| `endIcon` | `component` | — | Trailing icon. Overridden by chevron when `hasDropdown` is true. |
| `hasDropdown` | `boolean` | `false` | Adds a trailing chevron and sets dropdown ARIA attributes |
| `ariaControls` | `string` | — | ID of the controlled element. Required when `hasDropdown` is true. |
| `ariaExpanded` | `boolean` | — | Open state for ARIA. Required when `hasDropdown` is true. |
| `onClick` | `event → void` | — | Called on click when not disabled or loading |

## Structure

```
┌─────────────────────────────────────────────────┐
│  [startIcon?]  [Label]  [endIcon / chevron?]    │
└─────────────────────────────────────────────────┘
```

When `isLoading`, the content is hidden and a centred spinner replaces it.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Background | inactive | `background.action.default.low` | `hsl(0, 0%, 100%)` |
| Background | inactive hover | `background.action.default.low` (hover state) | `hsl(220, 19%, 94%)` |
| Background | active | `background.action.default.low` (pressed state) | `hsl(225, 21%, 7%)` |
| Background | disabled | `background.action.default.low` (disabled state) | — see `background.json` |
| Border | inactive | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Border | active | `border.action.default.low` (pressed state) | `hsl(225, 21%, 7%)` |
| Border | disabled | `border.action.default.low` (disabled state) | — see `border.json` |
| Label + icons | inactive | `text.onaction.default.low` | `hsl(225, 21%, 7%)` |
| Label + icons | active | `text.onaction.default.low` (pressed state) | `hsl(0, 0%, 100%)` |
| Label + icons | disabled | `text.onaction.default.low` (disabled state) | — see `text.json` |

### Typography

| Size | Token | Fallback |
|------|-------|---------|
| `small` | `label-medium` | 14px / weight 400 / line-height 16px |
| `medium` | `label-large` | 16px / weight 400 / line-height 20px |
| `large` | `label-large` | 16px / weight 400 / line-height 20px |

### Spacing

| Size | Property | Value |
|------|----------|-------|
| `small` | Height | 32px |
| `small` | Horizontal padding | 12px |
| `medium` | Height | 40px |
| `medium` | Horizontal padding | 16px |
| `large` | Height | 48px |
| `large` | Horizontal padding | 12px |
| all | Horizontal gap between elements | spacing token `4` (4px) |
| Border | Width and style | — | 1px solid |

When `hasDropdown` is true, trailing padding is reduced: small → 8px, medium → 12px, large → 8px.

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Chip container | `radius.round` | 9999px |

## Accessibility

- When `hasDropdown` is true, set `ariaControls` to the ID of the controlled panel and `ariaExpanded` to reflect its open state.
- `isLoading` blocks interaction silently — communicate loading state to screen readers via surrounding context or `aria-live`.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 4px (outline-offset-4).
