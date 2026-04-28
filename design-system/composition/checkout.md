# Checkout — multi-step flow

## When to use

Linear form flow where the user completes a sequence of steps to place an order. Use whenever a transaction requires multiple distinct stages that must be completed in order.

Do not use for single-page forms or tasks that can be completed without a defined sequence.

## Components involved

| Component | File | Role |
|-----------|------|------|
| RevStepper | `components/data-display/RevStepper.md` | Step progress indicator |
| RevForm | `components/forms/RevForm.md` | Per-step form wrapper |
| RevCard | `components/cards/RevCard.md` | Order summary sidebar container |
| RevList | `components/data-display/RevList.md` | Line items in the order summary |
| RevInputText | `components/forms/RevInputText.md` | Address, promo code, and freeform fields |
| RevInputSelect | `components/forms/RevInputSelect.md` | Country, state, and list-based selectors |
| RevInputNumber | `components/forms/RevInputNumber.md` | Item quantity control |
| RevInputAutocomplete | `components/forms/RevInputAutocomplete.md` | Address lookup with suggestions |
| RevRadio | `components/selection/RevRadio.md` | Delivery option and payment method selection |
| RevCheckbox | `components/selection/RevCheckbox.md` | Billing address toggle and terms agreement |
| RevInfoBlock | `components/feedback/RevInfoBlock.md` | Contextual callouts (cut-off times, warranty) |
| RevButton | `components/actions/RevButton.md` | Step progression and final submit |
| RevDialog | `components/overlays/RevDialog.md` | High-risk confirmations (remove item, discard) |

## Structure

Mobile (stacked):

```
┌──────────────────────────────────────────────────┐
│  [RevStepper]                                    │
├──────────────────────────────────────────────────┤
│  [Per-step RevForm content]                      │
│                                                  │
│  [RevInfoBlock? — contextual callout]            │
│                                                  │
│  [RevButton — "Continue to [next step]"]         │
└──────────────────────────────────────────────────┘
```

Desktop (md+ — two column):

```
┌──────────────────────────────────────────────────────────────┐
│  [RevStepper]                                                │
├────────────────────────────────┬─────────────────────────────┤
│  [Per-step RevForm content]    │  [RevCard]                  │
│                                │    [RevList — line items]   │
│  [RevInfoBlock?]               │    [Price summary]          │
│                                │                             │
│  [RevButton — "Continue"]      │                             │
└────────────────────────────────┴─────────────────────────────┘
```

## Assembly

1. Render `RevStepper` at the top of the flow with all step names. Keep step labels short and task-oriented: "Cart", "Delivery", "Payment", "Review".
2. Each step renders a `RevForm` with the relevant inputs for that step. Gate progression behind form validation — do not advance with invalid fields.
3. On desktop (`md+`): show a persistent sidebar with `RevCard` containing a `RevList` of line items and a price summary. This sidebar persists across all steps.
4. Build each step with the following components:

| Step | Key components |
|------|----------------|
| Cart | `RevList` items, quantity `RevInputNumber`, promo `RevInputText` + `RevButton` |
| Address | `RevInputText`, `RevInputSelect`, `RevInputAutocomplete` for address lookup |
| Delivery | `RevRadio` list of delivery options, `RevInfoBlock` for order cut-off times |
| Payment | `RevRadio` or `RevList` for payment method, `RevCheckbox` for billing address toggle |
| Review | Read-only `RevList` summary, terms `RevCheckbox`, submit `RevButton` |

5. Place a primary `RevButton` at the bottom of each step to advance. Label it "Continue to [next step]" when the next step is not obvious from context; "Continue" when it is.
6. Use `RevDialog` for high-risk confirmations (removing an item, discarding unsaved changes). Do not use `RevToast` for these.

## Rules

- Never advance to the next step with invalid fields. `RevForm` handles error suppression until the first submit attempt.
- Persist partial data when the user navigates backward — never clear already-completed steps.
- The back action must restore the previous step's data exactly as the user left it.
- For unsaved-change warnings when leaving a step mid-edit: use `RevDialog` with title "Discard changes?", destructive confirm "Discard", and cancel "Keep editing". See `content/microcopy.md` for multi-step navigation copy rules.
