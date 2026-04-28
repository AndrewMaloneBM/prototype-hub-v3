# Overlays — decision tree

```
Blocking overlay behind a modal or drawer?                     → RevBackdrop

Need a positioned floating surface (no chrome)?                → RevModalBase

Focused task or confirmation requiring a response?
  → Centred modal with title and actions                       → RevDialog
  → Slides in from an edge                                     → RevDrawer

Contextual options triggered from a point on the page?
  → Anchored dropdown menu                                     → RevContextualMenu
  → Brief label on hover/focus                                 → RevTooltip
```

Notes:
- RevBackdrop and RevModalBase are building blocks — prefer RevDialog or RevDrawer for complete overlay patterns.
- RevPortal behaviour (rendering outside the component tree) is implemented internally by RevDialog, RevDrawer, and RevToast. It is not exposed as a standalone component.
