# RevEditorialCard

## When to use

A content card with an image, title, description, and optional call-to-action. Use for editorial content, blog posts, promotions, and feature highlights.

Use RevCategoryCard when only a label and image are needed with no description. Use RevButtonCard when the entire surface is the action.

## Dependencies

- RevButton (`guidelines/components/actions/RevButton.md`) — used for the optional CTA button
- RevImage (`guidelines/components/media/RevImage.md`)

## Variants

| Variant | Description |
|---------|-------------|
| `vertical` | Image on top, content below |
| `horizontal` | Image on the left, content on the right |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | `string` | required | Card heading |
| `description` | `string` | — | Supporting text |
| `image` | `node` | — | Card image (RevImage) |
| `cta` | `node` | — | Call-to-action button (RevButton) |
| `variant` | `'vertical' \| 'horizontal'` | `'vertical'` | Layout direction |
| `href` | `string` | — | Makes the card title a link |
| `to` | `string` | — | Makes the card title a router link |

## Structure

Vertical variant:

```
┌──────────────────────────────────┐
│  ┌────────────────────────────┐  │
│  │         [Image?]           │  │
│  └────────────────────────────┘  │
│  [Title]                         │
│  [Description?]                  │
│  [CTA?]                          │
└──────────────────────────────────┘
```

Horizontal variant:

```
┌────────────────────────────────────────────┐
│  ┌──────────┐   [Title]                    │
│  │ [Image?] │   [Description?]             │
│  └──────────┘   [CTA?]                     │
└────────────────────────────────────────────┘
```

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Card background | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Card border | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Title text | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Description text | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Title | `heading-3` | 18px / weight 600 / line-height 24px |
| Description | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Content area | Padding — all sides | `16` | 16px |
| Title + description | Vertical gap | `8` | 8px |
| Description + CTA | Vertical gap | `16` | 16px |
| Image + content (horizontal) | Horizontal gap | `16` | 16px |
| Card border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Card | `radius.lg` | 12px |
| Image corners (vertical) | `radius.lg` top corners | 12px |
| Image (horizontal) | `radius.lg` left corners | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Default | `shadow.short` | `0px 2px 4px 0px rgba(0, 0, 0, 0.05)` |

## Accessibility

- If `href` or `to` is set, the title renders as a link. Ensure the link text is descriptive.
- The image should have a meaningful `alt` if it conveys content not present in the title or description.
- The card itself is not interactive — only explicit links and buttons within it carry interactive semantics.
