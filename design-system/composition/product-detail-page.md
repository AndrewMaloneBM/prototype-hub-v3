# Product detail page

## When to use

Single product evaluation and purchase page. Use for any surface where the primary goal is for the user to inspect a product and initiate a purchase.

## Components involved

| Component | File | Role |
|-----------|------|------|
| RevBreadcrumbs | `components/navigation/RevBreadcrumbs.md` | Hierarchy trail |
| RevMediaViewer | `components/media/RevMediaViewer.md` | Full-screen inspectable image gallery |
| RevCardCarousel | `components/cards/RevCardCarousel.md` | Thumbnail strip that triggers the media viewer |
| RevRating | `components/selection/RevRating.md` | Product star rating display |
| RevRadio | `components/selection/RevRadio.md` | Single-option variant picker (e.g. storage size) |
| RevChip | `components/selection/RevChip.md` | Multi-option variant picker (e.g. colour) |
| RevButton | `components/actions/RevButton.md` | Primary purchase CTA |
| RevStickyBar | `components/navigation/RevStickyBar.md` | Price + CTA when the buy box is off-screen |
| RevInfoBlock | `components/feedback/RevInfoBlock.md` | Warranty, returns, and sustainability highlights |
| RevTabs | `components/navigation/RevTabs.md` | Sections switcher: Specs / Reviews / FAQ |
| RevTable | `components/data-display/RevTable.md` | Technical specifications |
| RevAccordionList | `components/data-display/RevAccordionList.md` | FAQ items |

## Structure

Mobile (stacked):

```
┌──────────────────────────────────────────────────┐
│  [RevBreadcrumbs]                                │
│  [RevCardCarousel — thumbnails]                  │
│  [Product title]                                 │
│  [RevRating]                                     │
│  [Price]                                         │
│  [Variant pickers: RevRadio / RevChip]           │
│  [RevButton — "Add to cart"]                     │
│  [RevInfoBlock × n]                              │
│  [RevTabs]                                       │
│    Specs → [RevTable]                            │
│    Reviews → [review list]                       │
│    FAQ → [RevAccordionList]                      │
│  [RevCardCarousel — related products]            │
└──────────────────────────────────────────────────┘
[RevStickyBar] ← visible only when buy box CTA is off-screen
```

Desktop (md+ — two-column buy box):

```
┌──────────────────────────────────────────────────────────────┐
│  [RevBreadcrumbs]                                            │
├────────────────────────────┬─────────────────────────────────┤
│  [RevMediaViewer]          │  [Product title]                │
│  [RevCardCarousel thumbs]  │  [RevRating]                    │
│                            │  [Price]                        │
│                            │  [Variant pickers]              │
│                            │  [RevButton — "Add to cart"]    │
├────────────────────────────┴─────────────────────────────────┤
│  [RevInfoBlock × n]                                          │
│  [RevTabs → RevTable / Reviews / RevAccordionList]           │
│  [RevCardCarousel — related products]                        │
└──────────────────────────────────────────────────────────────┘
```

## Assembly

1. Place `RevBreadcrumbs` at the top of the page content area.
2. Build the buy box as a two-column block on `md+` (stacked on mobile): media on the left, product info and CTAs on the right.
3. In the media column: use a `RevCardCarousel` of thumbnails to trigger `RevMediaViewer` when a thumbnail is tapped or clicked.
4. In the product column: render title, `RevRating`, price, variant pickers, then the primary `RevButton` ("Add to cart").
5. Add `RevStickyBar` at the bottom of the viewport. Make it visible only once the buy box CTA has scrolled out of view — track this with an IntersectionObserver on the buy box button. The sticky bar must show the price and mirror the CTA label exactly.
6. Below the buy box: place `RevInfoBlock` components for warranty, returns, and sustainability content.
7. Use `RevTabs` to organise technical specs (`RevTable`), customer reviews, and FAQ (`RevAccordionList`) in a single section.
8. End the page with a `RevCardCarousel` of related products.

## Rules

- The CTA label must be identical between the buy box button and the `RevStickyBar` — never let them diverge.
- `RevStickyBar` must not be visible when the buy box is in the viewport. Use IntersectionObserver — not a scroll position threshold.
- Use `RevRadio` for option groups where the user picks one from a small visible set (2–7 options). Use `RevChip` for compact visual selection where labels are short or colour chips are needed.
- Keep variant picker labels consistent with the product data — do not rewrite or abbreviate option names.
