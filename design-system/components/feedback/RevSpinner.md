# RevSpinner

## When to use

Animated loading indicator for indeterminate operations — when you know something is loading but not how long it will take. Use inside buttons while an action is in progress, or as a full-page indicator for brief transitions.

Prefer `RevSkeleton` over `RevSpinner` for content areas — skeletons communicate structure and reduce perceived latency better than a spinning icon.

## Dependencies

None. RevSpinner uses the icon system internally but has no Rev component dependencies.

## Variants

None. RevSpinner has a single style. Colour is inherited from the surrounding context.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `size` | `'small' \| 'medium' \| 'large'` | `'medium'` | Controls the spinner dimensions |
| `alternativeText` | `string` | `'Loading'` | Accessible label announced to screen readers |

## Structure

```
┌────────────────┐
│   [Spinner]    │
└────────────────┘
```

The spinner is a single animated icon element. Its colour is inherited from the surrounding context via `currentColor`.

## Tokens

### Spacing

| Size | Dimensions |
|------|------------|
| `small` | 16 × 16px |
| `medium` | 24 × 24px |
| `large` | 48 × 48px |

## Accessibility

- `alternativeText` is announced via `aria-label`. Always set a meaningful label for full-page spinners — "Loading" is acceptable for inline use but "Loading order details" is better for full-page.
- Colour inherits from the parent's text colour token (`currentColor`) — never set a colour directly on the spinner.
- Do not place multiple spinners in the same view simultaneously.
