# Breakpoints

Resolved token values: [`breakpoints.json`](breakpoints.json)

## Tokens

Breakpoint values in `breakpoints.json` are in pixels (integer, mobile-first). Token keys: `xs`, `sm`, `md`, `lg`.

| Token | Range | Columns | Gutter | Use |
|-------|-------|---------|--------|-----|
| `breakpoint.xs` | 0–374px | 1 | 0px | Very small / legacy phones |
| `breakpoint.sm` | 375–767px | 1 | 0px | Standard phones — default layout |
| `breakpoint.md` | 768–1199px | 4 | 72px | Tablets and small laptops |
| `breakpoint.lg` | 1200px+ | 12 | 32px | Desktop — full grid |

## Rules

- Design mobile-first: base styles apply from `xs`; use `md` and `lg` to progressively enhance.
- Do not introduce custom breakpoints outside this scale.
- Typography tokens for headings and punchline automatically scale at `md` — do not override this with custom media queries.

## Components with built-in responsive behaviour

These components adapt automatically across breakpoints — no manual responsive wiring needed:

- `RevContainer` — applies responsive horizontal padding and centres content with max-width
- `RevCardGrid` — switches column count based on breakpoint
- `RevCardCarousel` — adjusts visible slide count at `md` and `lg`

## Grid guidance

- At `sm` (phone): single-column layouts, full-width components, generous vertical spacing.
- At `md` (tablet): introduce 2- or 4-column compositions. Use `RevContainer` as the outer wrapper.
- At `lg` (desktop): use the full 12-column grid for complex layouts. Section padding increases.
