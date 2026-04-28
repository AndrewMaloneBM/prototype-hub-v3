# RevPagination

## When to use

For navigating across pages of results. Renders a previous/next control and a set of numbered page buttons.

Use RevPagination when results are split into discrete pages. For infinite scroll or "load more" patterns, use a plain RevButton instead.

## Dependencies

- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the previous and next arrow buttons

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `page` | `number` | required | Current page (1-indexed) |
| `total` | `number` | required | Total number of pages |
| `onChange` | `(page: number) → void` | required | Called when the user selects a page |
| `siblingCount` | `number` | `1` | Number of page buttons shown on each side of the current page |

## Structure

```
┌────────────────────────────────────────────────────┐
│  [Prev]  [1]  …  [4]  [5]  [6]  …  [12]  [Next]   │
└────────────────────────────────────────────────────┘
```

Pages far from the current range are collapsed to an ellipsis. The current page button is highlighted.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Page button | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Page button | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Page button | current | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| Page button border | default | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| Page button border | current | none | — |
| Page number | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Page number | current | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| Page number | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Ellipsis | — | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Page number | `body-2` | 14px / weight 400 / line-height 20px |
| Current page number | `body-2-bold` | 14px / weight 600 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Pagination row | Horizontal gap between items | `4` | 4px |
| Page button | Minimum width | — | 36px |
| Page button | Vertical padding | `8` | 8px |
| Page button | Horizontal padding | `8` | 8px |
| Page button border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Page button | `radius.sm` | 6px |

## Accessibility

- The pagination container must be wrapped in a `<nav>` with `aria-label="Pagination"` (or localised equivalent).
- The current page button must have `aria-current="page"`.
- Prev/next buttons must have accessible labels (e.g. "Previous page", "Next page").
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
