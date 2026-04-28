# RevInputPhone

## When to use

For phone number entry with an inline country code selector. The leading selector shows a flag and the dialling code (e.g. +33).

Do not use for free-format phone fields without a country selector — use RevInputText instead.

## Dependencies

- RevInputText (`guidelines/components/forms/RevInputText.md`) — this component extends RevInputText
- RevCountryFlag (`guidelines/components/media/RevCountryFlag.md`) — used in the leading country selector

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | `string` | required | Links the label to the input |
| `label` | `string` | required | Visible label above the input |
| `value` | `string` | — | Controlled phone number value |
| `name` | `string` | — | Form field name |
| `countryCode` | `string` | — | ISO 3166-1 alpha-2 code of the selected country (e.g. `'FR'`) |
| `countries` | `object[]` | — | List of available countries with code and dialling prefix |
| `hint` | `string` | — | Helper text below the input |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the input and the country selector |
| `required` | `boolean` | `false` | Marks the field as required |
| `onCountryChange` | `(code: string) → void` | — | Called when the country selection changes |
| `onChange` | `event → void` | — | Called on phone number value change |

## Structure

```
┌──────────────────────────────────────────┐
│  [Label]                                 │
│  ┌────────────────────────────────────┐  │
│  │ [Flag + Code ▾] │  [Phone number]  │  │
│  └────────────────────────────────────┘  │
│  [Hint / Error?]                         │
└──────────────────────────────────────────┘
```

The country selector acts as a button that opens a dropdown list of countries. The divider between selector and input is `border.action.default.low`.

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
| Selector divider | default | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Country code text | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Country code text | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Phone number value | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Phone number value | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Placeholder | default | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Hint text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Error text | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| Chevron icon | default | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| Country code | `body-1` | 16px / weight 400 / line-height 24px |
| Phone number value | `body-1` | 16px / weight 400 / line-height 24px |
| Placeholder | `body-1` | 16px / weight 400 / line-height 24px |
| Hint / Error text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Bottom margin | `4` | 4px |
| Input | Vertical padding | `12` | 12px |
| Country selector | Horizontal padding | `12` | 12px |
| Phone number field | Horizontal padding | `16` | 16px |
| Flag + code | Horizontal gap | `8` | 8px |
| Hint / Error | Top margin | `4` | 4px |
| Input border | Width and style | — | 1px solid |
| Selector divider | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Input container | `radius.sm` | 6px |

## Accessibility

- The country selector must have an accessible label (e.g. "Country code") and announce the selected country name when opened.
- The phone number input is of type `tel` to trigger the numeric keyboard on mobile.
- The label must describe the combined field (e.g. "Phone number"), not the country selector alone.
- Focus ring: `focus.default-low` — `hsl(225, 7%, 78%)`, solid, 2px, offset 0.
