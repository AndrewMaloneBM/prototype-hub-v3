# RevStepper

## When to use

For multi-step flows where the user must complete steps in sequence — checkout, onboarding, multi-page forms. Shows the user how many steps remain and which they have completed.

Do not use RevStepper for tab-style navigation where steps can be visited in any order — use RevTabs instead.

## Dependencies

- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the optional back navigation control

## Variants

| Variant | Description |
|---------|-------------|
| `horizontal` | Steps laid out in a row, suitable for top-of-page use |
| `vertical` | Steps stacked, suitable for sidebars |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `steps` | `object[]` | required | Ordered list of steps. Each has `label: string` and optionally `description: string`. |
| `activeStep` | `number` | required | Zero-indexed current step |
| `variant` | `'horizontal' \| 'vertical'` | `'horizontal'` | Layout direction |

## Structure

Horizontal variant:

```
┌──────────────────────────────────────────────────────┐
│  [●]─────────[●]─────────[○]─────────[○]            │
│  [Step 1]    [Step 2]    [Step 3]    [Step 4]        │
└──────────────────────────────────────────────────────┘
```

Filled circles are completed or active steps; empty circles are upcoming steps.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Step indicator | completed | `background.action.success.hi` | `hsl(156, 100%, 21%)` |
| Step indicator | active | `background.action.default.hi` | `hsl(225, 21%, 7%)` |
| Step indicator | upcoming | `background.static.default.hi` | `hsl(225, 15%, 89%)` |
| Step indicator border | active | `border.action.default.hi` | `hsl(223, 7%, 20%)` |
| Step indicator border | upcoming | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Connector line | completed | `border.action.success.hi` | `hsl(156, 100%, 21%)` |
| Connector line | upcoming | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Step number / check icon | completed | `text.static.light.hi` (via currentColor) | `hsl(0, 0%, 100%)` |
| Step number | active | `text.onaction.default.hi` | `hsl(0, 0%, 100%)` |
| Step number | upcoming | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Step label | active | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| Step label | completed | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Step label | upcoming | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| Step description | — | `text.static.default.low` | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Step label (active) | `body-2-bold` | 14px / weight 600 / line-height 20px |
| Step label (other) | `body-2` | 14px / weight 400 / line-height 20px |
| Step number | `caption-bold` | 12px / weight 600 / line-height 16px |
| Step description | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Step indicator | Size (width and height) | — | 24px |
| Step indicator + label | Vertical gap (horizontal layout) | `8` | 8px |
| Step indicator + label | Horizontal gap (vertical layout) | `12` | 12px |
| Steps | Horizontal gap (horizontal layout) | `16` | 16px |
| Steps | Vertical gap (vertical layout) | `16` | 16px |
| Step indicator border | Width and style | — | 1px solid |
| Connector line | Width and style | — | 1px solid |

## Accessibility

- The stepper is informational — it does not need interactive roles.
- Each completed step must be visually distinguishable from upcoming ones (not color alone).
- The active step must be announced to screen readers (e.g. `aria-current="step"`).
- Step labels must not be hidden — they are the primary accessible description of each step.
