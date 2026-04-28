# RevInputPassword

## When to use

For password entry. Masks the value by default and provides a trailing toggle to reveal the characters.

Do not use for security codes or PINs that should never be revealed — use RevInputText with `type="tel"` and no reveal toggle instead.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText
- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the show/hide toggle button

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `string` | — | Controlled value |
| `name` | `string` | — | Form field name |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the input |
| `required` | `boolean` | `false` | Marks the field as required |
| `autocomplete` | `string` | — | Maps to the native `autocomplete` attribute (e.g. `'current-password'`, `'new-password'`) |
| `onChange` | `event → void` | — | Called on value change |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │  [Value (masked)]  [ShowHideToggle]│  │
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
| Show/hide icon | default | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |

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
| Input | Horizontal gap between value and toggle | `8` | 8px |
| Hint / Error | Top margin | `4` | 4px |
| Input border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |

## Accessibility

- The show/hide toggle must have an accessible label that describes the current action (e.g. "Show password", "Hide password"), not the current state.
- Do not announce the revealed password characters to screen readers — the masking state is a visual control, not a state change that needs to be announced.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
