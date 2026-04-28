# Artwork tokens

Resolved token values: [`artwork.json`](artwork.json)

Use exclusively for illustrations and decorative elements — never for text, component backgrounds, borders, or interactive surfaces. All tokens are mood-aware and shift automatically with the active mood context.

---

## Illustration tokens

Each token has **base**, **hover**, and **disabled** states where applicable.

| Token | Description |
|-------|-------------|
| `artwork.primary` | Primary illustration fill |
| `artwork.primary-soft` | Soft/light variant of primary fill |
| `artwork.secondary` | Secondary illustration fill |
| `artwork.secondary-soft` | Soft/light variant of secondary fill |
| `artwork.danger` | Danger-function illustration element |
| `artwork.success` | Success-function illustration element |
| `artwork.warning` | Warning-function illustration element |
| `artwork.warning-soft` | Soft/light variant of warning fill |
| `artwork.info` | Info-function illustration element |
| `artwork.accent` | Accent highlight within illustrations |

Deprecated tokens — do not use:
- `artwork.primary-light` → use `artwork.primary-soft`
- `artwork.secondary-light` → use `artwork.secondary-soft`
- `artwork.warning-light` → use `artwork.warning-soft` if a replacement is provided

---

## File type tokens

Use to colour file-type indicators (icons, labels) within illustrations or document UI.

| Token | File type |
|-------|-----------|
| `artwork.file.audio` | Audio files |
| `artwork.file.document` | Word-processing documents |
| `artwork.file.general` | Generic/unknown file type |
| `artwork.file.image` | Image files |
| `artwork.file.pdf` | PDF files |
| `artwork.file.presentation` | Presentation files |
| `artwork.file.spreadsheet` | Spreadsheet files |
| `artwork.file.video` | Video files |

---

## Rules

- Do not use `artwork.*` tokens for UI text, backgrounds, or borders.
- Do not use deprecated `-light` tokens — use their `-soft` replacements.
- Artwork tokens resolve per mood — do not hardcode illustration colors outside this system.
