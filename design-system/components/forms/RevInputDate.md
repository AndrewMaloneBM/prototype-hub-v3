# RevInputDate

## When to use

For date entry. Renders as a text input that opens a date picker when activated.

Use for calendar-driven selection (appointments, shipping dates, date of birth). When the date is known and typed directly (e.g. credit card expiry), use RevInputText with appropriate `inputmode` and `autocomplete` attributes.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `string` | — | Controlled date value in ISO 8601 format (`YYYY-MM-DD`) |
| `name` | `string` | — | Form field name |
| `min` | `string` | — | Earliest selectable date (`YYYY-MM-DD`) |
| `max` | `string` | — | Latest selectable date (`YYYY-MM-DD`) |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the input |
| `required` | `boolean` | `false` | Marks the field as required |
| `onChange` | `(value: string) → void` | — | Called when a date is selected. Returns ISO 8601 date string. |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │  [Value / Placeholder]  [CalIcon]  │  │
│  └────────────────────────────────────┘  │
│  [Hint / Error?]                         │
└──────────────────────────────────────────┘
```

The date picker panel opens below (or above if insufficient space below) the input.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Input background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Input background | disabled | `background.static.default.low` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| Input border | default | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Input border | focused | `focus.default-low` | `hsl(225, 7%, 78%)`, solid, 2px, offset 0 |
| Input border | error | `border.action.danger.hi` | `hsl(351, 84%, 39%)` |
| Input border | error + focused | `focus.danger-low` | `hsl(2, 100%, 85%)`, solid, 2px, offset 0 |
| Input border | disabled | `border.action.default.low` (disabled) | `hsl(225, 7%, 78%)` |
| Input value | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Input value | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Placeholder | default | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Calendar icon | default | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |
| Picker panel background | — | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Picker panel border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Selected date background | — | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| Selected date text | — | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| Today indicator | — | `border.action.default.hi` | `hsl(223, 7%, 20%)` |
| Disabled date text | — | `text.action.default.hi` (disabled state) | — see `text.json` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Input value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |
| Picker month/year heading | `body-1-bold` | 16px / weight 600 / line-height 24px |
| Picker day label | `caption` | 12px / weight 400 / line-height 16px |
| Picker date cell | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Input | Vertical padding | `12` | 12px |
| Input | Horizontal padding | `16` | 16px |
| Input | Horizontal gap between value and icon | `8` | 8px |
| Hint / Error | Top margin | `4` | 4px |
| Picker panel | Padding — all sides | `16` | 16px |
| Input border | Width and style | — | 1px solid |
| Picker panel border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |
| Picker panel | `radius.md` | 8px |
| Selected date cell | `radius.round` | 9999px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Picker panel | `shadow.md` | see `shadows.json` |

## Accessibility

- The date picker panel must be keyboard-navigable (arrow keys for date traversal, Enter to select, Escape to close).
- The input must convey the expected format in the label or hint (e.g. "DD/MM/YYYY").
- Selected date must be announced to screen readers when changed.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
