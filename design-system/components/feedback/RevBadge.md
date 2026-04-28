# RevBadge

## When to use

Small count or status indicator. Use for notification counts, status dots, and quantity indicators positioned alongside an icon or label.

Do not use as a standalone interactive element — if the badge needs to trigger an action, use `RevButtonIcon` with `hasBadge` instead.

## Dependencies

None.

## Variants

Controlled by the `variant` prop.

| Variant | Use |
|---------|-----|
| `danger` | Errors, alerts, urgent notifications |
| `warning` | Cautionary states |
| `success` | Completions, confirmations |
| `info` | Neutral counts and indicators |
| `accent` | Highlighted count (lime tint) |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `string` | `'info'` | Background colour — see variants table |
| `count` | `number` | `0` | Count to display. `0` renders a plain dot with no number. |
| `maxCount` | `number` | `99` | Counts above this threshold display as `maxCount+` |
| `size` | `'small' \| 'medium' \| 'large'` | `'large'` | Dot size when `count` is `0`. Has no effect when a count is shown. |
| `ariaLabel` | `string` | — | Accessible label for the badge |
| `ariaLabelledby` | `string` | — | ID of an element that labels this badge |

## Structure

Count shown (`count` > 0):

```
╭──────────────╮
│   [Count]    │
╰──────────────╯
```

Dot only (`count` = 0):

```
╭────╮
│    │
╰────╯
```

## Tokens

### Color

| Variant | Part | Token | Fallback (default mood) |
|---------|------|-------|------------------------|
| `danger` | Background | `background.static.danger.hi` | `hsl(2, 100%, 85%)` |
| `warning` | Background | `background.static.warning.hi` | `hsl(39, 70%, 69%)` |
| `success` | Background | `background.static.success.hi` | `hsl(149, 67%, 61%)` |
| `info` | Background | `background.static.info.hi` | `hsl(219, 65%, 82%)` |
| `accent` | Background | `background.static.info.max` | `hsl(70, 88%, 73%)` |
| all | Text | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Count label | `caption-bold` | 12px / weight 600 / line-height 16px |

### Spacing

| State | Property | Value |
|-------|----------|-------|
| Dot only (`count` = 0) — small | Width × Height | 6 × 6px |
| Dot only (`count` = 0) — medium | Width × Height | 8 × 8px |
| Dot only (`count` = 0) — large | Width × Height | 12 × 12px |
| Count shown | Min width | 20px |
| Count shown | Padding horizontal | spacing token `4` (4px) |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Badge container | `radius.lg` | 12px |

## Accessibility

- Updates to `count` are announced to screen readers automatically via `aria-live="polite"`.
- Always provide `ariaLabel` or `ariaLabelledby` when the badge conveys meaning beyond a decorative count — for example "3 unread messages" rather than just "3".
- `variant` implies semantic meaning — be consistent across the product. Do not use `danger` for non-error states or `success` for non-completion states.
