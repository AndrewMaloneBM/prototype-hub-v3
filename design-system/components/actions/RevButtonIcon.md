# RevButtonIcon

## When to use

Icon-only button. Use when space is constrained or when the action is universally understood from the icon alone. Always requires an accessible label — the button has no visible text.

For actions that need a visible label, use `RevButton`. For card-shaped surfaces, use `RevButtonCard`.

## Dependencies

- `RevSpinner` — `guidelines/components/feedback/RevSpinner.md`
- Icon component — `guidelines/icons/icons.md`

Both must be implemented before building RevButtonIcon.

## Variants

| Variant | Style | Use |
|---------|-------|-----|
| `primary` | Filled — default | Primary icon action |
| `primaryDestructive` | Filled — danger | Primary destructive icon action |
| `secondary` | Outlined — default | Secondary icon action |
| `secondaryDestructive` | Outlined — danger | Secondary destructive icon action |
| `ghost` | No border, no fill | Subtle action in toolbars or inline contexts |
| `ghostDestructive` | No border, no fill — danger text | Subtle destructive icon action |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `icon` | `component` | required | The icon to display |
| `variant` | `string` | required | Visual style — see variants table |
| `size` | `'medium' \| 'small'` | `'medium'` | Button size |
| `disabled` | `boolean` | `false` | Disables interaction |
| `loading` | `boolean` | `false` | Shows spinner instead of icon |
| `hasBadge` | `boolean` | `false` | Shows a small danger dot — e.g. notification indicator |
| `alternativeText` | `string` | required | Accessible label. The button has no visible text — this is mandatory. |
| `loadingAlternativeText` | `string` | — | Accessible label while loading |
| `to` | `object` | — | Route object — delegates to navigation context |
| `href` | `string` | — | URL string — renders as a hyperlink |
| `replace` | `boolean` | `false` | Replaces the current history entry instead of pushing a new one |

## Structure

```
┌──────────┐
│  [Icon]  │
└──────────┘
```

When `loading` is true, the icon is replaced by a spinner. When `hasBadge` is true, a small dot indicator is overlaid at the top-trailing corner of the container.

## Tokens

### Color

Filled variants (`primary`, `primaryDestructive`) follow the same pattern as RevButton filled. Ghost variants share the background token with outlined but have no border.

| Variant | Part | State | Token | Fallback (default mood) |
|---------|------|-------|-------|------------------------|
| `primary` | Background | base | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| `primary` | Background | hover | `background.action.default.hi` (hover) | `hsl(231, 7%, 21%)` |
| `primary` | Background | disabled | `background.action.default.hi` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| `primary` | Icon color | base + hover | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| `primary` | Icon color | disabled | `text.onaction.default.hi` (disabled) | `hsl(223, 3%, 57%)` |
| `primaryDestructive` | Background | base | `background.action.danger.hi` | `hsl(351, 84%, 39%)` |
| `primaryDestructive` | Background | hover | `background.action.danger.hi` (hover) | `hsl(354, 72%, 52%)` |
| `primaryDestructive` | Background | disabled | `background.action.danger.hi` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| `primaryDestructive` | Icon color | base + hover | `text.onaction.danger.hi` | `hsl(0, 0%, 100%)` |
| `primaryDestructive` | Icon color | disabled | `text.onaction.danger.hi` (disabled) | `hsl(223, 3%, 57%)` |
| `secondary` | Background | base | `background.action.default.min` | `hsla(225, 21%, 7%, 0)` |
| `secondary` | Background | hover | `background.action.default.min` (hover) | `hsla(225, 21%, 7%, 0.06)` |
| `secondary` | Background | disabled | `background.action.default.min` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| `secondary` | Icon color | base + hover | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| `secondary` | Icon color | disabled | `text.action.default.hi` (disabled) | `hsl(223, 3%, 57%)` |
| `secondary` | Border | base + hover | `border.action.default.low` | `hsl(223, 3%, 52%)` |
| `secondary` | Border | disabled | `border.action.default.low` (disabled) | `hsl(225, 7%, 78%)` |
| `secondaryDestructive` | Background | base | `background.action.danger.min` | `hsla(351, 84%, 39%, 0)` |
| `secondaryDestructive` | Background | hover | `background.action.danger.min` (hover) | `hsla(351, 84%, 39%, 0.06)` |
| `secondaryDestructive` | Background | disabled | `background.action.danger.min` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| `secondaryDestructive` | Icon color | base + hover | `text.action.danger.hi` | `hsl(351, 84%, 39%)` |
| `secondaryDestructive` | Icon color | disabled | `text.action.danger.hi` (disabled) | `hsl(223, 3%, 57%)` |
| `secondaryDestructive` | Border | base + hover | `border.action.danger.hi` | `hsl(351, 84%, 39%)` |
| `secondaryDestructive` | Border | disabled | `border.action.danger.hi` (disabled) | `hsl(225, 7%, 78%)` |
| `ghost` | Background | base | `background.action.default.min` | `hsla(225, 21%, 7%, 0)` |
| `ghost` | Background | hover | `background.action.default.min` (hover) | `hsla(225, 21%, 7%, 0.06)` |
| `ghost` | Background | disabled | `background.action.default.min` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| `ghost` | Icon color | base + hover | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| `ghost` | Icon color | disabled | `text.action.default.hi` (disabled) | `hsl(223, 3%, 57%)` |
| `ghostDestructive` | Background | base | `background.action.default.min` | `hsla(225, 21%, 7%, 0)` |
| `ghostDestructive` | Background | hover | `background.action.default.min` (hover) | `hsla(225, 21%, 7%, 0.06)` |
| `ghostDestructive` | Background | disabled | `background.action.default.min` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| `ghostDestructive` | Icon color | base + hover | `text.action.danger.hi` | `hsl(351, 84%, 39%)` |
| `ghostDestructive` | Icon color | disabled | `text.action.danger.hi` (disabled) | `hsl(223, 3%, 57%)` |

Badge dot color: `background.action.danger.hi` base — `hsl(351, 84%, 39%)`.

Mood-inverse fallback values are in `guidelines/foundations/colors/background.json`, `text.json`, and `border.json`.

### Spacing

| Size | Dimension | Value |
|------|-----------|-------|
| `medium` | Width × Height (default) | 32 × 32px |
| `medium` | Width × Height (xs breakpoint+) | 40 × 40px |
| `small` | Width × Height (default) | 24 × 24px |
| `small` | Width × Height (xs breakpoint+) | 32 × 32px |
| Border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Button container | `radius.round` | 9999px |

## Accessibility

- `alternativeText` is mandatory. The button has no visible text — without it the element is inaccessible.
- When `hasBadge` is true, the badge is decorative. The notification state should be communicated via the `alternativeText` value (e.g. "Notifications — 3 unread").
- Focus ring: `focus.default-hi` — color `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
