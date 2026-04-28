# RevSlider

## When to use

Continuous range input for numeric values — price filters, volume, intensity. Always fully controlled: `value` must be managed externally.

## Dependencies

None.

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | required | Accessible label for the slider thumb |
| `value` | `number` | required | Controlled current value |
| `min` | `number` | `0` | Minimum value |
| `max` | `number` | required | Maximum value |
| `step` | `number` | `1` | Snap increment |
| `disabled` | `boolean` | `false` | Disables interaction |
| `showSteps` | `boolean` | `false` | Renders visual step dots along the track |
| `onChange` | `number → void` | — | Called with the new value on interaction |

## Structure

```
┌──────────────────────────────────────────────────┐
│  ●━━━━━━━━━━━━━━━○  [step dots?]  ○──────────○   │
│                 ▲                                 │
│              [Thumb]                             │
└──────────────────────────────────────────────────┘
```

The filled portion extends from the left edge to the thumb position. The thumb is draggable and keyboard-navigable.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Track (unfilled) | enabled | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Track (filled portion) | enabled | `border.static.default.hi` | `hsl(223, 7%, 20%)` |
| Thumb border | enabled | `border.action.default.hi` | `hsl(223, 7%, 20%)` |
| Thumb | hover | `background.action.default.low` (hover state) | `hsl(220, 19%, 94%)` |
| Thumb | hover | `elevation.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |
| Step dots | disabled | `background.action.default.low` (disabled state) | — see `background.json` |

### Spacing

| Part | Property | Value |
|------|----------|-------|
| Track | Width | 100% of container |
| Thumb | Size | 28 × 28px |
| Step dots | Size | 12 × 12px |
| Thumb border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Track | `radius.sm` | 6px |
| Thumb | `radius.round` | 9999px |
| Step dots | `radius.round` | 9999px |

## Accessibility

- `label` is applied as `aria-label` on the thumb element.
- Keyboard navigation is built in: Arrow Right/Up increments, Arrow Left/Down decrements, Home jumps to `min`, End jumps to `max`.
- `aria-valuemin`, `aria-valuemax`, and `aria-valuenow` are set automatically from props.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
