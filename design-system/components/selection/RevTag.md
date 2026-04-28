# RevTag

## When to use

Read-only label for categorising or annotating content — product conditions, status labels, content types. Never interactive.

For clickable filter tags use RevChip. Keep label text short and in sentence case.

## Dependencies

None.

## Variants

Two axes: `variant` (colour) and `variation` (fill style).

| Variant | Use |
|---------|-----|
| `primary` | Brand highlight (lime tint) |
| `secondary` | Neutral |
| `info` | Informational |
| `success` | Positive / confirmed |
| `warning` | Cautionary |
| `danger` | Error / destructive |
| `alternate` | Purple-toned neutral |

| Variation | Style |
|-----------|-------|
| `filled` | Solid background (default) |
| `outline` | Border only, transparent background |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | required | Tag text |
| `variant` | `string` | required | Colour — see variants table |
| `size` | `'small' \| 'medium' \| 'large'` | `'medium'` | Dimensions |
| `variation` | `'filled' \| 'outline'` | `'filled'` | Fill style |

## Structure

```
╭──────────────╮
│  [Label]     │
╰──────────────╯
```

## Tokens

### Color — filled variation

| Variant | Background token | Fallback | Text token | Fallback |
|---------|-----------------|----------|------------|---------|
| `primary` | `background.static.info.max` | `hsl(70, 88%, 73%)` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| `secondary` | `background.static.default.mid` | `hsl(220, 19%, 94%)` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| `info` | `background.static.info.mid` | `hsl(221, 86%, 92%)` | `text.static.info.hi` | `hsl(219, 27%, 40%)` |
| `success` | `background.static.success.mid` | `hsl(145, 83%, 77%)` | `text.static.success.hi` | `hsl(156, 100%, 21%)` |
| `warning` | `background.static.warning.mid` | `hsl(38, 90%, 84%)` | `text.static.warning.hi` | `hsl(42, 75%, 27%)` |
| `danger` | `background.static.danger.mid` | `hsl(3, 100%, 92%)` | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| `alternate` | `background.static.default.mid` | `hsl(220, 19%, 94%)` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Color — outline variation

| Variant | Border token | Fallback | Text token | Fallback |
|---------|-------------|----------|------------|---------|
| `primary` | `border.static.brand.hi` | `hsl(70, 45%, 49%)` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| `secondary` | `border.static.default.mid` | — see `border.json` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| `info` | `border.static.info.mid` | — see `border.json` | `text.static.info.hi` | `hsl(219, 27%, 40%)` |
| `success` | `border.static.success.mid` | — see `border.json` | `text.static.success.hi` | `hsl(156, 100%, 21%)` |
| `warning` | `border.static.warning.mid` | — see `border.json` | `text.static.warning.hi` | `hsl(42, 75%, 27%)` |
| `danger` | `border.static.danger.mid` | — see `border.json` | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| `alternate` | `border.static.default.mid` | — see `border.json` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Size | Token | Fallback |
|------|-------|---------|
| `small` | `caption-bold` | 12px / weight 600 / line-height 16px |
| `medium` | `body-2-bold` | 14px / weight 600 / line-height 20px |
| `large` | `body-1-bold` | 16px / weight 600 / line-height 24px |

### Spacing

| Size | Property | Token | Value |
|------|----------|-------|-------|
| `small` | Horizontal padding | `2` | 2px |
| `medium` | Horizontal padding | `4` | 4px |
| `large` | Horizontal padding | `4` | 4px |
| all | Vertical padding | — | 0px |
| Border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Tag container | `radius.xs` | 2px |

## Accessibility

- Rendered as `<span>` — it carries no interactive role.
- Variant colours imply semantic meaning — be consistent: `danger` for errors, `success` for confirmations. Do not choose variants for aesthetic reasons.
- Long labels are truncated with ellipsis. Always ensure the full label is available via `title` attribute or surrounding context.
