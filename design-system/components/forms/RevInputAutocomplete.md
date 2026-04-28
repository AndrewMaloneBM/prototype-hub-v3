# RevInputAutocomplete

## When to use

For freeform text input that surfaces matching suggestions as the user types. Suggestions are provided externally — the component calls `onQuery` on each keystroke and renders whatever list is returned.

Use RevInputSelectSearchable when the full list of options is known upfront and filtering happens client-side. Use RevInputText with no suggestions when no completion is needed.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `string` | — | Controlled input value |
| `suggestions` | `object[]` | — | List of suggestions to display. Each has `value: string` and `label: string`. |
| `name` | `string` | — | Form field name |
| `placeholder` | `string` | — | Hint text shown when value is empty |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the input |
| `required` | `boolean` | `false` | Marks the field as required |
| `noResultsLabel` | `string` | — | Message shown when suggestions is an empty array |
| `onQuery` | `(query: string) → void` | — | Called on each value change. Use to fetch or filter suggestions. |
| `onSelect` | `(value: string) → void` | — | Called when a suggestion is selected |
| `onChange` | `event → void` | — | Called on every keystroke |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │  [Query text / Placeholder]        │  │
│  └────────────────────────────────────┘  │
│  ┌────────────────────────────────────┐  │
│  │  [Suggestion]                      │  │
│  │  [Suggestion]                      │  │
│  └────────────────────────────────────┘  │
│  [Hint / Error?]                         │
└──────────────────────────────────────────┘
```

The suggestion panel appears only while the input is focused and `suggestions` is non-empty (or `noResultsLabel` is set).

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
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Suggestion panel background | — | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Suggestion panel border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Suggestion row | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Suggestion row | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Suggestion text | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| No results text | — | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Input value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Suggestion text | `body-1` | 16px / weight 400 / line-height 24px |
| No results text | `body-2` | 14px / weight 400 / line-height 20px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Input | Vertical padding | `12` | 12px |
| Input | Horizontal padding | `16` | 16px |
| Suggestion row | Vertical padding | `12` | 12px |
| Suggestion row | Horizontal padding | `16` | 16px |
| Hint / Error | Top margin | `4` | 4px |
| Input border | Width and style | — | 1px solid |
| Suggestion panel border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |
| Suggestion panel | `radius.md` | 8px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Suggestion panel | `shadow.md` | see `shadows.json` |

## Accessibility

- The input has `role="combobox"` and `aria-expanded` to indicate panel state.
- Each suggestion has `role="option"`; the list has `role="listbox"`.
- Arrow keys navigate the list; Enter confirms; Escape closes the panel.
- Live results must be announced to screen readers (e.g. "3 suggestions available").
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
