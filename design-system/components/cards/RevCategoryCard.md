# RevCategoryCard

## When to use

A navigational card linking to a product category or section. Combines an image with a category label. The entire card surface is the link target.

Use RevEditorialCard when the card needs a description or a separate CTA button. Use RevButtonCard when no image is required.

## Dependencies

- RevImage (`guidelines/components/media/RevImage.md`)

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | required | Category name displayed below the image |
| `image` | `node` | required | Category image (RevImage) |
| `href` | `string` | — | Link to external URL |
| `to` | `string` | — | Link using the application's router |

## Structure

```
┌──────────────────────────┐
│  ┌────────────────────┐  │
│  │    [Image]         │  │
│  └────────────────────┘  │
│  [Label]                 │
└──────────────────────────┘
```

The entire card is a link. The image fills the top portion; the label sits below it.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Card background | default | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Card background | hovered | `background.float.default.low` (hover) | `hsl(0, 0%, 100%)` |
| Card border | default | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Label text | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-1-bold` | 16px / weight 600 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Label | Vertical padding | `12` | 12px |
| Label | Horizontal padding | `12` | 12px |
| Card border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Card | `radius.lg` | 12px |
| Image top corners | `radius.lg` | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Default | `shadow.short` | `0px 2px 4px 0px rgba(0, 0, 0, 0.05)` |
| Hovered | `shadow.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |

## Accessibility

- The card renders as an `<a>` element. The accessible name is derived from `label`.
- The image is decorative — its `alt` should be empty or match the label if descriptive.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
