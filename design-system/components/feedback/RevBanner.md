# RevBanner

## When to use

Full-width page-level notification for persistent, informational messages. Place immediately below the page header, above all page content.

Do not use for transient feedback after an action — use `RevToast`. Do not use for decisions requiring confirmation — use `RevDialog`.

## Dependencies

- `RevButtonIcon` — `guidelines/components/actions/RevButtonIcon.md`

Must be implemented before building RevBanner (used for the close button).

## Variants

None. RevBanner has a single visual style. The `mood` prop shifts the entire colour context when a genuine theme change is needed.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | — | Primary message text |
| `cta` | `string` | — | Call-to-action link label shown inline beside the label |
| `to` | `string` | — | When provided, makes the entire banner a single clickable link |
| `mood` | `'default' \| 'inverse'` | — | Overrides the mood context for the banner |
| `onClose` | `event → void` | — | When provided, shows a close button at the trailing edge |
| `closeAlternativeText` | `string` | `'Close'` | Accessible label for the close button |
| `children` | `node` | — | Custom content rendered before `label` |

When `to` is set, the entire banner surface is the link hit area — do not place competing interactive elements inside `label` or `cta`.

## Structure

```
┌──────────────────────────────────────────────────────────┐
│  [Children?]  [Label]  [CTA link?]           [Close?]   │
└──────────────────────────────────────────────────────────┘
```

The banner is full-width. `[Close?]` renders only when `onClose` is provided and is pinned to the trailing edge.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Background | base | `background.static.info.hi` | `hsl(219, 65%, 82%)` |
| Background | hover (when `to` is set) | `background.static.info.hi` (hover state) | `hsl(219, 49%, 75%)` |
| Text + CTA | base | `text.action.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Label | `body-2` | 14px / weight 400 / line-height 20px |
| CTA link | `body-2-link` | 14px / weight 600 / line-height 20px / underlined |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Content area | Vertical padding | `16` | 16px |
| Content area | Leading padding (mobile) | `24` | 24px |
| Content area | All sides (desktop `md+`) | `16` | 16px |
| Close button | Trailing margin | `8` | 8px |

## Accessibility

- Rendered as `<aside>` — it is a complementary landmark, not an alert.
- Always provide `onClose` so users can dismiss the banner if it is not critical.
- When `to` is set, the entire banner is a single interactive element. Do not nest additional links or buttons inside it.
- Focus ring on close button: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
