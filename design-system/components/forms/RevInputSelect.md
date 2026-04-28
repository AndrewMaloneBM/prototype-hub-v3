# RevInputSelect

## When to use

For single-choice selection from a predefined list of options. Use when there are more than 7 options or when screen space is limited.

Use RevRadio when 2–7 options should be visible at once. Use RevInputSelectSearchable when the list is long enough to warrant filtering. Use RevInputMultiSelect when more than one option can be selected.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for the trailing chevron

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the select |
| `label` | `string` | required | Visible label above the select |
| `value` | `string` | — | Controlled selected value |
| `options` | `object[]` | required | List of options. Each option has `value: string` and `label: string`. Optionally `disabled: boolean`. |
| `name` | `string` | — | Form field name |
| `placeholder` | `string` | — | Text shown when no value is selected |
| `hint` | `string` | — | Helper text below the select |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the select |
| `required` | `boolean` | `false` | Marks the field as required |
| `onChange` | `(value: string) → void` | — | Called when selection changes |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │  [Selected label / Placeholder]  ▾ │  │
│  └────────────────────────────────────┘  │
│  [Hint / Error?]                         │
└──────────────────────────────────────────┘
```

When open, a dropdown panel appears below (or above) the trigger with the list of options.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Trigger background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Trigger background | disabled | `background.static.default.low` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| Trigger border | default | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Trigger border | focused | `focus.default-low` | `hsl(225, 7%, 78%)`, solid, 2px, offset 0 |
| Trigger border | error | `border.action.danger.hi` | `hsl(351, 84%, 39%)` |
| Trigger border | disabled | `border.action.default.low` (disabled) | `hsl(225, 7%, 78%)` |
| Selected value | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Selected value | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Placeholder | default | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Chevron icon | default | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Dropdown panel background | — | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Dropdown panel border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Option row | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Option row | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Option row | selected | `background.action.default.mid` | `hsl(220, 19%, 94%)` |
| Option text | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Option text | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Selected value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Option text | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Trigger | Vertical padding | `12` | 12px |
| Trigger | Horizontal padding | `16` | 16px |
| Option row | Vertical padding | `12` | 12px |
| Option row | Horizontal padding | `16` | 16px |
| Hint / Error | Top margin | `4` | 4px |
| Trigger border | Width and style | — | 1px solid |
| Dropdown panel border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Trigger | `radius.sm` | 6px |
| Dropdown panel | `radius.md` | 8px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Dropdown panel | `shadow.md` | see `shadows.json` |

## Accessibility

- The trigger must be keyboard-activatable (Space or Enter).
- The dropdown must be navigable with arrow keys; focus must be trapped within when open.
- The currently selected option must be marked `aria-selected="true"`.
- The dropdown must close on Escape.
- Focus returns to the trigger after selection or dismissal.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
