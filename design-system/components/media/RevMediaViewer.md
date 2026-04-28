# RevMediaViewer

## When to use

Full-screen gallery modal for inspecting a set of images in detail. Use for product photography where users need to zoom in and navigate between multiple shots.

Do not mix unrelated asset types in the same items array. Do not use for simple single-image display — use `RevImage` instead.

## Dependencies

- `RevButtonIcon` — `guidelines/components/actions/RevButtonIcon.md`
- `RevImage` — `guidelines/components/media/RevImage.md`
- `RevModalBase` — `guidelines/components/overlays/RevModalBase.md`

All three must be implemented before building RevMediaViewer.

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `open` | `boolean` | required | Controls visibility |
| `onClose` | `() → void` | required | Called when the viewer is dismissed |
| `items` | `MediaItem[]` | required | Array of images to display. Each item: `{ src, alt, thumbnailSrc? }` |
| `initialIndex` | `number` | `0` | Index of the image to show when the viewer opens |
| `closeButtonLabel` | `string` | `'Close'` | Accessible label for the close button |
| `previousLabel` | `string` | `'Previous'` | Accessible label for the Previous navigation button |
| `nextLabel` | `string` | `'Next'` | Accessible label for the Next navigation button |

**Built-in behaviours:**
- Counter showing current position (`current / total`) renders automatically
- Scrollable thumbnail strip renders automatically when `thumbnailSrc` is provided on items
- Previous/Next buttons are disabled at the first and last image respectively
- Keyboard navigation: Arrow Left / Arrow Right
- Output is rendered outside the normal component tree at the document root

### Thumbnail highlighting

The active thumbnail uses `border.action.default.low` (pressed state) — `hsl(223, 3%, 52%)`.

## Structure

```
┌──────────────────────────────────────────────────────────┐
│                                            [CloseBtn]    │
│                                                          │
│  [Prev]          [Main image]             [Next]         │
│                  [n / total]                             │
│  ┌────────────────────────────────────────────────────┐  │
│  │  [Thumb]  [Thumb]  [Thumb]  [Thumb]  ...          │  │
│  └────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────┘
```

The thumbnail strip renders only when at least one item provides a `thumbnailSrc`. The counter (`n / total`) renders automatically above the strip.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Active thumbnail border | selected | `border.action.default.low` (pressed state) | `hsl(223, 3%, 52%)` |

Remaining surface colours are inherited from `RevModalBase` — see `guidelines/components/overlays/RevModalBase.md`.

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Active thumbnail border | Width and style | — | 1px solid |

## Accessibility

- Always provide a descriptive `alt` on every item in the `items` array.
- `closeButtonLabel`, `previousLabel`, and `nextLabel` must be set to meaningful localised strings — do not leave them as the English defaults in non-English interfaces.
- Keyboard navigation (Arrow Left / Arrow Right) is built in. Ensure focus is managed correctly when the viewer opens and closes.
- Focus is trapped inside the viewer while open. Focus returns to the trigger element on close.
