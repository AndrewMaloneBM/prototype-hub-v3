# RevInputNumber

## When to use

For collecting numeric values with explicit increment and decrement controls. Suitable for quantities, counts, and bounded numeric inputs.

Do not use for prices, measurements, or other numbers where the user will type a specific value — use RevInputText instead. Use `min` and `max` to define the valid range.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText
- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the increment and decrement buttons

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `number` | — | Controlled value |
| `name` | `string` | — | Form field name |
| `min` | `number` | — | Minimum allowed value |
| `max` | `number` | — | Maximum allowed value |
| `step` | `number` | `1` | Increment/decrement amount |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the input and both buttons |
| `required` | `boolean` | `false` | Marks the field as required |
| `onChange` | `(value: number) → void` | — | Called on value change |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌──────────────────────────────────┐    │
│  │ [Decrement]  [Value]  [Increment]│    │
│  └──────────────────────────────────┘    │
│  [Hint / Error?]                         │
└──────────────────────────────────────────┘
```

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
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Increment / Decrement button | default | See RevButtonIcon `secondary` variant tokens |  |
| Increment / Decrement button | disabled | See RevButtonIcon `secondary` disabled tokens | |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Input value | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Input | Vertical padding | `12` | 12px |
| Input | Horizontal padding | `16` | 16px |
| Decrement / Increment button | Horizontal gap from value | `8` | 8px |
| Hint / Error | Top margin | `4` | 4px |
| Input border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |

## Accessibility

- Decrement and increment buttons must have accessible labels (e.g. "Decrease quantity", "Increase quantity").
- When `min` or `max` is reached, the corresponding button must be disabled.
- The input must expose `aria-valuemin`, `aria-valuemax`, and `aria-valuenow` if rendered as a custom spinbutton.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
