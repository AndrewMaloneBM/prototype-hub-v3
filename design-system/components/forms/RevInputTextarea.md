# RevInputTextarea

## When to use

For collecting multi-line freeform text: messages, descriptions, comments, and similar long-form content.

Use RevInputText for single-line values. Do not restrict character count unless the backend has a hard limit — surface the limit as a hint, not as a hard block.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the textarea |
| `value` | `string` | — | Controlled value |
| `name` | `string` | — | Form field name |
| `placeholder` | `string` | — | Hint text shown when value is empty |
| `rows` | `number` | `4` | Initial number of visible rows |
| `maxLength` | `number` | — | Maximum character count. When set, a character counter is shown below. |
| `hint` | `string` | — | Helper text below the textarea |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the textarea |
| `readOnly` | `boolean` | `false` | Makes the textarea non-editable but focusable |
| `required` | `boolean` | `false` | Marks the field as required |
| `onChange` | `event → void` | — | Called on value change |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │  [Value / Placeholder]             │  │
│  │                                    │  │
│  │                                    │  │
│  └────────────────────────────────────┘  │
│  [Hint / Error?]         [Count / Max?]  │
└──────────────────────────────────────────┘
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Textarea background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Textarea background | disabled | `background.static.default.low` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| Textarea border | default | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Textarea border | focused | `focus.default-low` | `hsl(225, 7%, 78%)`, solid, 2px, offset 0 |
| Textarea border | error | `border.action.danger.hi` | `hsl(351, 84%, 39%)` |
| Textarea border | error + focused | `focus.danger-low` | `hsl(2, 100%, 85%)`, solid, 2px, offset 0 |
| Textarea border | disabled | `border.action.default.low` (disabled) | `hsl(225, 7%, 78%)` |
| Input value | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Input value | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Placeholder | default | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Character counter | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Character counter | over limit | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Textarea value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |
| Character counter | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Textarea | Vertical padding | `12` | 12px |
| Textarea | Horizontal padding | `16` | 16px |
| Hint / Counter row | Top margin | `4` | 4px |
| Textarea border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Textarea container | `radius.sm` | 6px |

## Accessibility

- Always provide `id` and `label` — the label is linked to the textarea via `for`/`id`.
- When a character limit is shown, it must be announced to screen readers as part of the hint (e.g. via `aria-describedby`), not only conveyed visually.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
