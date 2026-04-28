# RevColorSwatch

## When to use

Square chip for displaying a colour option in a product selector or palette. Not interactive on its own — wrap in a button or selection control when colour picking is needed.

Always pair with a visible colour name or label — do not rely on the chip alone to convey information.

## Dependencies

None.

## Variants

None. Size is controlled by the `size` prop.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `color` | `string` | required | The colour to display. Accepts any valid colour value (hex, rgb, hsl, etc.). |
| `size` | `'small' \| 'medium'` | `'medium'` | Swatch dimensions — see size table |

### Size dimensions

| Size | Dimensions |
|------|-----------|
| `small` | 12 × 12px |
| `medium` | 16 × 16px |

## Structure

```
┌──────┐
│      │  ← filled with the `color` prop value
└──────┘
```

The swatch is a single square element. The border is a fixed overlay rendered on top of the colour fill.

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Border | `border.static.default.dim` | `hsla(225, 21%, 7%, 0.4)` |

The swatch background is set directly from the `color` prop — it is not a design token value.

### Spacing

| Part | Property | Value |
|------|----------|-------|
| Container | Margin (all sides) | 2px |
| Border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Swatch | `radius.md` | 8px |

## Accessibility

- RevColorSwatch is purely presentational. Always provide a visible colour name or accessible label on the surrounding control.
- For interactive colour selection, wrap RevColorSwatch in a button and communicate the selected state via `aria-pressed` or `aria-checked`.
- Do not use colour as the only means of conveying the current selection state.
