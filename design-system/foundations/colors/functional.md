# Functional tokens

Resolved token values: [`functional.json`](functional.json) — focus ring token: [`../focus.json`](../focus.json)

Functional tokens are **raw palette scales**, not semantic tokens. They provide the color values that `background.*`, `text.*`, and `border.*` semantic tokens reference internally.

Do not use `functional.*` tokens directly in components or layouts. Use the semantic tokens in `background.md`, `text.md`, and `border.md` instead.

---

## When to use functional tokens directly

Only in cases where semantic tokens are insufficient — primarily data visualisation, charts, or custom illustration elements that need a specific shade from the scale. In those cases, use only `visibility: primary` shades.

---

## Available scales

Each scale runs from darkest (5) to lightest (99), with `visibility: primary` shades for direct use and `visibility: secondary` shades reserved as hover transitions between primaries.

| Scale | Function | CSS prefix |
|-------|----------|------------|
| `functional.danger` | Errors, destructive states | `--color-functional-danger-*` |
| `functional.success` | Confirmations, positive states | `--color-functional-success-*` |
| `functional.warning` | Cautionary, non-critical states | `--color-functional-warning-*` |
| `functional.info` | Neutral informational states | `--color-functional-info-*` |
| `functional.focus` | Focus ring colour (single value: `50`) | `--color-functional-focus-50` |

---

## Focus token

The focus ring uses a single token: `functional.focus.50` — a blue at `hsl(225, 100%, 60%)`.

This is applied automatically by interactive components. Do not override or suppress focus ring colour.

---

## Primary shade reference (danger — use as a guide for all scales)

| Shade | Lightness | Typical use |
|-------|-----------|-------------|
| 5–25 | Very dark | Text on light backgrounds, icon fills |
| 30–50 | Mid | Filled feedback backgrounds |
| 55–70 | Light-mid | Text on dark backgrounds |
| 75–90 | Light | Tinted backgrounds, borders |
| 95–99 | Very light | Subtle tinted surface backgrounds |

The same lightness pattern applies to `success`, `warning`, and `info` scales.
