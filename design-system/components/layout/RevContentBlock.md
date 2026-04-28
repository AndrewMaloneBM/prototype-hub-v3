# RevContentBlock

## When to use

Structured editorial section combining a heading, optional surtitle, image, body copy, and up to two action buttons. Use for marketing and informational sections that follow a consistent heading + content + CTA pattern.

Keep to one primary action per block. Keep headings concise and body copy to short paragraphs.

## Dependencies

- `RevButton` — `guidelines/components/actions/RevButton.md`
- `RevImage` — `guidelines/components/media/RevImage.md`

Both must be implemented before building RevContentBlock.

## Variants

Controlled by `titleVariant` rather than a `variant` prop.

| `titleVariant` | Typography token | Use |
|----------------|-----------------|-----|
| `punchline` | `punchline` | Hero or marketing headline |
| `title1` | `heading-1` | Standard section heading (default) |
| `title2` | `heading-2` | Subsection heading |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | `string` | required | Section heading |
| `titleTag` | `'h2' \| 'h3' \| 'h4'` | `'h2'` | Semantic heading level — choose based on document outline, not visual size |
| `titleVariant` | `'punchline' \| 'title1' \| 'title2'` | `'title1'` | Typography scale for the heading |
| `surtitle` | `string` | — | Small label rendered above the heading |
| `imageProps` | `object` | — | Section image — `{ src, alt, width?, height? }` |
| `imageLeft` | `boolean` | `false` | Places the image on the left on `md+`. Default is right. |
| `hasRoundedContainer` | `boolean` | `false` | Rounds the outer container |
| `hasRoundedImage` | `boolean` | `false` | Rounds the image |
| `buttonLabel` | `string` | — | Primary button label. Button only renders when this is provided. |
| `buttonTo` | `string` | — | Primary button navigation target |
| `buttonLoading` | `boolean` | `false` | Primary button loading state |
| `buttonDisabled` | `boolean` | `false` | Primary button disabled state |
| `onButtonClick` | `() → void` | — | Primary button click handler |
| `secondaryButtonLabel` | `string` | — | Secondary button label. Button only renders when this is provided. |
| `secondaryButtonTo` | `string` | — | Secondary button navigation target |
| `onSecondaryButtonClick` | `() → void` | — | Secondary button click handler |
| `children` | `node` | — | Body copy |

## Structure

Default (`imageLeft: false`, image on the right at `md+`):

```
┌──────────────────────────────────────────────────────────┐
│  [Surtitle?]                             [Image?]        │
│  [Title]                                                 │
│  [Children — body]                                       │
│  [PrimaryBtn?]  [SecondaryBtn?]                          │
└──────────────────────────────────────────────────────────┘
```

`imageLeft: true` (image on the left at `md+`):

```
┌──────────────────────────────────────────────────────────┐
│  [Image?]  [Surtitle?]                                   │
│            [Title]                                       │
│            [Children — body]                             │
│            [PrimaryBtn?]  [SecondaryBtn?]                │
└──────────────────────────────────────────────────────────┘
```

On mobile the image always stacks above the text regardless of `imageLeft`.

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Heading | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Surtitle | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Body copy | `text.static.default.mid` | `hsl(223, 7%, 20%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Surtitle | `body-2` | 14px / weight 400 / line-height 20px |
| Heading — `punchline` | `punchline` | 42px (56px on `md+`) / weight 600 |
| Heading — `title1` | `heading-1` | 24px (28px on `md+`) / weight 600 |
| Heading — `title2` | `heading-2` | 20px (22px on `md+`) / weight 600 |
| Body copy | `body-1` | 16px / weight 400 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Surtitle | Bottom margin | `4` | 4px |
| Heading | Bottom margin | `8` | 8px |
| Button group | Top margin | `20` | 20px |
| Button group | Horizontal gap between buttons | `12` | 12px |

### Radius

| Condition | Surface | Token | Fallback |
|-----------|---------|-------|---------|
| `hasRoundedContainer` | Outer container | `radius.lg` | 12px |
| `hasRoundedImage` | Image wrapper | `radius.lg` | 12px |

## Accessibility

- Always set `titleTag` to match the document heading hierarchy — do not choose it based on visual size.
- Always provide a descriptive `alt` in `imageProps`. Use `alt=""` only for decorative images.
- Primary button takes `primary` variant; secondary button takes `secondary` variant — do not override this.
