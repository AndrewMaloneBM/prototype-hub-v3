# Modal form

## When to use

When a secondary task must be completed before the user can continue, but a full page change would break context. Common examples: editing an address, updating a payment method, confirming a destructive action with additional input.

Do not use for primary checkout or onboarding flows — those warrant dedicated pages. Do not nest a modal form inside another modal.

## Components involved

| Component | File | Role |
|-----------|------|------|
| RevDialog | `components/overlays/RevDialog.md` | Overlay container with title, body, and footer slot |
| RevForm | `components/forms/RevForm.md` | Coordinates validation inside the dialog body |
| RevButton | `components/actions/RevButton.md` | Submit and cancel actions in the footer |

Input components inside `RevForm` follow the same conventions as the `form` pattern.

## Structure

```
┌──────────────────────────────────────────────────┐
│  [Dialog title]                      [Close btn] │
├──────────────────────────────────────────────────┤
│  [Label]                                         │
│  [Input field]                                   │
│  [Helper text / error?]                          │
│                                                  │
│  [Label]                                         │
│  [Input field]                                   │
├──────────────────────────────────────────────────┤
│  [Cancel button]              [Submit button]    │
└──────────────────────────────────────────────────┘
```

## Assembly

1. Place `RevDialog` with `open` controlled by the parent and `onClose` wired to the cancel action.
2. Give `RevForm` a unique `id`. Place it in the dialog body with the form fields inside.
3. Place the submit `RevButton` (variant `primary`) in the dialog `footer` slot. Set its `form` attribute to match the `RevForm` id — this wires the button to the form without nesting it inside the dialog body.
4. Place a cancel `RevButton` (variant `secondary`) alongside the submit button in the footer. Wire it to `onClose`.
5. Wire each input's `errorMessage` to the validation result for that field.

## Rules

- Always provide a cancel path — via `onClose` or a cancel button in the footer. Never trap the user in a modal.
- The submit button lives in the footer, connected to the form via the `form=` attribute — not nested inside the form element.
- Dialog title should name the action, not the component: "Edit address", not "Address form". See `content/microcopy.md` for modal title rules.
- For destructive actions (delete, remove), use `primaryDestructive` variant on the confirm button and name the object explicitly: "Delete this address".
