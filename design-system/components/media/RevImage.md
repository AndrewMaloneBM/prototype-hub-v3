# RevImage

## When to use

Standard image component with performance defaults. Use for all product images, editorial images, and any raster content. Renders a native image element with lazy loading and async decoding by default.

## Dependencies

None.

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `src` | `string` | required | Image URL |
| `alt` | `string` | required | Alt text describing the image content |
| `width` | `number` | — | Intrinsic width in px. Provide to prevent layout shift. |
| `height` | `number` | — | Intrinsic height in px. Provide to prevent layout shift. |
| `loading` | `'lazy' \| 'eager'` | `'lazy'` | Loading strategy. Use `'eager'` for above-the-fold images. |
| `decoding` | `'async' \| 'sync' \| 'auto'` | `'async'` | Decoding mode |
| `srcSet` | `string` | — | Responsive source set for serving different resolutions |
| `sizes` | `string` | `'100vw'` | Responsive sizes hint — only applied when `srcSet` is set |

The image scales within its container without distortion. Width and height are bounded by the container dimensions.

## Structure

```
┌──────────────────────────────────────┐
│                                      │
│              [img]                   │
│                                      │
└──────────────────────────────────────┘
```

RevImage is a single `img` element. Sizing is entirely controlled by the container — the component applies no dimensions of its own.

## Tokens

None. RevImage applies no design tokens directly — sizing and layout are controlled by the container.

## Accessibility

- Always provide a descriptive `alt`. Describe the content and context of the image, not its appearance.
- Use `alt=""` only for purely decorative images that add no information.
- Do not embed critical text inside images — it cannot be read by screen readers or scaled by the user.
- Set `loading="eager"` for the largest above-the-fold image to avoid a Core Web Vitals LCP penalty.
- Always provide `width` and `height` to prevent cumulative layout shift (CLS).
