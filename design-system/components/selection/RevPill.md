# RevPill

## When to use

Compact status indicator, optionally actionable. Use for condition labels, status badges, and short contextual labels that may or may not be clickable.

For interactive filter tags use RevChip. For read-only content labels use RevTag.

## Dependencies

None.

## Variants

| Variant | Use |
|---------|-----|
| `default` | Neutral status |
| `success` | Positive / confirmed state |
| `danger` | Error / destructive state |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | — | Visible text |
| `size` | `'small' \| 'medium' \| 'large'` | `'medium'` | Dimensions — see size table |
| `variant` | `string` | `'default'` | Colour — see variants table |
| `isActionable` | `boolean` | `false` | Renders as a button with hover styles |
| `showChevron` | `boolean` | `false` | Shows a trailing chevron. Only when `isActionable` is true. |
| `prefixIcon` | `component` | — | Leading icon |
| `ariaLabel` | `string` | — | Accessible label override. Falls back to `label`. |
| `onClick` | `event → void` | — | Only fires when `isActionable` is true |

## Structure

```
╭───────────────────────────────────────╮
│  [prefixIcon?]  [Label]  [chevron?]   │
╰───────────────────────────────────────╯
```

## Tokens

### Color

| Variant | Part | Token | Fallback (default mood) |
|---------|------|-------|------------------------|
| `default` | Background | `background.static.default.mid` | `hsl(220, 19%, 94%)` |
| `default` | Text | `text.static.default.mid` | `hsl(223, 7%, 20%)` |
| `success` | Background | `background.static.success.low` | `hsl(139, 85%, 90%)` |
| `success` | Text | `text.static.success.hi` | `hsl(156, 100%, 21%)` |
| `danger` | Background | `background.static.danger.low` | `hsl(6, 100%, 96%)` |
| `danger` | Text | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |

When `isActionable` is true, each variant gains a hover background state — see `background.json` for the hover values.

### Typography

| Size | Token | Fallback |
|------|-------|---------|
| `small` | `caption` | 12px / weight 400 / line-height 16px |
| `medium` | `body-2` | 14px / weight 400 / line-height 20px |
| `large` | `body-1` | 16px / weight 400 / line-height 24px |

### Spacing

| Size | Property | Value |
|------|----------|-------|
| `small` | Height | 28px |
| `small` | Horizontal padding (no icon) | 6px each side |
| `small` | Leading padding (with icon) | 10px |
| `small` | Trailing padding (with icon) | 8px |
| `medium` | Height | 36px |
| `medium` | Horizontal padding (no icon) | 10px each side |
| `medium` | Leading padding (with icon) | 12px |
| `medium` | Trailing padding (with icon) | 8px |
| `large` | Height | 42px |
| `large` | Horizontal padding (no icon) | 12px each side |
| `large` | Leading padding (with icon) | 16px |
| `large` | Trailing padding (with icon) | 10px |
| all | Horizontal gap between icon and label | `4`–`8` (varies by size) |

### Spacing — icon sizes

| Size | Icon size |
|------|-----------|
| `small` | 16px |
| `medium` | 20px |
| `large` | 24px |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Pill container | `radius.round` | 9999px |

## Accessibility

- When `isActionable` is false, rendered as `<span>` — no interactive role.
- When `isActionable` is true, rendered as `<button>` — provide `ariaLabel` if `label` alone is insufficient to describe the action.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
