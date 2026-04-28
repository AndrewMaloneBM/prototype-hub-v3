# RevInfoBlock

## When to use

Large embedded feedback block for persistent contextual content within a page layout — informational, success, warning, or danger messages that are tied to a specific section or action.

Do not use for transient feedback — use `RevToast`. Do not use for decisions requiring confirmation — use `RevDialog`. Do not stack multiple RevInfoBlock components in sequence; place each near the content it qualifies.

## Dependencies

- `RevButton` — `guidelines/components/actions/RevButton.md`
- `RevButtonIcon` — `guidelines/components/actions/RevButtonIcon.md`
- `RevToggle` — `guidelines/components/selection/RevToggle.md` (only when `toggleLabel` is used)

RevButton and RevButtonIcon must be implemented before building RevInfoBlock.

## Variants

| Variant | Use |
|---------|-----|
| `default` | Neutral informational content |
| `info` | Informational content with blue tint |
| `success` | Positive outcome or confirmation |
| `danger` | Error or destructive state |
| `warning` | Cautionary, non-critical state |

`variant` must match the semantic meaning of the content — do not choose colours arbitrarily.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `icon` | `component` | required | Leading icon displayed at the start of the block |
| `title` | `string` | required | Primary heading |
| `variant` | `string` | required | Sets background colour — see variants table |
| `caption` | `string` | — | Small secondary text below the title |
| `content` | `string` | — | Body paragraph below the caption |
| `cta` | `string` | — | Primary action button label |
| `onCtaClick` | `() → void` | — | Called when the CTA button is clicked |
| `dismissable` | `boolean` | `false` | Shows a dismiss button |
| `dismissLabel` | `string` | `'Dismiss'` | Accessible label for the dismiss button |
| `onDismiss` | `() → void` | — | Called when dismissed |
| `toggleLabel` | `string` | — | Renders an inline toggle with this label |
| `toggleDescription` | `string` | — | Description text for the inline toggle |
| `toggleChecked` | `boolean` | — | Controlled state for the inline toggle |
| `onToggle` | `() → void` | — | Called when the inline toggle changes |
| `children` | `node` | — | Custom content rendered in the body area |

## Structure

```
┌──────────────────────────────────────────────────────┐
│  [Icon]  [Title]                      [Dismiss?]     │
│          [Caption?]                                  │
│          [Content / Children?]                       │
│          [Toggle label?]          [Toggle?]          │
│          [CTA button?]                               │
└──────────────────────────────────────────────────────┘
```

`[Dismiss?]` renders only when `dismissable` is true. `[Toggle?]` renders only when `toggleLabel` is provided.

## Tokens

### Color

| Variant | Part | Token | Fallback (default mood) |
|---------|------|-------|------------------------|
| `default` | Background | `background.static.default.mid` | `hsl(220, 19%, 94%)` |
| `info` | Background | `background.static.info.mid` | `hsl(221, 86%, 92%)` |
| `success` | Background | `background.static.success.mid` | `hsl(145, 83%, 77%)` |
| `danger` | Background | `background.static.danger.mid` | `hsl(3, 100%, 92%)` |
| `warning` | Background | `background.static.warning.mid` | `hsl(38, 90%, 84%)` |
| all | Title + icon | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| all | Caption | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| all | Body content | `text.static.default.mid` | `hsl(223, 7%, 20%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Title | `body-2-bold` | 14px / weight 600 / line-height 20px |
| Caption | `caption` | 12px / weight 400 / line-height 16px |
| Body content | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Container | Vertical padding | `16` | 16px |
| Container | Leading padding | `16` | 16px |
| Container | Trailing padding | `8` | 8px |
| Icon | Trailing margin | `12` | 12px |
| Content | Vertical gap between sections | `12` | 12px |
| Title area | Vertical gap between title and caption | `8` | 8px |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Block container | `radius.lg` | 12px |

## Accessibility

- `variant` is a visual affordance only — always use clear, descriptive text in `title` and `content` to communicate the message meaning. Do not rely on colour alone.
- The dismiss button requires `dismissLabel` to be set meaningfully (e.g. "Dismiss update notice", not just "Dismiss").
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
