# RevButton

## When to use

Standard labelled button for triggering actions. Use when the action needs a visible text label. For icon-only actions use `RevButtonIcon`. For card-shaped interactive surfaces use `RevButtonCard`.

## Dependencies

- `RevSpinner` — `guidelines/components/feedback/RevSpinner.md`
- Icon component (optional) — `guidelines/icons/icons.md`

Both must be implemented before building RevButton.

## Variants

| Variant | Style | Use |
|---------|-------|-----|
| `primary` | Filled — default | Primary CTA on a page or form |
| `primaryDestructive` | Filled — danger | Confirm a destructive action |
| `primarySuccess` | Filled — success | Confirm a positive completion |
| `secondary` | Outlined — default | Secondary action alongside a primary |
| `secondaryDestructive` | Outlined — danger | Secondary destructive action |
| `secondarySuccess` | Outlined — success | Secondary positive action |

Icons are suppressed automatically on `primaryDestructive` and `secondaryDestructive`.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `string` | required | Visual style — see variants table |
| `size` | `'medium' \| 'small'` | `'medium'` | Button size |
| `fullWidth` | `'always' \| 'never' \| 'adaptive'` | `'never'` | Width behaviour. `'adaptive'` is full-width on mobile, auto on `md+` |
| `disabled` | `boolean` | `false` | Disables interaction |
| `loading` | `boolean` | `false` | Shows spinner, hides label, blocks interaction |
| `icon` | `component` | — | Optional icon alongside label. Suppressed on destructive variants. |
| `iconPosition` | `'start' \| 'end'` | `'end'` | Icon position relative to label |
| `loadingAlternativeText` | `string` | `'Loading'` | Accessible label for the loading spinner |
| `to` | `object` | — | Route object — delegates to navigation context |
| `href` | `string` | — | URL string — renders as a hyperlink |
| `replace` | `boolean` | `false` | Replaces the current history entry instead of pushing a new one — the user cannot navigate back to the previous page |
| `type` | `'button' \| 'submit' \| 'reset'` | `'button'` | Button type. Set to `'submit'` when the button sits inside a form and should submit it. |
| `children` | `node` | — | Button label |

When neither `to` nor `href` is set, renders as a button.

## Structure

```
┌──────────────────────────────────────────┐
│  [Icon?]  [Label]  [Icon?]  [Spinner?]  │
└──────────────────────────────────────────┘
```

Icon position is controlled by `iconPosition` (`start` or `end`). When `loading` is true, the label is hidden and the spinner is shown in its place; layout dimensions are preserved.

## Tokens

### Color

Filled variants (`primary`, `primaryDestructive`, `primarySuccess`) follow the same token pattern. The function segment changes: `default` for primary, `danger` for primaryDestructive, `success` for primarySuccess.

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Background | base | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| Background | hover | `background.action.default.hi` (hover state) | `hsl(231, 7%, 21%)` |
| Background | disabled | `background.action.default.hi` (disabled state) | `hsla(225, 21%, 7%, 0.05)` |
| Text | base + hover | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| Text | disabled | `text.onaction.default.hi` (disabled state) | `hsl(223, 3%, 57%)` |

Replace `default` with `danger` for primaryDestructive, or `success` for primarySuccess.

Outlined variants (`secondary`, `secondaryDestructive`, `secondarySuccess`) follow the same pattern with `min` level tokens:

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Background | base | `background.action.default.min` | `hsla(225, 21%, 7%, 0)` |
| Background | hover | `background.action.default.min` (hover state) | `hsla(225, 21%, 7%, 0.06)` |
| Background | disabled | `background.action.default.min` (disabled state) | `hsla(225, 21%, 7%, 0.05)` |
| Text | base + hover | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Text | disabled | `text.action.default.hi` (disabled state) | `hsl(223, 3%, 57%)` |
| Border | base + hover | `border.action.default.hi` | `hsl(223, 7%, 20%)` |
| Border | disabled | `border.action.default.hi` (disabled state) | `hsl(225, 7%, 78%)` |

Replace `default` with `danger` for secondaryDestructive, or `success` for secondarySuccess.

Mood-inverse fallback values are in `guidelines/foundations/colors/background.json`, `text.json`, and `border.json`.

### Typography

| Part | State | Token | Fallback |
|------|-------|-------|---------|
| Label | size `medium` | `body-1-bold` | 16px / weight 600 / line-height 24px |
| Label | size `small` | `body-2-bold` | 14px / weight 600 / line-height 20px |

### Spacing

Outlined variants use 1px less padding on each side to account for the border.

| Size | Variant type | Property | Token | Value |
|------|-------------|----------|-------|-------|
| `medium` | filled | padding (all sides) | `12` | 12px |
| `medium` | outlined | padding (all sides) | `11` | 11px |
| `small` | filled | padding horizontal | `12` | 12px |
| `small` | filled | padding vertical | `6` | 6px |
| `small` | outlined | padding horizontal | `11` | 11px |
| `small` | outlined | padding vertical | `5` | 5px |
| — | — | Horizontal gap — icon to label (medium) | `12` | 12px |
| — | — | Horizontal gap — icon to label (small) | `8` | 8px |
| Border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Button container | `radius.sm` | 6px |

## Accessibility

- When `loading` is true, the label is visually hidden but the button remains in the tab order. The spinner provides an accessible label via `loadingAlternativeText`.
- When `disabled` is true on a button, the element is natively non-interactive. When rendered as a link with `disabled`, `aria-disabled` is set instead.
- Always pair destructive variants with a confirmation step — do not make destructive actions the only or default option.
- Focus ring: `focus.default-hi` — color `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
