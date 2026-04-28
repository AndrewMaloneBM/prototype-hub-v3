# Radius

Resolved token values: [`radius.json`](radius.json)

## Tokens

| Token | Value | Intended surface |
|-------|-------|-----------------|
| `radius.xs` | 2px | Badges, tiny UI elements requiring subtle rounding |
| `radius.sm` | 6px | Inputs, chips in dense layouts |
| `radius.md` | 8px | Default for buttons, inputs, and most component containers |
| `radius.lg` | 12px | Cards and small overlay surfaces |
| `radius.round` | 9999px | Pills, fully circular avatars and thumbnails |

## Rules

- Do not mix radius tokens across surface types. A button always uses the button radius token; a card always uses the card radius token.
- Do not use arbitrary values for border radius.
- Use `radius.round` for pill-shaped elements and circular avatars — not a percentage.
- Larger radius conveys hierarchy and elevation: modals and drawers use a larger radius than flat cards.
