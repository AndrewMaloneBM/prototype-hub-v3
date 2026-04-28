# RevRadio

Covers RevRadioBase, which is an internal primitive not exposed in these guidelines.

## When to use

For single-choice selection from a set of 2–7 options. All radios sharing a `name` are mutually exclusive.

Use RevInputSelect when options exceed 7. Use RevCheckbox when multiple options can be selected. Use RevToggle for a single binary on/off setting.

Always define a default selected value — avoid leaving a radio group with nothing selected. When zero selection is a valid state, add an explicit "None" option rather than leaving all radios unchecked.

## Dependencies

None.

## Variants

Identical to RevCheckbox:

| Variant | Description |
|---------|-------------|
| `default` | Inline radio with label beside it |
| `full` | Card-style with optional description and trailing image. Shows a highlighted border when selected. |
| `imageOnly` | Card-style with trailing image, no description |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label and input — must be unique |
| `label` | `string` | required | Accessible label. Used as visible text when no `children` are provided. |
| `value` | `string` | required | Value of this option — required for radio groups |
| `name` | `string` | — | Groups radio buttons. All radios sharing a `name` are mutually exclusive. |
| `checked` | `boolean` | `false` | Controlled checked state |
| `disabled` | `boolean` | `false` | Disables interaction |
| `variant` | `string` | `'default'` | Layout — see variants table |
| `description` | `node` | — | Secondary text. `full` variant only. |
| `displayDescriptionOnlyWhenChecked` | `boolean` | `false` | Hides description until selected. `full` variant only. |
| `image` | `node` | — | Trailing image or icon. `full` and `imageOnly` variants only. |
| `onChange` | `event → void` | — | Called on state change |
| `children` | `node` | — | Label content override |

## Structure

Default variant:

```
┌─────────────────────────────────┐
│  [Radio control]  [Label]       │
└─────────────────────────────────┘
```

Full variant:

```
┌──────────────────────────────────────────┐
│  [Radio control]  [Label]  [Image?]      │
│                   [description?]         │
└──────────────────────────────────────────┘
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Container (full/imageOnly) | unselected | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Container (full/imageOnly) | unselected | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Container (full/imageOnly) | selected | `border.action.default.low` (pressed state) | `hsl(225, 21%, 7%)` |
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
| Radio control + label | Horizontal gap | `8` | 8px |
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

- Always set the same `name` on all radios in a group — this makes them mutually exclusive and groups them for screen readers.
- Always provide a visible group label (e.g. via `<fieldset>` + `<legend>`).
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
