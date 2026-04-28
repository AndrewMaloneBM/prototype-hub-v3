# Listing page

## When to use

Catalog or search results page displaying a filterable, paginated collection of items. Use for category pages, search results, and any surface where the primary goal is to browse and narrow a set of products or entities.

## Components involved

| Component | File | Role |
|-----------|------|------|
| RevBanner | `components/feedback/RevBanner.md` | Page-level notification (when applicable) |
| RevBreadcrumbs | `components/navigation/RevBreadcrumbs.md` | Hierarchy trail below the page header |
| RevInputSelect | `components/forms/RevInputSelect.md` | Sort control |
| RevChip | `components/selection/RevChip.md` | Applied filter tags with individual clear action |
| RevLink | `components/actions/RevLink.md` | "Clear all" filters action |
| RevDrawer | `components/overlays/RevDrawer.md` | Filter panel container on mobile |
| RevStickyBar | `components/navigation/RevStickyBar.md` | "Apply filters" CTA pinned to bottom on mobile |
| RevCheckbox | `components/selection/RevCheckbox.md` | Multi-select filter groups |
| RevRadio | `components/selection/RevRadio.md` | Single-select filter groups |
| RevSlider | `components/selection/RevSlider.md` | Range filter (price, size, etc.) |
| RevDivider | `components/layout/RevDivider.md` | Separator between filter groups |
| RevCardGrid | `components/cards/RevCardGrid.md` | Results layout |
| RevPagination | `components/data-display/RevPagination.md` | Page navigation below results |
| RevSkeleton | `components/feedback/RevSkeleton.md` | Placeholder while results load |
| RevToast | `components/feedback/RevToast.md` | Transient feedback unrelated to filtering |

## Structure

Mobile:

```
┌──────────────────────────────────────────────────┐
│  [RevBanner?]                                    │
│  [RevBreadcrumbs]                                │
│  [Sort: RevInputSelect]    [Filters: button]     │
│  [RevChip ...]             [Clear all: RevLink?] │
├──────────────────────────────────────────────────┤
│  [RevCardGrid]                                   │
│  (or RevSkeleton placeholders while loading)     │
├──────────────────────────────────────────────────┤
│  [RevPagination]                                 │
└──────────────────────────────────────────────────┘
     ↕ RevDrawer (filter panel, slides up)
     ↕ RevStickyBar ("Apply" pinned at bottom while drawer open)
```

Desktop (md+):

```
┌────────────────────────────────────────────────────────────┐
│  [RevBanner?]                                              │
│  [RevBreadcrumbs]                                          │
│  [Sort: RevInputSelect]   [RevChip ...]   [Clear all?]     │
├──────────────────────────────┬─────────────────────────────┤
│  Filter sidebar              │  [RevCardGrid]              │
│  [RevCheckbox group]         │                             │
│  [RevDivider]                │                             │
│  [RevRadio group]            │                             │
│  [RevDivider]                │                             │
│  [RevSlider]                 │                             │
├──────────────────────────────┴─────────────────────────────┤
│  [RevPagination]                                           │
└────────────────────────────────────────────────────────────┘
```

## Assembly

1. Place `RevBanner` immediately below the page header if a page-level message is needed.
2. Place `RevBreadcrumbs` below the banner (or below the header if no banner).
3. Render a sort `RevInputSelect` and a row of applied-filter `RevChip` components above the results. Include a "Clear all" `RevLink` when any filters are active.
4. On mobile: open the filter panel in a `RevDrawer`. Pair it with a `RevStickyBar` at the bottom of the screen for the Apply action while the drawer is open.
5. On desktop (`md+`): render the filter panel as an inline sidebar beside the results grid. Separate filter groups with `RevDivider`.
6. Render results in `RevCardGrid`. While loading, replace grid items with `RevSkeleton` placeholders that mirror the card dimensions and layout exactly.
7. Place `RevPagination` below the grid.

## Rules

- Represent active filters as `RevChip` with the active state set. Always show applied state visually.
- Always provide a way to remove individual filters (per `RevChip`) and all filters at once ("Clear all" `RevLink`).
- On mobile, the filter `RevDrawer` must be paired with a `RevStickyBar` Apply action — do not make users scroll back to a top-positioned button.
- `RevSkeleton` placeholders must mirror the exact card grid layout (dimensions, column count) — mismatched skeletons increase perceived latency.
- `RevToast` is only for feedback unrelated to filtering or sorting (e.g. "Item added to cart"). Filter and sort state changes are reflected immediately in the grid — no toast needed.
