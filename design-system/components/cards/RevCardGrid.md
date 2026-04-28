# RevCardGrid

## When to use

A responsive grid layout for a set of cards. Handles the column count, gutter, and wrapping automatically based on the viewport and available space.

Use RevCardCarousel when cards should scroll horizontally without wrapping. RevCardGrid always wraps into multiple rows.

## Dependencies

None.

## Variants

None. Column count adapts to the container width based on the `minCardWidth` prop.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `minCardWidth` | `number` | `280` | Minimum card width in pixels. The grid uses as many columns as fit at this width. |
| `gap` | `number` | `16` | Gap between cards in pixels |
| `children` | `node` | required | Card components |

## Structure

```
┌──────────────────────────────────────────────┐
│  ┌────────┐  ┌────────┐  ┌────────┐          │
│  │ [Card] │  │ [Card] │  │ [Card] │          │
│  └────────┘  └────────┘  └────────┘          │
│  ┌────────┐  ┌────────┐                      │
│  │ [Card] │  │ [Card] │                      │
│  └────────┘  └────────┘                      │
└──────────────────────────────────────────────┘
```

## Tokens

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Cards | Horizontal gap between cards | `16` | 16px |
| Cards | Vertical gap between rows | `16` | 16px |

## Accessibility

- RevCardGrid is a layout container with no interactive role.
- Ensure the card order in the DOM matches the visual order to preserve logical reading flow for screen readers.
