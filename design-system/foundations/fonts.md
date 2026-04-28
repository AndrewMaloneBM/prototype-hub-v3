# Fonts

Font files are in [`foundations/fonts/`](fonts/). Font stack definitions per platform: [`font-families.json`](font-families.json)

## Included files

### BMDupletTXT — body copy

| File | Weight | Style |
|------|--------|-------|
| `BMDupletTXT-Regular.otf` | 400 | normal |
| `BMDupletTXT-Semibold.otf` | 600 | normal |
| `BMDupletTXT-Italic.otf` | 400 | italic |
| `BMDupletTXT-SemiboldItalic.otf` | 600 | italic |

Used by: all `body-*`, `label-*`, `caption-*` typography tokens.

### BMDupletDSP — secondary heading

| File | Weight | Style |
|------|--------|-------|
| `BMDupletDSP-Semibold.otf` | 600 | normal |

Used by: `heading-2`, `heading-3` typography tokens.

### IvarSoft — primary heading

| File | Weight | Style |
|------|--------|-------|
| `IvarSoft-SemiBold.ttf` | 600 | normal |
| `IvarSoft-SemiBoldItalic.ttf` | 600 | italic |

Used by: `heading-1`, `punchline`, `punchline-italic` typography tokens.

## Format notes

- `.otf` — OpenType, suitable for web and desktop
- `.ttf` — TrueType, suitable for web, iOS, and Android
- No `.woff2` files are included. For web deployment, convert OTF/TTF to WOFF2 before serving.
