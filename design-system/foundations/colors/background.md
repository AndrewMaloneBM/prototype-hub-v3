# Background tokens

Resolved token values: [`background.json`](background.json) — raw palette: [`raw.json`](raw.json)

Token naming: `background.[category].[function].[level]`.

State variants are resolved automatically per mood.

---

## static — non-interactive container fills

| Token | Description | Available states |
|-------|-------------|-----------------|
| `static.default.hi` | Strongly highlighted container | hover, disabled |
| `static.default.mid` | Mildly highlighted container | hover, disabled |
| `static.default.low` | Default container background | hover, disabled |
| `static.default.min` | Transparent container background | hover, disabled |
| `static.warning.hi` | Strongly highlighted container — warning | hover, disabled |
| `static.warning.mid` | Mildly highlighted container — warning | hover, disabled |
| `static.warning.low` | Subtle container — warning | hover, disabled |
| `static.danger.hi` | Strongly highlighted container — danger | hover, disabled |
| `static.danger.mid` | Mildly highlighted container — danger | hover, disabled |
| `static.danger.low` | Subtle container — danger | hover, disabled |
| `static.success.hi` | Strongly highlighted container — success | hover, disabled |
| `static.success.mid` | Mildly highlighted container — success | hover, disabled |
| `static.success.low` | Subtle container — success | hover, disabled |
| `static.info.max` | Strongly highlighted small container — info | hover, disabled |
| `static.info.hi` | Highlighted container — info | hover, disabled |
| `static.info.mid` | Mildly highlighted container — info | hover, disabled |
| `static.info.low` | Subtle container — info | hover, disabled |
| `static.brand.hi` | Brand-hi tinted container | — |
| `static.brand.mid` | Brand-mid tinted container | — |
| `static.brand.low` | Brand-low tinted container | — |
| `static.backup.low` | BackUp feature background | disabled |

---

## action — interactive element fills

Use only on elements with click/tap affordance. Match level and function across all states — do not mix.

| Token | Description | Available states |
|-------|-------------|-----------------|
| `action.default.hi` | Primary filled action (e.g. primary button) | hover, disabled, pressed, hoverpressed |
| `action.default.mid` | Secondary filled action | hover, disabled, pressed, hoverpressed |
| `action.default.low` | Subtle action fill | hover, disabled, pressed, hoverpressed |
| `action.default.min` | Transparent/ghost action | hover, disabled |
| `action.default.brand.hi` | Brand-tinted picker — cornflower | — |
| `action.default.brand.mid` | Brand-tinted picker — purple | — |
| `action.default.brand.low` | Brand-tinted picker — blush | — |
| `action.danger.hi` | Primary filled destructive action | hover, disabled, pressed, hoverpressed |
| `action.danger.min` | Ghost destructive action | hover, disabled |
| `action.success.hi` | Primary filled success action | hover, disabled, pressed, hoverpressed |
| `action.success.min` | Ghost success action | hover, disabled |

---

## surface — page and section backgrounds

Use as the base layer for pages, panels, and sections. No interactive affordance.

| Token | Description | Available states |
|-------|-------------|-----------------|
| `surface.default.hi` | Contrasting page/section background | — |
| `surface.default.mid` | Slightly contrasting page/section background | — |
| `surface.default.low` | Default page/section background | — |
| `surface.brand.hi` | Blue brand-tinted section | — |
| `surface.brand.mid` | Purple brand-tinted section | — |
| `surface.brand.low` | Pink brand-tinted section | — |
| `surface.brand.min` | Extra content hierarchy surface | — |

---

## float, overlap, raised — elevated surfaces

These tokens are required when a surface is neutral — shadow alone cannot establish visual separation on a surface that shares the same colour as its surroundings. On tinted or coloured surfaces, shadow can be used without these tokens. See `foundations/shadows.md` for the full pairing rules.

| Token | Description | Paired shadow | Available states |
|-------|-------------|--------------|-----------------|
| `float.default.low` | Elevation 1 — cards resting on surface | `elevation.short` | hover, disabled |
| `float.default.mid` | Elevation 1 — contrasting card | `elevation.short` | hover, disabled |
| `float.default.hi` | Elevation 1 — high-contrast card | `elevation.short` | hover |
| `overlap.default.low` | Elevation 2 — popovers, menus | `elevation.middle` | hover, disabled |
| `raised.default.low` | Elevation 3 — tooltips, drawers | `elevation.long` | hover, disabled |

---

## overlay — scrim backgrounds

| Token | Description | Available states |
|-------|-------------|-----------------|
| `overlay.hi` | Strong scrim — non-comparative overlays (e.g. dialog backdrop) | — |
| `overlay.low` | Light scrim — comparative overlays (e.g. drawer backdrop) | — |
