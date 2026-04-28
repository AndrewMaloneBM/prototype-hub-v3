# RevStickyBar

## When to use

A fixed bar pinned to the bottom of the viewport. Used for primary call-to-action buttons that must remain visible as the user scrolls — checkout, confirmation, or other primary actions on product and cart pages.

Do not use RevStickyBar for secondary navigation or breadcrumbs. Do not stack multiple sticky bars.

## Dependencies

None.

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `children` | `node` | required | Action buttons, price summaries, or other inline content |

## Structure

```
┌──────────────────────────────────────────────────────┐
│  [children — buttons, text, or summary content]      │
└──────────────────────────────────────────────────────┘
```

The bar is fixed at the bottom of the viewport. Content is horizontally padded and vertically centred.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Bar background | — | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Bar top border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Bar | Vertical padding | `16` | 16px |
| Bar | Horizontal padding | `16` | 16px |
| Bar top border | Width and style | — | 1px solid |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Bar | `shadow.lg` | see `shadows.json` |

## Accessibility

- The bar must not obscure interactive content below it. The page must add bottom padding equal to the bar's height so scrollable content is always reachable.
- On small viewports, ensure all children remain accessible and not clipped by the safe area inset at the bottom.
