# Content overview

UI copy guidelines for Back Market product surfaces. Scoped to what affects generated UI strings — not email, push, or per-locale translation guides.

---

## Voice

Back Market's voice is **human, direct, and lightly irreverent** — a knowledgeable teammate, not a corporate system.

| Quality | Means |
|---------|-------|
| Human and helpful | Speak like a thoughtful colleague |
| Confident, not cocky | Clear about facts; never gloating |
| Optimistic and pragmatic | Celebrate better choices without guilt-tripping |
| Witty in small doses | Light clever touches; never snarky or at the user's expense |
| Trust-first | Transparent and precise — especially on price, condition, and sustainability |

---

## Tone by context

Keep the same voice; adjust tone to match the user's situation.

| Context | Tone | Example |
|---------|------|---------|
| Neutral flows (browsing, forms) | Clear, concise, unobtrusive | "Choose a storage size." |
| Positive moments (success, rewards) | Warm, brief — no hype | "Order placed. We'll email tracking soon." |
| Sensitive topics (payment, returns) | Reassuring, exact, plain | "Your refund will appear within 5–10 business days." |
| Errors and blockers | Direct, empathetic, solution-forward | "Card declined. Try another card or contact your bank." |

When in doubt: reduce wit, increase clarity.

---

## Core principles

- **Clarity over cleverness.** Say the simplest accurate thing.
- **Action-first.** Tell the user what to do next, not backstory.
- **Front-load meaning.** Most important words go first.
- **One idea per sentence.** Short, scannable lines.
- **Active voice.** "Update your address" — not "Your address can be updated."
- **Second person.** Use "you / your". Use "we / our" only when clarifying Back Market's responsibility. Never "I".
- **Present tense** for general statements; future tense only for promises or scheduled events.

---

## American English defaults

- Spelling: American (color, center, canceled).
- Reference: AP Stylebook for mechanics; Merriam-Webster for spelling.
- Oxford comma: use it.
- Dates: Month Day, Year — "April 17, 2026". No ordinals ("April 1", not "April 1st").
- Time: 12-hour with lowercase am/pm — "7:30 pm". Include time zone when relevant.
- Numbers: see `mechanics.md`.

---

## Files in this folder

| File | Contents |
|------|----------|
| `overview.md` | Voice, tone, core principles, and language defaults — start here |
| `mechanics.md` | Grammar and house style: capitalization, punctuation, numbers, standardized terms |
| `microcopy.md` | Copy rules for specific UI patterns: buttons, modals, toasts, errors, empty states, forms |
| `states.md` | Component and UX guidance for loading, error, success, validation, disabled, and empty states |

---

## Localization guardrails

- Write source strings in American English; keep them modular and unambiguous.
- Avoid idioms, puns, and culturally bound humor that won't translate.
- Leave room for text expansion — up to ~30% longer in other languages.
- Never hardcode currency, date, or unit formats — use locale-aware formatting in code.
