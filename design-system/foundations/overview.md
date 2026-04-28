# Foundations overview

All visual values in Revolve are defined as design tokens. Every token has a resolved value in the JSON files co-located with each guideline — load the relevant file to get exact values rather than hardcoding anything.

## How to read the token files

Each JSON file follows one of two shapes depending on whether the token is raw or semantic.

**Raw tokens** (`colors/raw.json`, `colors/functional.json`, `spacing.json`, `radius.json`, etc.) are flat key → value maps:

```json
"color.raw.grey.5": "hsl(225, 21%, 7%)",
"spacing.16": "16px",
"radius.md": "8px"
```

**Semantic color tokens** (`colors/background.json`, `colors/text.json`, `colors/border.json`) carry a `ref` pointing back to the raw palette entry, plus the resolved `value`. Each token has a `default` state and optionally a `mood-inverse` state:

```json
"color.background.action.default.hi": {
  "comment": "Primary filled action background",
  "default": {
    "base":     { "ref": "color.raw.grey.5",          "value": "hsl(225, 21%, 7%)" },
    "hover":    { "ref": "color.raw.grey.21",          "value": "hsl(231, 7%, 21%)" },
    "disabled": { "ref": "color.raw.alpha.black.5",    "value": "hsla(225, 21%, 7%, 0.05)" }
  },
  "mood-inverse": {
    "base":     { "ref": "color.raw.grey.100",         "value": "hsl(0, 0%, 100%)" },
    "hover":    { "ref": "color.raw.grey.94",          "value": "hsl(220, 19%, 94%)" },
    "disabled": { "ref": "color.raw.alpha.white.5",    "value": "hsla(223, 28%, 95%, 0.05)" }
  }
}
```

Follow the `ref` into `colors/raw.json` whenever you need to understand the full palette chain.

## Implement only what the page requires

Do not implement tokens speculatively or in bulk. The token files are reference material — look up a token only when the component or page you are building explicitly calls for it.

The correct workflow is:
1. Read the component or page specification to understand what visual properties are needed
2. Identify which token names those properties map to (from the component guideline or the relevant foundation doc)
3. Look up only those tokens in the JSON files to get their resolved values
4. Apply those values using your platform's primitives

A button that uses `background.action.default.hi` and `text.onaction.default.hi` should result in exactly two color token lookups — not an import of the entire background or text token file.

## Rules

- Never hardcode color values. Always reference a semantic token — never a raw token directly in a component or layout.
- Never hardcode spacing or size values outside the spacing scale.
- Always use the semantic color layer (`background.*`, `text.*`, `border.*`). The raw palette (`color.raw.*`, `color.functional.*`) exists only to back semantic tokens.
- Apply mood at the section or container level, never per-component. Two mood contexts are available: `default` and `mood-inverse`.
- Only implement tokens that are required by the current component or page. Do not pre-emptively define or register tokens that nothing uses.

## Token categories

| Category | Guidance | Resolved values |
|----------|----------|-----------------|
| Colors — background | `colors/background.md` | `colors/background.json` |
| Colors — text | `colors/text.md` | `colors/text.json` |
| Colors — border | `colors/border.md` | `colors/border.json` |
| Colors — functional palette | `colors/functional.md` | `colors/functional.json` |
| Colors — artwork | `colors/artwork.md` | `colors/artwork.json` |
| Colors — raw palette | `colors/overview.md` | `colors/raw.json` |
| Focus ring | `colors/functional.md` | `focus.json` |
| Typography | `typography.md` | `typography.json` |
| Font families | `typography.md` | `font-families.json` |
| Spacing | `spacing.md` | `spacing.json` |
| Radius | `radius.md` | `radius.json` |
| Shadows | `shadows.md` | `shadows.json` |
| Breakpoints | `breakpoints.md` | `breakpoints.json` |

## Decision tree

- Choosing a color → `colors/overview.md` first, then the relevant category file
- Setting text size, weight, or line height → `typography.md`
- Setting padding, gap, or any spatial value → `spacing.md`
- Rounding a surface → `radius.md`
- Adding depth or elevation → `shadows.md`
- Making a layout responsive → `breakpoints.md`
