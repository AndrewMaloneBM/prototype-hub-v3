# RevInputText

Base text input. Most other input components in this category build on this one.

## When to use

For collecting short freeform text: names, emails, search queries, and similar single-line values.

Use RevInputTextarea for multi-line text. Use RevInputSelect when options are predefined. Use RevInputNumber for numeric values with increment/decrement controls.

## Dependencies

- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the optional clear button and trailing action.

## Variants

None. Appearance is controlled through state (error, disabled) and props (leadingIcon, trailingIcon, clearable).

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `string` | — | Controlled value |
| `name` | `string` | — | Form field name |
| `placeholder` | `string` | — | Hint text shown when value is empty |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message. When set, the input is in error state and the message replaces the hint. |
| `disabled` | `boolean` | `false` | Disables the input |
| `readOnly` | `boolean` | `false` | Makes the input non-editable but focusable |
| `required` | `boolean` | `false` | Marks the field as required |
| `autocomplete` | `string` | — | Maps to the native `autocomplete` attribute (e.g. `'email'`, `'given-name'`) |
| `leadingIcon` | `node` | — | Icon placed inside the input before the value |
| `trailingIcon` | `node` | — | Icon placed inside the input after the value |
| `clearable` | `boolean` | `false` | Shows a clear button when the input has a value |
| `onChange` | `event → void` | — | Called on value change |
| `onBlur` | `event → void` | — | Called when the input loses focus |
| `onFocus` | `event → void` | — | Called when the input gains focus |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │ [LeadingIcon?]  [Value / Placeholder]  [ClearButton? / TrailingIcon?] │
│  └────────────────────────────────────┘  │
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
| Placeholder | default | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Leading / trailing icon | default | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Input value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Input | Vertical padding | `12` | 12px |
| Input | Horizontal padding | `16` | 16px |
| Input | Horizontal gap between icon and value | `8` | 8px |
| Hint / Error | Top margin | `4` | 4px |
| Input border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |

## Accessibility

- Always provide `id` and `label` — the label is linked to the input via `for`/`id`.
- When in error state, the error message must be associated with the input via `aria-describedby`.
- When `required`, the input must be marked `aria-required="true"` and the label must indicate the requirement visually.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0. In error state: `focus.danger-low` — `hsl(2, 100%, 85%)`, solid, 2px, offset 0.
- The clear button must have an accessible label (e.g. "Clear [field label]").
