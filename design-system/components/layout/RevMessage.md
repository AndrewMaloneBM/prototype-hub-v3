# RevMessage

## When to use

Conversational message bubble for chat threads and message history UIs. Use when displaying a sequence of messages from identifiable senders.

This is not a notification component — do not use for alerts, status feedback, or system messages. Use `RevBanner` or `RevInfoBlock` for those.

## Dependencies

- `RevAvatar` — `guidelines/components/media/RevAvatar.md`
- `RevTag` — `guidelines/components/selection/RevTag.md`

Both must be implemented before building RevMessage.

## Variants

| Variant | Sender identity |
|---------|----------------|
| `customer` | End user / buyer |
| `seller` | Merchant / seller |
| `backmarket` | Back Market support |

Variant drives per-sender styling consistently. Do not override colours manually.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `string` | required | Sender identity — see variants table |
| `label` | `string` | required | Sender name. Also used as the avatar fallback initial. |
| `tag` | `string` | — | Optional label rendered beside the sender name |
| `timestamp` | `Date` | — | Message time, formatted as HH:MM using the active locale |
| `locale` | `string` | `'en-US'` | BCP 47 locale for timestamp formatting |
| `visibility` | `string` | — | Visibility status text (e.g. "Visible to buyer") |
| `children` | `node` | — | Message body. Line breaks are preserved. |
| `documents` | `node` | — | Attached documents. Rendered in a 3-column grid on `lg+`. |
| `appendix` | `node` | — | Additional content appended after the message body |

## Structure

```
┌──────────────────────────────────────────────────────┐
│  [Avatar]  [Sender name]  [Tag?]          [Time?]    │
│            [Visibility?]                             │
│            [Message body]                            │
│            [Documents?]                              │
│            [Appendix?]                               │
└──────────────────────────────────────────────────────┘
```

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Sender name | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Message body | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Timestamp | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Visibility text | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Sender name | `body-1-bold` | 16px / weight 600 / line-height 24px |
| Message body | `body-1` | 16px / weight 400 / line-height 24px |
| Timestamp | `body-1` | 16px / weight 400 / line-height 24px |
| Visibility text | `body-2-bold` | 14px / weight 600 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Avatar + content | Horizontal gap | `12` | 12px |
| Header | Bottom margin | `4` | 4px |
| Sender name + tag | Horizontal gap | `8` | 8px |
| Message body | Bottom margin | `16` | 16px |
| Documents | Bottom margin | `16` | 16px |
| Documents grid | Gap — all sides | `16` | 16px |

## Accessibility

- Rendered as `<article>` — each message is a self-contained piece of content.
- Timestamp uses a `<time>` element — ensure the displayed text matches the `datetime` value.
- Group consecutive messages from the same sender with tighter spacing to signal continuity without repeating the sender avatar.
- `locale` affects only timestamp formatting — wire it to the application's active locale from the context (see `guidelines/context.md`).
