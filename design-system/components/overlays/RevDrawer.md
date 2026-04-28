# RevDrawer

## When to use

A panel that slides in from the edge of the viewport. Use for secondary task flows, filter panels, and navigation menus that need more space than a dialog but should not navigate away from the current page.

Use RevDialog for brief confirmations or short forms. Use a full page navigation for tasks complex enough to require their own URL.

Renders its content outside the component tree at the document root (equivalent to React `createPortal`).

## Dependencies

- RevModalBase (`guidelines/components/overlays/RevModalBase.md`)

## Variants

| Variant | Description |
|---------|-------------|
| `right` | Slides in from the right edge |
| `left` | Slides in from the left edge |
| `bottom` | Slides up from the bottom edge |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `open` | `boolean` | required | Controls visibility |
| `title` | `string` | required | Drawer heading — used as the accessible name |
| `variant` | `'right' \| 'left' \| 'bottom'` | `'right'` | Slide-in direction |
| `onClose` | `() → void` | — | Called when the close button is clicked, backdrop is clicked, or Escape is pressed |
| `actions` | `node` | — | Optional footer buttons |
| `children` | `node` | required | Drawer body content |

## Structure

Right variant:

```
┌──────── viewport ───────────────────┐
│  [RevBackdrop]       ┌─── panel ──┐ │
│                      │ [Title] [X]│ │
│                      │            │ │
│                      │ [Body]     │ │
│                      │            │ │
│                      │ [Actions?] │ │
│                      └────────────┘ │
└─────────────────────────────────────┘
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
| Panel width (right/left) | — | — | 400px (capped at 100vw on small viewports) |
| Header bottom border | Width and style | — | 1px solid |
| Footer top border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Panel top corners (bottom variant) | `radius.lg` | 12px |
| Panel left corners (right variant) | `radius.lg` | 12px |
| Panel right corners (left variant) | `radius.lg` | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Panel | `shadow.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |

## Accessibility

- The drawer panel must have `role="dialog"`, `aria-modal="true"`, and `aria-labelledby` pointing to the title.
- Focus must be trapped within the panel while open.
- On open, focus moves to the first focusable element.
- On close, focus returns to the trigger element.
- Pressing Escape must call `onClose`.
