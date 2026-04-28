# Border tokens

Resolved token values: [`border.json`](border.json) — raw palette: [`raw.json`](raw.json)

Token naming: `border.[category].[function].[level]`.

State variants are resolved automatically per mood.

---

## static — non-interactive borders

| Token | Description | Available states |
|-------|-------------|-----------------|
| `static.default.hi` | Highlighted border — pressed states, progress bars | — |
| `static.default.mid` | Secondary border | — |
| `static.default.low` | Default border — dividers and containers | — |
| `static.default.dim` | Border with opacity — for layered surfaces | — |
| `static.danger.hi` | High-emphasis border — danger function | — |
| `static.danger.mid` | Secondary border — danger function | — |
| `static.success.hi` | High-emphasis border — success function | — |
| `static.success.mid` | Secondary border — success function | — |
| `static.brand.hi` | Brand border — blue tones | — |
| `static.brand.mid` | Brand border — purple tones | — |
| `static.brand.low` | Brand border — pink tones | — |
| `static.info.mid` | Secondary border — info function | — |
| `static.warning.mid` | Secondary border — warning function | — |

---

## action — interactive element borders

Use on outlined/ghost interactive elements. Match function and level to the paired background and text tokens — see `colors/overview.md`.

| Token | Description | Available states |
|-------|-------------|-----------------|
| `action.default.hi` | High-importance outlined action (e.g. outlined button) | disabled, focus, pressed |
| `action.default.low` | Low-importance outlined action | disabled, focus, pressed |
| `action.success.hi` | High-importance outlined success action | disabled |
| `action.danger.hi` | High-importance outlined destructive action | disabled, focus, pressed |
| `action.danger.low` | Low-importance outlined destructive action | disabled, focus, pressed |
| `action.brand.hi` | Outlined action — blue brand tones | disabled, focus, pressed |
| `action.brand.mid` | Outlined action — purple brand tones | disabled, focus, pressed |
| `action.brand.low` | Outlined action — pink brand tones | disabled, focus, pressed |

---

## overlap — borders on elevated surfaces

| Token | Description | Available states |
|-------|-------------|-----------------|
| `overlap.default.low` | Border for surfaces that sit over other surfaces | hover, disabled |

---

## Rules

- Static borders have no state variants — they are fixed values used on non-interactive surfaces.
- Action borders use `focus` instead of `hover` for state feedback — the border role in interactive elements is to communicate focus and press, not hover.
- Do not apply `action.*` borders to non-interactive elements.
