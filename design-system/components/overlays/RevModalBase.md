# RevModalBase

## When to use

A positioned floating surface rendered above the page — with no header, footer, or close button. RevModalBase provides the container shape, elevation, and backdrop integration. It is a building block for RevDialog and RevDrawer.

Use RevDialog or RevDrawer instead of RevModalBase directly unless you need a fully custom overlay layout.

Renders its content outside the component tree at the document root (equivalent to React `createPortal`).

## Dependencies

- RevBackdrop (`guidelines/components/overlays/RevBackdrop.md`)
- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — available for use within custom content placed inside the modal

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `open` | `boolean` | required | Controls visibility |
| `backdropVariant` | `'hi' \| 'low'` | `'hi'` | Passed to RevBackdrop |
| `onClose` | `() → void` | — | Called when the backdrop is clicked or Escape is pressed |
| `children` | `node` | required | Overlay content |

## Structure

```
┌─────────── viewport ───────────┐
│  [RevBackdrop]                 │
│  ┌─────── floating panel ────┐ │
│  │  [children]               │ │
│  └───────────────────────────┘ │
└────────────────────────────────┘
```

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Panel background | `background.float.default.low` | `hsl(0, 0%, 100%)` |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Panel | `radius.lg` | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Panel | `shadow.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |

## Accessibility

- Focus must be trapped within the open overlay panel.
- Pressing Escape must call `onClose`.
- When closed, focus must return to the element that triggered the overlay.
- The panel must have `role="dialog"` and `aria-modal="true"`.
