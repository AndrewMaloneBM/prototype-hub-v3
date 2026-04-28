# RevTable

## When to use

For displaying structured data with labelled columns and multiple rows. Use when relationships between values across columns matter and users need to compare rows.

Use RevList when rows are navigational items without column structure. Do not use RevTable for single-column lists.

## Dependencies

- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for sortable column header controls

## Variants

None. Column sort and row selection are controlled through props.

## Props

### RevTable

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `columns` | `object[]` | required | Column definitions. Each has `key: string`, `label: string`, and optionally `sortable: boolean` and `align: 'left' \| 'center' \| 'right'`. |
| `rows` | `object[]` | required | Row data. Each object maps column keys to cell content (`node`). |
| `sortKey` | `string` | — | Currently sorted column key |
| `sortDirection` | `'asc' \| 'desc'` | — | Current sort direction |
| `onSort` | `(key: string, direction: 'asc' \| 'desc') → void` | — | Called when a sortable column header is clicked |
| `caption` | `string` | — | Accessible table caption |

## Structure

```
┌──────────────────────────────────────────────────────┐
│  [ColumnHeader ▲]  [ColumnHeader]  [ColumnHeader ▼]  │
├──────────────────────────────────────────────────────┤
│  [Cell]            [Cell]          [Cell]             │
├──────────────────────────────────────────────────────┤
│  [Cell]            [Cell]          [Cell]             │
└──────────────────────────────────────────────────────┘
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Header background | — | `background.static.default.mid` | `hsl(220, 19%, 94%)` |
| Header text | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Header sort icon | active | `text.static.default.hi` (via currentColor) | `hsl(225, 21%, 7%)` |
| Header sort icon | inactive | `text.static.default.low` (via currentColor) | `hsl(223, 4%, 37%)` |
| Row background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Row background | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Row background | alternate (optional) | `background.static.default.mid` | `hsl(220, 19%, 94%)` |
| Row divider | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Cell text | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Cell text | secondary | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Column header | `body-2-bold` | 14px / weight 600 / line-height 20px |
| Cell text | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Header cell | Vertical padding | `12` | 12px |
| Header cell | Horizontal padding | `16` | 16px |
| Body cell | Vertical padding | `16` | 16px |
| Body cell | Horizontal padding | `16` | 16px |
| Row divider | Width and style | — | 1px solid |

## Accessibility

- Always provide a `caption` for screen readers, even if it is visually hidden.
- Sortable headers are `<button>` elements with `aria-sort` set to `"ascending"`, `"descending"`, or `"none"`.
- The table must use semantic `<table>`, `<thead>`, `<tbody>`, `<th>`, and `<td>` elements.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
