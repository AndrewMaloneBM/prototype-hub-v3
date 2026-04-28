# UI states

Copy and component guidance for system feedback states.

---

## Loading

- Use `RevSkeleton` for content placeholders — no copy needed. Mirror the shape and rhythm of the final layout exactly.
- Use `RevSpinner` only for indeterminate operations (e.g. a button in flight, a full-page gate). Always set a meaningful `alternativeText`.
- Do not place multiple spinners in proximity.
- When wait time is known, say so: "This may take up to 2 minutes."
- Avoid full-page spinners for long operations — use `RevSkeleton` to show content structure instead.

---

## Error states

Every error surface needs three things:

1. **What failed** — stated plainly.
2. **Why** — included if it helps the user act (omit internal causes).
3. **How to fix** — a clear recovery action.

Always pair a `RevToast` error with an in-context error state on the relevant input or section — never surface errors via toast alone.

Offer at least one recovery action (retry, alternative path, or support link). Do not leave users at a dead end.

See `microcopy.md` for error message copy rules.

---

## Success and confirmation states

- Use `useToast` `success` for transient confirmations after async operations.
- Pattern: "[Action] complete. [Next step or outcome]." — "Return booked. We'll email your label."
- Keep copy positive and brief — one sentence.
- Do not use success toasts for actions that require the user to make a further decision — use `RevDialog`.

---

## Validation states

- Suppress field errors until the first submit attempt (`RevForm` handles this automatically).
- Show inline errors directly below the failing field as soon as the user leaves it after a failed submit.
- For forms with multiple errors, surface a summary at the top of the form in addition to inline messages.
- Never use color alone to signal validity — always pair with an icon and text.

---

## Disabled states

- Prefer progressive disclosure over disabled buttons — reveal the action only when it becomes available.
- When a button must be disabled, explain why nearby: via helper text, a `RevTooltip`, or an inline message.
- Never disable a button silently.

---

## Skeleton vs. spinner guidance

| Situation | Component |
|-----------|-----------|
| Content structure is known (cards, lists, text blocks) | `RevSkeleton` |
| Indeterminate operation with no layout to mirror (button loading, full-page gate) | `RevSpinner` |
| After a user action that changes part of the page | Inline `RevSpinner` on the triggering element |

---

## Empty states

Four types, each requiring different handling:

| Type | Cause | Required elements |
|------|-------|-------------------|
| First-use | No data exists yet | What will appear here + primary action to create it |
| No results | Search or filter returned nothing | What was searched + how to adjust + primary action |
| Cleared | User removed all items | Confirmation of the empty state + path back |
| Error | Data failed to load | Acknowledgment of the failure + retry or recovery action |

**Component guidance:**

- Always include a primary action — do not leave the user at a dead end.
- For first-use and error states, use `RevInfoBlock` with the appropriate `variant` (`info` for first-use, `danger` for errors) to frame the message and action.
- For no-results states in a list or grid, render the message inline where the results would appear. Do not use a full-page overlay.
- For cleared states (e.g. empty cart), a short message with a `RevButton` or `RevLink` is sufficient — `RevInfoBlock` is not required.
- Pair an illustration or icon only when it adds meaning. Do not use them decoratively.
- Never show a skeleton or spinner for an empty state — the content has resolved; there is nothing left to load.

See `microcopy.md` for copy patterns (what to write for each empty state type).
