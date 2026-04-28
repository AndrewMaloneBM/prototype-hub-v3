# Microcopy

Copy rules for specific UI patterns.

---

## Buttons and CTAs

- Start with a strong, specific verb: "Add to cart", "Place order", "Save changes", "Try again".
- Describe the outcome when the label alone is ambiguous: "Continue to payment" not "Continue".
- Keep labels ≤ 24 characters; ≤ 2–3 words where possible.
- One primary action per view.
- Destructive actions are explicitly labeled: "Delete order", "Remove card".
- No ending punctuation.
- Never use "Click here", "Submit", or "Proceed" as standalone labels.
- Do not use "Click" or "Tap" — write device-agnostically.

| Do | Don't |
|----|-------|
| "Start trade-in" | "Let's do this!" |
| "Retry payment" | "Try" |
| "Download invoice" | "Download" (when multiple assets exist) |

---

## Modal and dialog titles

- Imperative verb phrase or concise noun phrase — 3–7 words.
- Sentence case; no ending punctuation.
- State the action, not the component name: "Delete payment method" not "Confirmation dialog".
- For destructive actions, name the object: "Delete this address".

Body copy in modals: one or two short sentences — what happens and what comes next. For destructive actions, name the effect: "This will permanently delete your account and its data."

---

## Toasts

Toasts are transient. Keep to one sentence, ≤ 90 characters.

| Variant | Pattern | Example |
|---------|---------|---------|
| `success` | What completed | "Payment method added." |
| `info` | What changed or is happening | "Discount applied." |
| `error` | What failed + how to fix | "Couldn't save address. Try again." |

- Do not rely on toast as the only surface for errors — always pair with an in-context error state on the relevant input or section.
- Do not use toast for confirmations that require a decision — use `RevDialog`.

---

## Error messages

Structure: **what failed** → **why (if known and helpful)** → **how to fix**.

- Place field-level errors directly below the relevant input.
- Be specific about constraints: "Use at least 8 characters with a number" — not "Invalid password".
- Never blame the user; remove accusatory language.
- No exclamation points.
- Do not expose raw system error codes in UI text.

| Do | Don't |
|----|-------|
| "Card declined. Try another card or contact your bank." | "Payment failed!!!" |
| "Enter a valid email (example@domain.com)." | "Error code 12" |
| "Use at least 8 characters with a number." | "Incorrect password." |

---

## Empty states

Identify the state type and tailor accordingly.

| Type | Pattern | Example |
|------|---------|---------|
| First-use | What will appear here + next step | "No saved addresses yet. Add one to check out faster." |
| No results | What was searched + next step | "No matches for 'Galaxy S21'. Try different filters." |
| Cleared | What is empty + next step | "Your cart is empty." → \[Browse phones\] |
| Error | Acknowledge + recovery | "We can't load your orders right now." → \[Retry\] |

- Always include a clear primary action.
- Keep copy to 1–2 sentences.

---

## Navigation labels for multi-step flows

- Use short, task-oriented step names: "Cart → Delivery → Payment → Review".
- Keep labels identical across the stepper, breadcrumbs, and page headings.
- Forward CTA: "Continue to [next step]" when clarity is needed; "Continue" when context is clear.
- Back label: "Back to [previous step]" on web when space allows; "Back" is acceptable in compact layouts.
- If the flow auto-saves: state it — "Your progress is saved automatically."
- On leaving with unsaved changes, show a confirm dialog: title "Discard changes?", actions "Discard" (destructive) and "Keep editing".

---

## Form helper text and labels

- Labels are concise nouns or noun phrases: "Phone number", "Delivery address".
- Placeholders are examples only — never essential instructions: placeholder "+1 (555) 123-4567".
- Helper text goes below the field, one short sentence: "We'll only use this to contact you about your order."
- Mark optional fields as "Optional" — do not mark all required fields individually.
