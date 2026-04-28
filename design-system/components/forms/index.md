# Forms — decision tree

```
Need a wrapper for inputs that submit together?     → RevForm

What type of value are you collecting?
  Single-line freeform text                         → RevInputText
  Multi-line freeform text                          → RevInputTextarea
  Number with increment/decrement controls          → RevInputNumber
  Password (masked entry)                           → RevInputPassword
  Phone number with country code selector           → RevInputPhone
  Date with calendar picker                         → RevInputDate
  Single choice from a predefined list              → RevInputSelect
  Single choice from a long list (with filtering)   → RevInputSelectSearchable
  Freeform text with dynamic suggestions            → RevInputAutocomplete
  Multiple choices from a predefined list           → RevInputMultiSelect
```

Notes:
- For binary choices that apply immediately (no submit), use RevToggle (see `selection/`).
- For in-form yes/no or multi-select, use RevCheckbox (see `selection/`).
- For in-form single-select with 2–7 options visible at once, use RevRadio (see `selection/`).
- For more than 7 options or when space is limited, use RevInputSelect.
