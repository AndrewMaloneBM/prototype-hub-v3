# RevTextList

## When to use

For rendering ordered or unordered lists of plain text items. Suitable for feature lists, bullet points, and step-by-step instructions that are editorial in nature.

Use RevList when rows are interactive, have leading icons or avatars, or carry metadata. RevTextList is strictly for non-interactive text content.

## Dependencies

None.

## Variants

| Variant | Description |
|---------|-------------|
| `unordered` | Bulleted list |
| `ordered` | Numbered list |
| `check` | Checkmark-prefixed list (e.g. feature confirmations) |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `'unordered' \| 'ordered' \| 'check'` | `'unordered'` | List marker type |
| `items` | `string[]` | required | List of text items |

## Structure

```
┌──────────────────────────────────┐
│  [Marker]  [Item text]           │
│  [Marker]  [Item text]           │
│  [Marker]  [Item text]           │
└──────────────────────────────────┘
```

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Item text | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Bullet / number marker | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Check marker | `text.static.success.hi` | `hsl(156, 100%, 21%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Item text | `body-1` | 16px / weight 400 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Items | Vertical gap between items | `8` | 8px |
| Item | Horizontal gap between marker and text | `8` | 8px |

## Accessibility

- Use the semantic list element for the appropriate variant (`<ul>`, `<ol>`).
- Check markers are decorative icons — hide from assistive technology with `aria-hidden="true"`.
