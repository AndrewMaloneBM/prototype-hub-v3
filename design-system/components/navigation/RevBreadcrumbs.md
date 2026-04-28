# RevBreadcrumbs

## When to use

Shows the user's current position within a multi-level page hierarchy and provides links back to each ancestor level.

Do not use for tab-style navigation or workflow steps — use RevTabs or RevStepper instead. Always reflect the actual URL hierarchy; do not use breadcrumbs as a history trail.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for the separator between crumb items

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `items` | `object[]` | required | Ordered list of crumb items from root to current. Each item has `label: string` and optionally `href: string` or `to: string`. The last item is the current page and is not a link. |

## Structure

```
┌──────────────────────────────────────────────────────┐
│  [CrumbLink] [Separator] [CrumbLink] [Separator] [CurrentPage] │
└──────────────────────────────────────────────────────┘
```

All items except the last are rendered as links. The last item is plain text marking the current page.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Crumb link | default | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Crumb link | hovered | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Current page text | — | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Separator icon | — | `text.static.default.low` (via currentColor) | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Crumb link | `body-2` | 14px / weight 400 / line-height 20px |
| Current page | `body-2-bold` | 14px / weight 600 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Crumb items | Horizontal gap between items | `8` | 8px |
| Separator icon | Horizontal margin | `4` | 4px |

## Accessibility

- The breadcrumb list must be wrapped in a `<nav>` with `aria-label="Breadcrumb"` (or localised equivalent).
- The current page item must be marked `aria-current="page"`.
- The separator icons are decorative and must be hidden from assistive technology (`aria-hidden="true"`).
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
