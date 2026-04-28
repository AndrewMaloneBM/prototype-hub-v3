# Project

## Project guidelines

<!-- Add project-specific context here: what this project is, its goals, stack, and any constraints Claude should know about. -->

---

## Design system

This project is built on **Revolve**, Back Market's design system. All UI work must follow the Revolve guidelines.

Start with `Guidelines.md` at the repo root — it explains what Revolve is and how to navigate the documentation.

### Key paths

| Path | Contents |
|------|----------|
| `Guidelines.md` | Entry point — Revolve overview, critical rules, and navigation |
| `guidelines/brand/` | Logo files and usage rules |
| `guidelines/context.md` | Application-level contract: mood, navigation, image loading |
| `guidelines/foundations/` | Token system — colors, typography, spacing, radius, shadows, breakpoints |
| `guidelines/components/` | All `Rev*` components — when to use, props, variants, structure |
| `guidelines/composition/` | Multi-component patterns for common product surfaces |
| `guidelines/content/` | UI copy rules — voice, tone, microcopy, state messaging |
| `guidelines/icons/` | Icon catalog (`icons.json`) and SVG files (`svg/`) |

### Rules

- Never hardcode color, spacing, radius, or typography values. Always use a Revolve token.
- Use semantic color tokens (`background.*`, `text.*`, `border.*`) — never raw palette values.
- All components use the `Rev` prefix. Check `guidelines/components/overview.md` before building anything new.
- Mood is set at the container level and inherited. Never override colors per-component.
- Load only the guideline file relevant to the current task — do not load all files upfront.

## Coding standards

1. Avoid assumptions. When there is too much ambiguity, stop and ask before proceeding.
2. Keep it simple — never over-engineer, no unnecessary defensive programming.
3. Be concise. No emojis ever.
