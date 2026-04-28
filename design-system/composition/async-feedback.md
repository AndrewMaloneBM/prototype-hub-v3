# Async feedback

## When to use

After any async operation — form submit, API call, user-triggered action — to communicate success or failure without navigating away from the current view.

Do not use as the only surface for critical errors. Always pair a toast error with an in-context error state on the relevant input or section. Do not use for decisions requiring confirmation — use `RevDialog`.

## Components involved

| Component | File | Role |
|-----------|------|------|
| RevToast | `components/feedback/RevToast.md` | Delivers the feedback notification |

## Structure

`RevToast` renders in a fixed position at the top of the viewport, outside the normal component tree. It has no spatial relationship to other components on the page.

```
[Viewport top edge]
┌─────────────────────────────────────────────────┐
│  [Icon]  [Title]              [Close / Action?] │
│          [Description?]                         │
└─────────────────────────────────────────────────┘
```

## Assembly

1. Mount one `RevToast` instance at the application root, outside any scrollable container. It renders at the document root regardless of where in the component tree it is placed.
2. Trigger notifications from anywhere using the `useToast` hook methods:
   - `success(title, options?)` — for completed operations
   - `error(title, options?)` — for failed operations
   - `info(title, options?)` — for neutral status updates
3. Pass a `description` option for secondary detail when the title alone is not enough.

## Rules

- Mount `RevToast` exactly once at the app root. Multiple instances produce duplicate notifications.
- For errors: always surface an in-context error state on the relevant input or section in addition to the toast. Never rely on the toast alone.
- For confirmations requiring a decision: use `RevDialog`, not a toast.
- Keep toast titles to one sentence. Use `description` for secondary detail.
- Use `success` for completions, `error` for failures, `info` for neutral updates. See `content/states.md` for copy patterns.
