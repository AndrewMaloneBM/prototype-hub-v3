# RevDivider

## When to use

Visual separator between content sections or list items. Use when a visible line materially improves scannability — for example between rows in a settings list or between accordion groups.

Prefer spacing tokens over a divider for creating section hierarchy. Do not use dividers as a substitute for whitespace.

## Dependencies

None.

## Variants

| Variant | Use |
|---------|-----|
| `horizontal` | Separates stacked content (default) |
| `vertical` | Separates side-by-side content |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `'horizontal' \| 'vertical'` | `'horizontal'` | Orientation of the separator |

## Structure

Horizontal variant (default):

```
────────────────────────────────────────────────────────
```

Vertical variant:

```
│
│
│
```

The line is a single element with no children. Its extent fills the available space in its container.

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Line | `border.static.default.low` | `hsl(225, 15%, 89%)` |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Line | Width and style | — | 1px solid |

## Accessibility

- Rendered as `<hr>` — it is a thematic break in the content, announced as a separator by screen readers.
- Do not use RevDivider purely for decorative spacing — use padding and gap tokens instead.
