# Form

## When to use

When collecting multiple fields that submit together as a single operation. Wrap all fields and the submit action in `RevForm` so validation and error suppression work correctly as a unit.

Do not use `RevForm` for a single toggle or immediate-effect control — those do not need a submit context. For a form inside a dialog, see the `modal-form` pattern.

## Components involved

| Component | File | Role |
|-----------|------|------|
| RevForm | `components/forms/RevForm.md` | Wrapper — coordinates validation and error suppression |
| RevButton | `components/actions/RevButton.md` | Submit action |

Other input components sit inside `RevForm` depending on the data being collected. Common examples:

| Component | File | Use |
|-----------|------|-----|
| RevInputText | `components/forms/RevInputText.md` | Single-line freeform text |
| RevInputSelect | `components/forms/RevInputSelect.md` | Single-choice dropdown |
| RevInputTextarea | `components/forms/RevInputTextarea.md` | Multi-line text |
| RevInputNumber | `components/forms/RevInputNumber.md` | Numeric input with controls |
| RevCheckbox | `components/selection/RevCheckbox.md` | In-form multi-select or agreement |
| RevRadio | `components/selection/RevRadio.md` | In-form single-select (2–7 options) |

## Structure

```
┌────────────────────────────────────────────┐
│  [Label]                                   │
│  [Input field]                             │
│  [Helper text / error?]                    │
│                                            │
│  [Label]                                   │
│  [Input field]                             │
│  [Helper text / error?]                    │
│                                            │
│  [Submit button]                           │
└────────────────────────────────────────────┘
```

## Assembly

1. Wrap all fields in `RevForm`. Pass an `onSubmit` handler that receives the validated field values.
2. Give each input an `id` and a visible `label`. Never rely on placeholder text as the only label.
3. Wire each input's `errorMessage` to the validation result for that field. `RevForm` suppresses these until the first submit attempt.
4. Place one primary `RevButton` with `type="submit"` inside the form. Label it with a specific action verb ("Save address", "Place order") — not "Submit".
5. Mark optional fields with the word "Optional" — do not mark all required fields individually.

## Rules

- One submit button per form, with `type="submit"`.
- `RevForm` suppresses field errors until the first submit. Do not show errors on field blur before the first submit attempt.
- If the form is inside a dialog, pass an `id` to `RevForm` and reference it via `form=` on the submit button in the dialog footer — see the `modal-form` pattern.
- See `content/microcopy.md` for label, helper text, and error message copy rules.
