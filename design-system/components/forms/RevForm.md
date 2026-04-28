# RevForm

## When to use

Wraps a group of input components that submit together. Manages collective validation state and the submit/reset lifecycle.

Use RevForm whenever inputs share a submit action. For standalone inputs that update state immediately on change (no submit), RevForm is not needed.

## Dependencies

None.

## Variants

None.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `onSubmit` | `event → void` | — | Called on form submission. Receives the native submit event. |
| `onReset` | `event → void` | — | Called on form reset. |
| `children` | `node` | required | Form inputs, labels, and action buttons |

## Structure

```
┌──────────────────────────────────────┐
│  [children — inputs, labels, actions]│
└──────────────────────────────────────┘
```

## Tokens

RevForm has no visual tokens — it is a structural wrapper with no rendered surface.

## Accessibility

- The form element is announced as a landmark (`role="form"`) when it has an accessible name via `aria-label` or `aria-labelledby`. Provide one when multiple forms appear on the same page.
- Always include a submit button so keyboard and assistive technology users have a clear trigger.
- Validation errors must be associated with their input via `aria-describedby` — this is handled by each input component (e.g. RevInputText).
