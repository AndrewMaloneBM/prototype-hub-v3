# RevSkeleton

## When to use

Pulsing placeholder shape shown while content is loading. Use to mirror the structure of the content being fetched — text lines, images, cards, avatars. Prefer over `RevSpinner` for content areas as it communicates layout and reduces perceived latency.

Do not mix skeleton placeholders and real content within the same atomic block — load whole blocks coherently.

## Dependencies

None.

## Variants

Controlled by the `shape` prop rather than a `variant` prop.

| Shape | Use |
|-------|-----|
| `circle` | Avatar, icon, or any circular placeholder |
| `line` | Text line, label, or any inline placeholder |
| `rectangle` | Image, card, or any block placeholder |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `shape` | `'circle' \| 'line' \| 'rectangle'` | `'circle'` | Visual shape of the placeholder |
| `width` | `string \| number` | — | Width of the placeholder. Number is treated as pixels. |
| `height` | `string \| number` | — | Height of the placeholder. Number is treated as pixels. |
| `children` | `node` | — | When provided, the skeleton wraps the children and hides them while preserving their layout dimensions |

**Shape behaviour:**

| Shape | Default height | Notes |
|-------|----------------|-------|
| `circle` | Matches `width` | Set both `width` and `height` for explicit sizing |
| `line` | Min 16px, grows with content | Matches text line rhythm |
| `rectangle` | Full height of container | Use for image and card placeholders |

When `children` is passed, the skeleton derives its dimensions from the children and hides them visually. This is useful for matching the exact layout of the content being loaded without specifying explicit dimensions.

## Structure

No-children variant (explicit sizing):

```
┌──────────────────────────────────────┐
│         [animated placeholder]       │
└──────────────────────────────────────┘
```

With-children variant (dimensions derived from content):

```
┌──────────────────────────────────────┐
│         [hidden children]            │
└──────────────────────────────────────┘
```

Shape (`circle`, `line`, or `rectangle`) controls the border-radius. The animated pulse is applied to the background of the container.

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Background | `background.static.default.mid` | `hsl(220, 19%, 94%)` |

### Radius

| Shape | Token | Fallback |
|-------|-------|---------|
| `circle` | `radius.round` | 9999px |
| `line` | `radius.xs` | 2px |
| `rectangle` | `radius.lg` | 12px |

## Accessibility

- The skeleton element is presentational. Ensure the loading state is communicated to screen readers at a higher level — for example via `aria-busy="true"` on the containing section.
- Mirror the shape and rhythm of the final content as closely as possible. Mismatched skeletons increase perceived latency.
