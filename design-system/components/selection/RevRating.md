# RevRating

## When to use

Read-only star rating display for scores and review counts. Use on product cards, review summaries, and seller profiles.

This component is display-only — it has no interactive state. For a star-input picker, build a custom component using icons and RevCheckbox.

## Dependencies

None.

## Variants

None. Size is controlled by the `size` prop.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `score` | `number` | required | Rating value, 0–5. Half stars appear at 0.5 increments. Values outside 0–5 are clamped. |
| `showScoreLabel` | `boolean` | `true` | Shows `score/5` text beside the stars |
| `totalReviews` | `string` | — | Review count displayed in parentheses beside the score |
| `size` | `'extra-small' \| 'small' \| 'medium'` | `'medium'` | Controls star size and label typography |
| `ratingAriaLabel` | `string` | — | Overrides the default accessible label (`"X out of 5"`) |
| `to` | `string` | — | When provided, wraps `totalReviews` in a link |

## Structure

```
┌──────────────────────────────────────────────┐
│  [★★★★½]  [score/5]  [(totalReviews?)]       │
└──────────────────────────────────────────────┘
```

Stars render as filled, half, and empty icons automatically based on `score`.

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Stars + score label | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Total reviews text | `text.action.default.low` | `hsl(223, 4%, 33%)` |

Star colour inherits from `text.action.default.hi` via `currentColor`.

### Typography

| Size | Score label token | Fallback |
|------|------------------|---------|
| `extra-small` | `caption-bold` | 12px / weight 600 / line-height 16px |
| `small` | `body-2-bold` | 14px / weight 600 / line-height 20px |
| `medium` | `heading-3` | 18px / weight 600 / line-height 24px |

Total reviews uses the same typography token as the score label for each size.

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Stars + score | Horizontal gap | `4` | 4px |
| Score + total reviews | Horizontal gap | `4` | 4px |

### Spacing — star icon sizes

| Size | Star icon size |
|------|---------------|
| `extra-small` | 12px |
| `small` | 16px |
| `medium` | 24px |

## Accessibility

- The entire rating is exposed as `role="img"` with an accessible label (default: `"X out of 5"`).
- The star icons are `aria-hidden` — screen readers announce the label only, not individual stars.
- Always provide a meaningful `ratingAriaLabel` when the score alone is insufficient context (e.g. "Seller rating: 4.5 out of 5").
- When `to` is set on `totalReviews`, the link must have a descriptive label — not just the count number.
