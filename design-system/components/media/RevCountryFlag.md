# RevCountryFlag

## When to use

Inline country flag image for locale indicators, shipping destinations, and phone country code selectors. Returns nothing for unrecognised country codes.

Always pair with a visible text country name or code — never rely on the flag image alone. Do not use flags to represent languages — use language names or codes instead.

## Dependencies

None.

## Flag image source

The component requires a source of flag images keyed by ISO 3166-1 alpha-2 country code. The recommended public source is **flagcdn.com** — free, no API key, Cloudflare-hosted, covers all 254 countries.

URL patterns:

```
PNG: https://flagcdn.com/w{width}/{code}.png
SVG: https://flagcdn.com/{code}.svg
```

Where `{code}` is the lowercase ISO 3166-1 alpha-2 country code (e.g. `fr`, `us`, `de`) and `{width}` is the desired pixel width (e.g. `24`, `40`, `80`).

Examples matching the RevCountryFlag size scale:

| Size | Recommended URL |
|------|----------------|
| `extra-small` (12px) | `https://flagcdn.com/w20/{code}.png` |
| `small` (18px) | `https://flagcdn.com/w20/{code}.png` |
| `medium` (24px) | `https://flagcdn.com/w40/{code}.png` |
| `large` (30px) | `https://flagcdn.com/w40/{code}.png` |
| `extra-large` (36px) | `https://flagcdn.com/w40/{code}.png` |

For vector output use `https://flagcdn.com/{code}.svg` — this scales to any size without quality loss.

## Variants

None. Size is controlled by the `size` prop.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `countryCode` | `string` | required | ISO 3166-1 alpha-2 country code (e.g. `'FR'`, `'US'`, `'DE'`). Returns nothing for unrecognised codes. |
| `size` | `'extra-small' \| 'small' \| 'medium' \| 'large' \| 'extra-large'` | `'medium'` | Flag width |
| `hasBorder` | `boolean` | `false` | Adds a subtle border around the flag |

### Size dimensions

| Size | Width | Height |
|------|-------|--------|
| `extra-small` | 12px | auto (3:2 ratio) |
| `small` | 18px | auto |
| `medium` | 24px | auto |
| `large` | 30px | auto |
| `extra-large` | 36px | auto |

Height is always `auto` to preserve the 3:2 flag aspect ratio.

## Structure

```
┌──────────────────────┐
│    [flag image]      │
└──────────────────────┘
```

The flag is a single image element sized by the `size` prop. Height is always `auto` (3:2 ratio). The optional border is a fixed overlay.

## Tokens

### Color

| Condition | Part | Token | Fallback (default mood) |
|-----------|------|-------|------------------------|
| `hasBorder: true` | Border | `border.static.default.dim` | `hsla(225, 21%, 7%, 0.4)` |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Border | Width and style | — | 1px solid |

### Radius

Corner radius scales proportionally with flag width when `hasBorder` is true. Values range from ~0.67px at `extra-small` to 2px (`radius.xs`) at `extra-large`.

## Accessibility

- The flag image is decorative by default. Always accompany it with a visible text country name or code.
- Do not use a flag as the sole indicator of a country — it is ambiguous for users unfamiliar with all flags.
- Never use flags to represent languages — a country may have multiple languages, and a language may be spoken in many countries.
