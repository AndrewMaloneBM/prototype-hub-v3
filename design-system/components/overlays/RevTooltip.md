# RevTooltip

## When to use

A small floating label that provides supplementary information about an element. Appears on hover or keyboard focus. Disappears when focus moves away.

Use only for genuinely supplementary content — if the information is essential, put it in the interface directly (e.g. as a hint below an input). Do not put interactive content (links, buttons) inside a tooltip. Do not use tooltips on mobile-only flows — hover is unavailable on touch devices.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for the optional trigger icon

## Variants

| Variant | Description |
|---------|-------------|
| `dark` | Dark background (default) — use on light surfaces |
| `light` | Light background — use on dark surfaces (mood-inverse) |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `content` | `string` | required | Tooltip text |
| `placement` | `'top' \| 'bottom' \| 'left' \| 'right'` | `'top'` | Preferred position relative to the trigger |
| `variant` | `'dark' \| 'light'` | `'dark'` | Color scheme |
| `children` | `node` | required | The trigger element |

## Structure

```
          ┌────────────────┐
          │  [Tooltip text]│
          └───────▼────────┘
          [Trigger element]
```

The tooltip arrow points toward the trigger. Position flips automatically if the preferred placement does not fit the viewport.

## Tokens

### Color

| Part | Variant | Token | Fallback (default mood) |
|------|---------|-------|------------------------|
| Panel background | `dark` | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| Panel background | `light` | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Panel border | `light` | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Tooltip text | `dark` | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| Tooltip text | `light` | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Tooltip text | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Panel | Vertical padding | `8` | 8px |
| Panel | Horizontal padding | `12` | 12px |
| Panel | Offset from trigger | `8` | 8px |
| Panel border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Panel | `radius.sm` | 6px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Panel | `shadow.middle` | `0px 4px 8px 0px rgba(0, 0, 0, 0.08)` |

## Accessibility

- The tooltip content is linked to its trigger via `aria-describedby`.
- The tooltip panel must not receive focus — it is purely supplementary.
- Do not use a tooltip as the sole accessible label for an icon button; use `aria-label` on the button directly.
- Tooltip content must also appear on keyboard focus (not hover alone).
