# Text tokens

Resolved token values: [`text.json`](text.json) — raw palette: [`raw.json`](raw.json)

Token naming: `text.[category].[function].[level]`.

State variants are resolved automatically per mood.

---

## static — non-interactive text

| Token | Description | Available states |
|-------|-------------|-----------------|
| `static.default.hi` | Primary text — titles, labels, high-importance copy | disabled |
| `static.default.mid` | Secondary text — body copy | disabled |
| `static.default.low` | Subtle text — captions, placeholder text | disabled |
| `static.warning.hi` | High-importance text — warning function | disabled |
| `static.danger.hi` | High-importance text — danger function | disabled |
| `static.success.hi` | High-importance text — success function | disabled |
| `static.info.hi` | High-importance text — info function | disabled |
| `static.brand.hi` | Brand text — blue tones | disabled |
| `static.brand.mid` | Brand text — purple tones | disabled |
| `static.brand.low` | Brand text — pink tones | disabled |
| `static.light.hi` | Always-light text — stays light regardless of mood or theme | disabled |

---

## action — interactive text

Use for text on or adjacent to interactive elements (links, button labels in ghost/outlined variants).

| Token | Description | Available states |
|-------|-------------|-----------------|
| `action.default.hi` | High-importance action text — links, interactive labels | hover, disabled, pressed, hoverpressed |
| `action.default.low` | Low-importance action text | hover, disabled, pressed, hoverpressed |
| `action.brand.hi` | Brand action text — blue tones | hover, disabled, pressed, hoverpressed |
| `action.brand.mid` | Brand action text — purple tones | hover, disabled, pressed, hoverpressed |
| `action.brand.low` | Brand action text — pink tones | hover, disabled, pressed, hoverpressed |
| `action.danger.hi` | Destructive action text | hover, disabled |
| `action.success.hi` | Success action text | hover, disabled |

---

## onaction — text placed on action backgrounds

Use only when text sits directly on an `action.*` background token. Match function and level to the background.

| Token | Paired background | Available states |
|-------|------------------|-----------------|
| `onaction.default.hi` | `action.default.hi` | disabled, pressed |
| `onaction.default.mid` | `action.default.mid` | disabled, pressed |
| `onaction.default.low` | `action.default.low` | disabled, pressed |
| `onaction.danger.hi` | `action.danger.hi` | disabled, pressed |
| `onaction.danger.mid` | `action.danger.*` mid-level | disabled, pressed |
| `onaction.success.hi` | `action.success.hi` | disabled, pressed |

---

## Rules

- Do not use `static.default.hi` on dark or brand-tinted backgrounds — contrast will fail.
- Always pair `onaction.*` tokens with their matching `action.*` background — never mix functions.
- `static.light.hi` is the only token that ignores mood. Use it only when text must remain light over any background (e.g. text on a photo).
