# RevCard

## When to use

A generic content container with optional header, body, and footer sections. Use as the layout surface for product summaries, user profiles, settings panels, and other grouped content.

Use RevButtonCard when the entire card is the interactive element. Use RevCategoryCard or RevEditorialCard for specific content patterns with an image.

## Dependencies

None.

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `header` | `node` | — | Optional header section |
| `footer` | `node` | — | Optional footer section |
| `children` | `node` | required | Card body content |

## Structure

```
┌──────────────────────────────────┐
│  [Header?]                       │
├──────────────────────────────────┤
│  [Body content]                  │
├──────────────────────────────────┤
│  [Footer?]                       │
└──────────────────────────────────┘
```

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Card background | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Card border | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Header / footer divider | `border.static.default.low` | `hsl(225, 15%, 89%)` |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Body | Padding — all sides | `16` | 16px |
| Header | Padding — all sides | `16` | 16px |
| Footer | Padding — all sides | `16` | 16px |
| Card border | Width and style | — | 1px solid |
| Header / footer divider | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Card | `radius.lg` | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Default | `shadow.short` | `0px 2px 4px 0px rgba(0, 0, 0, 0.05)` |

## Accessibility

- RevCard is a presentational container with no interactive role.
- Any interactive elements within the card (buttons, links) carry their own focus and role semantics.
