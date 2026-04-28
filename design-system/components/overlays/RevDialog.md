# RevDialog

## When to use

A centred modal dialog for focused tasks and confirmations that require an explicit user response before continuing. Blocks all background interaction until dismissed.

Use for destructive confirmations, short forms, and gated actions. Do not use for alerts that do not require an action — use RevBanner or RevToast instead. Keep dialog content short; if the task needs a full-page experience, navigate instead.

Renders its content outside the component tree at the document root (equivalent to React `createPortal`).

## Dependencies

- RevModalBase (`guidelines/components/overlays/RevModalBase.md`)

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `open` | `boolean` | required | Controls visibility |
| `title` | `string` | required | Dialog heading — used as the accessible name |
| `onClose` | `() → void` | — | Called when the close button is clicked, backdrop is clicked, or Escape is pressed |
| `actions` | `node` | — | Buttons rendered in the footer (typically a primary + secondary action) |
| `children` | `node` | required | Dialog body content |

## Structure

```
┌───────────── dialog panel ─────────────┐
│  [Title]                   [CloseBtn]  │
├────────────────────────────────────────┤
│  [Body content]                        │
│                                        │
├────────────────────────────────────────┤
│  [Actions — e.g. Cancel  Confirm]      │
└────────────────────────────────────────┘
```

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Panel background | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Header bottom border | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Footer top border | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Title text | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Body text | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Title | `heading-2` | 20px / weight 600 / line-height 28px |
| Body text | `body-1` | 16px / weight 400 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Header | Vertical padding | `16` | 16px |
| Header | Horizontal padding | `24` | 24px |
| Body | Vertical padding | `24` | 24px |
| Body | Horizontal padding | `24` | 24px |
| Footer | Vertical padding | `16` | 16px |
| Footer | Horizontal padding | `24` | 24px |
| Footer actions | Horizontal gap between buttons | `12` | 12px |
| Header bottom border | Width and style | — | 1px solid |
| Footer top border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Panel | `radius.lg` | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Panel | `shadow.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |

## Accessibility

- The dialog panel must have `role="dialog"`, `aria-modal="true"`, and `aria-labelledby` pointing to the title.
- Focus must be trapped within the panel while open.
- On open, focus moves to the first focusable element (or the panel itself if none).
- On close, focus returns to the trigger element.
- Pressing Escape must call `onClose`.
