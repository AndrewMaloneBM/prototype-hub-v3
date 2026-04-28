# RevAccordionList

Covers RevAccordionItem, the individual expandable row within the list. RevAccordionItem is not exposed independently.

## When to use

For content that can be progressively disclosed — FAQs, filter panels, settings groups. Each item has a header row that toggles its body on click.

Do not use accordions to hide essential information the user will always need. Use RevList when rows are navigational rather than expandable.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for the expand/collapse chevron

## Variants

None.

## Props

### RevAccordionList

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `children` | `node` | required | RevAccordionItem components |
| `allowMultiple` | `boolean` | `false` | When `true`, multiple items can be open simultaneously. When `false`, opening one closes the others. |

### RevAccordionItem

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | `string` | required | Header row text |
| `open` | `boolean` | `false` | Controlled open state |
| `disabled` | `boolean` | `false` | Disables toggling |
| `onToggle` | `(open: boolean) → void` | — | Called on open/close |
| `children` | `node` | required | Body content shown when expanded |

## Structure

```
┌────────────────────────────────────────────────┐
│  [Title]                              [Chevron] │
├────────────────────────────────────────────────┤
│  [Body content — visible when open]            │
├────────────────────────────────────────────────┤
│  [Title]                              [Chevron] │
└────────────────────────────────────────────────┘
```

The chevron rotates 180° when the item is open. The body region animates height on open/close.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Header background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Header background | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Header background | disabled | `background.static.default.low` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| Row divider | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Title | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Title | disabled | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Chevron icon | default | `text.static.default.hi` (via currentColor) | `hsl(225, 21%, 7%)` |
| Chevron icon | disabled | `text.static.default.low` (via currentColor) | `hsl(223, 4%, 37%)` |
| Body background | — | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Body text | — | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Title | `body-1-bold` | 16px / weight 600 / line-height 24px |
| Body text | `body-1` | 16px / weight 400 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Header row | Vertical padding | `16` | 16px |
| Header row | Horizontal padding | `16` | 16px |
| Title + chevron | Horizontal gap | `8` | 8px |
| Body | Vertical padding | `16` | 16px |
| Body | Horizontal padding | `16` | 16px |
| Row divider | Width and style | — | 1px solid |

## Accessibility

- Each header is a `<button>` with `aria-expanded` reflecting the open state.
- The body panel is linked to its header via `aria-controls` / `id`.
- When `allowMultiple` is `false`, the list follows the accordion pattern (`role="region"` on each panel).
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
