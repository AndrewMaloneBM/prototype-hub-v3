# RevDocumentList

## When to use

A layout container for multiple `RevDocument` items. Supports two display modes: a responsive grid that fills the available container, and a horizontally scrollable inline row.

Use `RevDocument` directly when displaying a single file.

## Dependencies

- RevDocument (`guidelines/components/documents/RevDocument.md`)

## Variants

| Variant | Description |
|---------|-------------|
| `grid` | Responsive grid: 1 column on small viewports, 2 columns on medium and above. Items wrap to a new row as the container fills. |
| `inline` | Horizontally scrollable row with snap scrolling. Items have a constrained width range. The wrapper bleeds into surrounding horizontal padding to reach the viewport edge. |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `'grid' \| 'inline'` | `'grid'` | Layout mode |
| `documents` | `node[]` | required | The RevDocument items to display. |

## Structure

Grid variant:

```
┌──────────────────────────────────────────────────────────┐
│  [RevDocument]          [RevDocument]                    │
│  [RevDocument]          [RevDocument]                    │
│  [RevDocument]                                           │
└──────────────────────────────────────────────────────────┘
```

Inline variant:

```
◀ ─────────────────────────────────────────────────────── ▶
  [RevDocument]  [RevDocument]  [RevDocument]  [RevDocument]
  ←── horizontally scrollable, snaps per item ──→
```

## Tokens

### Spacing

| Part | Property | Token | Fallback value |
|------|----------|-------|----------------|
| Items | Horizontal gap (inline) | `16` | 16px |
| Items | Vertical gap (grid) | `16` | 16px |
| Item (inline) | Minimum width | `240` | 240px |
| Item (inline) | Maximum width | `448` | 448px |

## Accessibility

- `RevDocumentList` is a layout container. Each `RevDocument` within it carries its own accessible semantics.
- If the list is dynamic (uploads can be added or removed), announce changes to screen readers via a live region (e.g. "2 files attached").
