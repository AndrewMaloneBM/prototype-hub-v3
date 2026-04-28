# RevList

## When to use

For lists of rich interactive rows. Each row can include a leading element (icon, avatar, or image), primary and secondary text, trailing metadata, and a disclosure chevron for navigation.

Use RevTextList for non-interactive editorial lists. Use RevTable when content is tabular with column headers.

## Dependencies

None. Clickable rows use an internal routing primitive equivalent to RevButtonBase behaviour — `to`, `href`, and `onClick` are supported directly on each row.

## Variants

None. Row content is composed through props.

## Props

### RevList

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `children` | `node` | required | RevListItem components |
| `divided` | `boolean` | `true` | Shows a divider between rows |

### RevListItem

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | required | Primary row text |
| `description` | `string` | — | Secondary text below the label |
| `leading` | `node` | — | Leading element (icon, avatar, image) |
| `trailing` | `node` | — | Trailing content (text, badge, icon) |
| `href` | `string` | — | Makes the row a link to an external URL |
| `to` | `string` | — | Makes the row a link using the application's router |
| `onClick` | `event → void` | — | Makes the row a button |
| `disabled` | `boolean` | `false` | Disables interaction |

## Structure

```
┌────────────────────────────────────────────────┐
│  [Leading?]  [Label]               [Trailing?] │
│              [description?]                    │
├────────────────────────────────────────────────┤
│  [Leading?]  [Label]               [Trailing?] │
│              [description?]                    │
└────────────────────────────────────────────────┘
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Row background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Row background | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Row background | disabled | `background.static.default.low` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| Row divider | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Label | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Label | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Description | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Trailing text | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-1` | 16px / weight 400 / line-height 24px |
| Description | `body-2` | 14px / weight 400 / line-height 20px |
| Trailing text | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Row | Vertical padding | `16` | 16px |
| Row | Horizontal padding | `16` | 16px |
| Leading + text | Horizontal gap | `12` | 12px |
| Text + trailing | Horizontal gap | `12` | 12px |
| Label + description | Vertical gap | `4` | 4px |
| Row divider | Width and style | — | 1px solid |

## Accessibility

- When a row has `href` or `to`, it renders as a link (`<a>`).
- When a row has `onClick` only, it renders as a button (`<button>`).
- Purely presentational rows have no interactive role.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
