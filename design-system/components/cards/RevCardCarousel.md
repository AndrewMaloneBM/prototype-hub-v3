# RevCardCarousel

## When to use

A horizontally scrollable row of cards. Suitable for product shelves, recommendation rows, and any sequence of cards that should remain on a single line.

Use RevCardGrid when cards should wrap into multiple rows. Do not use RevCardCarousel for more than about 20 items — prefer pagination or "view all" navigation instead.

## Dependencies

- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the previous and next scroll controls

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `children` | `node` | required | Card components |
| `cardWidth` | `number` | — | Fixed card width in pixels. When unset, cards size to their content. |
| `gap` | `number` | `16` | Gap between cards in pixels |
| `showControls` | `boolean` | `true` | Shows previous/next arrow buttons |

## Structure

```
┌─────────────────────────────────────────────────────┐
│  [Prev]  ┌────────┐  ┌────────┐  ┌────────┐  [Next]│
│          │ [Card] │  │ [Card] │  │ [Card] │        │
│          └────────┘  └────────┘  └────────┘        │
└─────────────────────────────────────────────────────┘
```

Cards overflow and clip at the container edges. Scroll is driven by touch/pointer drag or the prev/next buttons.

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Prev / next button | See RevButtonIcon `secondary` variant tokens | |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Cards | Horizontal gap between cards | `16` | 16px |

## Accessibility

- The carousel has `role="region"` and `aria-label` describing the content (e.g. "Recommended products").
- The previous and next buttons must have accessible labels.
- Users must be able to scroll the carousel via keyboard (arrow keys or Tab through cards).
- Do not auto-play or auto-advance the carousel.
