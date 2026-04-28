# RevInputMultiSelect

## When to use

For selecting multiple values from a predefined list. Selected items are shown as tags inside the trigger. The dropdown lists all available options with checkmarks on selected ones.

Use RevCheckbox when options must be visible at all times without a dropdown. Use RevInputSelect when only one value can be chosen.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for the trailing chevron and option checkmarks

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the trigger |
| `label` | `string` | required | Visible label above the trigger |
| `value` | `string[]` | `[]` | Controlled array of selected values |
| `options` | `object[]` | required | Available options. Each has `value: string` and `label: string`. |
| `name` | `string` | — | Form field name |
| `placeholder` | `string` | — | Text shown when no value is selected |
| `hint` | `string` | — | Helper text below the trigger |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the trigger |
| `required` | `boolean` | `false` | Marks the field as required |
| `maxSelections` | `number` | — | Maximum number of selectable items |
| `onChange` | `(values: string[]) → void` | — | Called when selection changes |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │ [Tag] [Tag] [Tag]  [Placeholder] ▾ │  │
│  └────────────────────────────────────┘  │
│  ┌────────────────────────────────────┐  │
│  │  ✓  [Selected option]              │  │
│  │     [Unselected option]            │  │
│  └────────────────────────────────────┘  │
│  [Hint / Error?]                         │
└──────────────────────────────────────────┘
```

Selected items appear as inline tags inside the trigger. Each tag has a remove button.

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
| Selected tag background | — | `background.static.default.hi` | `hsl(225, 15%, 89%)` |
| Selected tag border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Selected tag text | — | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Selected tag remove icon | — | `text.static.default.low` (via currentColor) | `hsl(223, 4%, 37%)` |
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
| Checkmark icon | selected | `text.action.default.hi` (via currentColor) | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Selected tag text | `body-2` | 14px / weight 400 / line-height 20px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Option text | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Trigger | Vertical padding | `8` | 8px |
| Trigger | Horizontal padding | `12` | 12px |
| Tag | Vertical padding | `4` | 4px |
| Tag | Horizontal padding | `8` | 8px |
| Tag | Horizontal gap between tags | `4` | 4px |
| Tag | Horizontal gap between text and remove icon | `4` | 4px |
| Option row | Vertical padding | `12` | 12px |
| Option row | Horizontal padding | `16` | 16px |
| Option row | Horizontal gap between checkmark and label | `8` | 8px |
| Hint / Error | Top margin | `4` | 4px |
| Trigger border | Width and style | — | 1px solid |
| Selected tag border | Width and style | — | 1px solid |
| Dropdown panel border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Trigger | `radius.sm` | 6px |
| Selected tag | `radius.round` | 9999px |
| Dropdown panel | `radius.md` | 8px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Dropdown panel | `shadow.md` | see `shadows.json` |

## Accessibility

- The trigger has `role="combobox"` and `aria-multiselectable="true"`.
- Each option has `role="option"` and `aria-selected` reflecting its current selection state.
- Each tag remove button must have an accessible label (e.g. "Remove France").
- When `maxSelections` is reached, unselected options must be marked `aria-disabled="true"`.
- Arrow keys navigate the dropdown list; Space or Enter toggles selection; Escape closes.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
