# RevContainer

## When to use

Centers page content within a responsive max-width column with consistent horizontal padding. Use as the outermost wrapper for page sections to enforce grid margins and gutters.

Do not nest multiple RevContainer layers — compounded padding breaks the grid. Use spacing tokens for inner layout instead. Full-bleed elements (hero images, banners) must intentionally break out of the container.

## Dependencies

None.

## Variants

None. RevContainer has a single layout behaviour. The `mood` prop shifts the colour context for all content within.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `mood` | `'default' \| 'inverse'` | — | Overrides the mood context for all content inside this container |
| `children` | `node` | — | Page content |

## Structure

```
┌──────────────────────────────────────────────────────────┐
│  ← padding →  [Children]  ← padding →                   │
│                                                          │
│         ← max-width constraint (lg+) →                  │
└──────────────────────────────────────────────────────────┘
```

Horizontal padding is applied on both sides. On `lg+` a max-width of 1184px is applied and the content is centred.

## Tokens

### Spacing

| Breakpoint | Property | Token | Value |
|------------|----------|-------|-------|
| Default (mobile) | Horizontal padding | `24` | 24px |
| `lg+` (1200px+) | Horizontal padding | `32` | 32px |
| `lg+` | Max width | — | 1184px |

## Accessibility

- RevContainer is a layout wrapper only — it carries no semantic role.
- When `mood` is set to `inverse`, ensure all text and interactive elements inside meet WCAG AA contrast against the inverse surface.
