# Selection — decision tree

```
Binary on/off setting that applies immediately?    → RevToggle
Multiple independent options (pick many)?          → RevCheckbox (group)
Single choice from a set (pick one)?               → RevRadio (group)

Interactive filter tag (clickable)?                → RevChip
Read-only content label?                           → RevTag
Status indicator with optional action?             → RevPill

Continuous numeric value?                          → RevSlider
Star-based score display?                          → RevRating
```

Notes:
- For more than 7 options in a single-choice set, use RevInputSelect instead of RevRadio.
- RevTag is never interactive. For clickable tags, use RevChip.
- RevRating is display-only. For a star-input picker, build a custom component.
