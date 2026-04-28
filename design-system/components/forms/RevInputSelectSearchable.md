# RevInputSelectSearchable

## When to use

For single-choice selection from a long list of options where filtering is needed. Renders a text input that both shows the selected value and filters the dropdown list as the user types.

Use RevInputSelect when the list is short enough to browse without filtering (typically under 20 options). Use RevInputAutocomplete when options are fetched dynamically from a backend as the user types.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText
- RevIcon (`guidelines/icons/`) — used for the trailing chevron

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `string` | — | Controlled selected value |
| `options` | `object[]` | required | Full list of options. Each has `value: string` and `label: string`. |
| `name` | `string` | — | Form field name |
| `placeholder` | `string` | — | Text shown when no value is selected |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the input |
| `required` | `boolean` | `false` | Marks the field as required |
| `noResultsLabel` | `string` | — | Message shown when the query matches no options |
| `onChange` | `(value: string) → void` | — | Called when an option is selected |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │  [Query / Selected label]        ▾ │  │
│  └────────────────────────────────────┘  │
│  ┌────────────────────────────────────┐  │
│  │  [Filtered option]                 │  │
│  │  [Filtered option]                 │  │
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
| Input border | disabled | `border.action.default.low` (disabled) | `hsl(225, 7%, 78%)` |
| Input value | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
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
| No results text | — | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Input value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Option text | `body-1` | 16px / weight 400 / line-height 24px |
| No results text | `body-2` | 14px / weight 400 / line-height 20px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Input | Vertical padding | `12` | 12px |
| Input | Horizontal padding | `16` | 16px |
| Option row | Vertical padding | `12` | 12px |
| Option row | Horizontal padding | `16` | 16px |
| No results message | Vertical padding | `16` | 16px |
| No results message | Horizontal padding | `16` | 16px |
| Hint / Error | Top margin | `4` | 4px |
| Input border | Width and style | — | 1px solid |
| Dropdown panel border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |
| Dropdown panel | `radius.md` | 8px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Dropdown panel | `shadow.md` | see `shadows.json` |

## Accessibility

- The input has `role="combobox"` and `aria-expanded` to indicate panel state.
- Each option has `role="option"`; the list has `role="listbox"`.
- Arrow keys navigate the filtered list; Enter confirms selection; Escape clears the query and closes the panel.
- The selected option is marked `aria-selected="true"`.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
