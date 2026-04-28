# RevToggle

## When to use

Binary on/off control for settings that apply immediately on change. Do not pair with a save button — toggling must apply the change at once.

Do not use in forms where changes are submitted later — use RevCheckbox instead. Label must describe the current state ("Notifications") not the action ("Enable notifications").

## Dependencies

None.

## Variants

None. Position is controlled via the `position` prop.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `checked` | `boolean` | `false` | Controlled state |
| `disabled` | `boolean` | `false` | Disables interaction |
| `label` | `string` | — | Visible label beside the track |
| `position` | `'left' \| 'right' \| 'sticked'` | `'left'` | Track position relative to label. `'sticked'` pushes label and track to opposite ends of the container. |
| `onChange` | `event → void` | — | Called on state change |
| `children` | `node` | — | Secondary description text below the label |

## Structure

```
┌──────────────────────────────────────┐
│  [Track]  [Label]                    │
│           [description?]             │
└──────────────────────────────────────┘
```

`position="right"` places the track after the label. `position="sticked"` spreads them to opposite ends.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Track | unchecked | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Track border | unchecked | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Track | checked | `background.action.success.hi` | `hsl(156, 100%, 21%)` |
| Track | checked | no border | — |
| Knob | all | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |
| Label | enabled | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Description | enabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Description | disabled | `text.static.default.low` (disabled state) | — see `text.json` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-1` | 16px / weight 400 / line-height 24px |
| Description | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Track + label | Horizontal gap | `12` | 12px |
| Track | Width | — | 46px |
| Track | Height | — | 24px |
| Knob (unchecked) | Size | — | 16 × 16px |
| Knob (checked) | Size | — | 20 × 20px |
| Track border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Track | `radius.lg` | 12px |
| Knob | `radius.round` | 9999px |

## Accessibility

- Uses a checkbox input internally — `aria-checked` reflects the state accurately.
- Label must be present and describe the current setting, not the action.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
