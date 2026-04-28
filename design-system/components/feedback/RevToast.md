# RevToast

## When to use

Transient notification that auto-dismisses after a short delay. Use for non-critical feedback after a user action — confirmations, errors, and informational messages that do not require a decision.

Do not use as the only surface for critical errors — always pair with an in-context error state on the relevant input or section. Do not use for decisions requiring confirmation — use `RevDialog`.

## Dependencies

- `RevButtonIcon` — `guidelines/components/actions/RevButtonIcon.md`

Must be implemented before building RevToast.

## Variants

Toasts have three variants, triggered via the `useToast` hook methods:

| Variant | Method | Use |
|---------|--------|-----|
| `success` | `useToast().success()` | Action completed successfully |
| `error` | `useToast().error()` | Action failed or an error occurred |
| `info` | `useToast().info()` | Neutral informational message |

## Usage

RevToast operates as a two-part system. Mount `RevToast` once at the application root, outside any scrollable container. Trigger toasts from anywhere using the `useToast` hook.

### Mounting

Place `RevToast` once at the root level of the application. Its output is rendered outside the normal component tree, directly at the document root — this ensures toasts appear above all other content regardless of where `RevToast` is mounted in the component hierarchy.

### useToast methods

| Method | Description |
|--------|-------------|
| `success(title, options?)` | Green toast with check icon. Returns an ID. |
| `error(title, options?)` | Red toast with alert icon. Returns an ID. |
| `info(title, options?)` | Dark toast with info icon. Returns an ID. |
| `dismiss(id)` | Dismisses a specific toast by ID |
| `dismissAll()` | Clears all active toasts |

### Toast options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `description` | `string` | — | Secondary text below the title |
| `duration` | `number` | `5000` | Auto-dismiss delay in milliseconds |
| `actionLabel` | `string` | — | Replaces the close button with an action link |
| `onAction` | `() → void` | — | Called when the action link is clicked. Also dismisses the toast. |
| `onClose` | `() → void` | — | Called when the close button is clicked |
| `icon` | `component` | — | Custom icon. Only applies to `info` — success and error use fixed icons. |

**Limits:** Maximum 4 toasts displayed simultaneously. New toasts prepend to the top; the oldest is removed when the limit is reached. Auto-dismiss pauses when the user hovers over or focuses a toast.

## Structure

```
┌────────────────────────────────────────────────────────┐
│  [Icon]  [Title]                  [Close / Action?]   │
│          [Description?]                               │
└────────────────────────────────────────────────────────┘
```

`[Close / Action?]` renders as a close button by default, or as an action link when `actionLabel` is provided.

## Tokens

### Color

| Variant | Part | Token | Fallback (default mood) |
|---------|------|-------|------------------------|
| `success` + `info` | Background | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| `success` + `info` | Text | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| `error` | Background | `background.action.danger.hi` | `hsl(351, 84%, 39%)` |
| `error` | Text | `text.onaction.danger.hi` | `hsl(0, 0%, 100%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Title | `body-2-bold` | 14px / weight 600 / line-height 20px |
| Description | `body-2` | 14px / weight 400 / line-height 20px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Container | Horizontal padding | `16` | 16px |
| Container | Vertical padding | `12` | 12px |
| Icon + content | Horizontal gap | `20` | 20px |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Toast container | `radius.lg` | 12px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Always | `elevation.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |

### Spacing (positioning)

| Property | Value |
|----------|-------|
| Min width (desktop `md+`) | 300px |
| Max width (desktop `md+`) | 400px |

## Accessibility

- `error` toasts use `role="alert"` and `aria-live="assertive"` — they are announced immediately and interrupt the screen reader.
- `success` and `info` toasts use `role="status"` and `aria-live="polite"` — they are announced at the next opportunity.
- Always set a descriptive `title`. Avoid generic messages like "Success" — prefer "Order confirmed" or "Payment failed".
- Do not rely on a toast as the sole indication of a critical error. Always surface errors in-context on the relevant form field or section as well.
