# RevBackdrop

## When to use

A full-viewport semi-transparent overlay used to dim background content behind modals, drawers, and other overlay panels. It blocks interaction with the content beneath it.

RevBackdrop is a building block — it is composed automatically by RevModalBase, RevDialog, and RevDrawer. Use it directly only when building a custom overlay that needs a backdrop.

## Dependencies

None.

## Variants

| Variant | Description |
|---------|-------------|
| `hi` | Strong dimming — use for dialogs and drawers that require full focus |
| `low` | Light dimming — use for contextual overlays where background context remains useful |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `'hi' \| 'low'` | `'hi'` | Opacity level |
| `onClick` | `event → void` | — | Called when the backdrop is clicked — typically used to close the overlay |

## Structure

```
┌─────────────────────────────────────────┐
│  [full-viewport dimming surface]        │
└─────────────────────────────────────────┘
```

## Tokens

### Color

| Part | Variant | Token | Fallback (default mood) |
|------|---------|-------|------------------------|
| Backdrop | `hi` | `background.overlay.hi` | `hsla(225, 21%, 7%, 0.85)` |
| Backdrop | `low` | `background.overlay.low` | `hsla(225, 21%, 7%, 0.4)` |

## Accessibility

- The backdrop must not receive keyboard focus.
- It must not trap focus — focus trapping is handled by the overlay content above it.
- Clicking the backdrop to close an overlay is an enhancement only; a close button within the overlay panel is always required.
