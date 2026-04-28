# RevCheckbox

Covers RevCheckboxBase, which is an internal primitive not exposed in these guidelines.

## When to use

For multiple independent options where the user can select any number of items. Group multiple RevCheckbox components yourself — there is no wrapper group component.

Do not use when only one option can be selected — use RevRadio. Do not use for an immediate on/off setting — use RevToggle.

Always provide a visible group label when rendering a set of checkboxes. Error state must combine colour and descriptive text — never rely on colour alone.

## Dependencies

None.

## Variants

| Variant | Description |
|---------|-------------|
| `default` | Inline checkbox with label beside it |
| `full` | Card-style with optional description and trailing image. Shows a highlighted border when checked. |
| `imageOnly` | Card-style with trailing image, no description |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label and input — must be unique |
| `label` | `string` | required | Accessible label. Used as visible text when no `children` are provided. |
| `checked` | `boolean` | `false` | Controlled checked state |
| `disabled` | `boolean` | `false` | Disables interaction |
| `value` | `string` | `'on'` | Value submitted with a form |
| `variant` | `string` | `'default'` | Layout — see variants table |
| `description` | `node` | — | Secondary text. `full` variant only. |
| `displayDescriptionOnlyWhenChecked` | `boolean` | `false` | Hides description until checked. `full` variant only. |
| `image` | `node` | — | Trailing image or icon. `full` and `imageOnly` variants only. |
| `onChange` | `event → void` | — | Called on state change |
| `children` | `node` | — | Label content override |

## Structure

Default variant:

```
┌──────────────────────────────────┐
│  [Checkbox control]  [Label]     │
└──────────────────────────────────┘
```

Full variant:

```
┌──────────────────────────────────────────┐
│  [Checkbox control]  [Label]  [Image?]   │
│                      [description?]      │
└──────────────────────────────────────────┘
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Container (full/imageOnly) | unchecked | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Container (full/imageOnly) | unchecked | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Container (full/imageOnly) | checked | `border.action.default.low` (pressed state) | `hsl(225, 21%, 7%)` |
| Container (full/imageOnly) | disabled | `background.static.default.low` (disabled state) | — see `background.json` |
| Label text | enabled | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Label text | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Description | enabled | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Description | disabled | `text.action.default.low` (disabled state) | — see `text.json` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-1` | 16px / weight 400 / line-height 24px |
| Description | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Checkbox control + label | Horizontal gap | `8` | 8px |
| Label | Left padding (aligns after control) | `28` | 28px |
| Description | Top padding | `8` | 8px |
| Container (full/imageOnly) | Padding — all sides | `16` | 16px |
| Container (full/imageOnly) | Minimum height | — | 56px |
| Image | Leading margin (horizontal) | `16` | 16px |
| Container (full/imageOnly) | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Container (full/imageOnly) | `radius.sm` | 6px |

## Accessibility

- `id` must be unique — it links the visible label to the checkbox input.
- Always provide a visible group heading above a set of checkboxes.
- Error state must use both colour and a descriptive text message — never colour alone.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
