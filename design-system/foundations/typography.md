# Typography

Resolved token values: [`typography.json`](typography.json) — font stacks by platform: [`font-families.json`](font-families.json)

40 type style tokens. All sizes in px; line heights in px. Heading and punchline tokens have a responsive size that applies at the `md` breakpoint (768px+).

## How to apply

The token name is the identifier. Look up the token in `typography.json` to get its `fontSize`, `fontWeight`, `lineHeight`, and `fontFamily` values, then apply them using whatever text-styling primitive your platform provides.

Never hardcode font sizes, weights, or line heights — always derive them from the token.

## Type scale

### Punchline

| Token | Size | Size (md+) | Weight | Line height | Use |
|-------|------|-----------|--------|-------------|-----|
| `punchline` | 42 | 56 | 600 | 48 / 64 | Marketing hero headline |
| `punchline-italic` | 42 | 56 | 600 | 48 / 64 | Italic hero headline |
| `punchline-sans` | 42 | 56 | 600 | 48 / 64 | Alternate family hero headline |
| `punchline-sans-tabular` | 42 | 56 | 600 | 48 / 64 | Numeric hero headline (tabular figures) |

### Headings

| Token | Size | Size (md+) | Weight | Line height | Use |
|-------|------|-----------|--------|-------------|-----|
| `heading-1` | 24 | 28 | 600 | 32 / 40 | Page or section title |
| `heading-1-italic` | 24 | 28 | 600 | 32 / 40 | Italic page title |
| `heading-1-sans` | 24 | 28 | 600 | 32 / 40 | Alternate family page title |
| `heading-1-tabular` | 24 | 28 | 600 | 32 / 40 | Numeric page title |
| `heading-2` | 20 | 22 | 600 | 28 / 32 | Section or subsection title |
| `heading-2-tabular` | 20 | 22 | 600 | 28 / 32 | Numeric section title |
| `heading-3` | 18 | 20 | 600 | 24 / 28 | Subsection or inline heading |

### Body

| Token | Size | Weight | Line height | Use |
|-------|------|--------|-------------|-----|
| `body-1` | 16 | 400 | 24 | Default paragraph copy |
| `body-1-bold` | 16 | 600 | 24 | Emphasis within body copy |
| `body-1-italic` | 16 | 400 | 24 | Italic body copy |
| `body-1-bold-italic` | 16 | 600 | 24 | Bold italic emphasis |
| `body-1-link` | 16 | 600 | 24 | Linked text in paragraphs (underlined) |
| `body-1-striked` | 16 | 400 | 24 | Struck-through text (e.g. original price) |
| `body-1-tabular` | 16 | 400 | 24 | Numeric body text (tabular figures) |
| `body-2` | 14 | 400 | 20 | Secondary body, dense UI text |
| `body-2-bold` | 14 | 600 | 20 | Emphasis within secondary body |
| `body-2-italic` | 14 | 400 | 20 | Italic secondary body |
| `body-2-bold-italic` | 14 | 600 | 20 | Bold italic secondary emphasis |
| `body-2-link` | 14 | 600 | 20 | Linked text in dense UI (underlined) |
| `body-2-striked` | 14 | 400 | 20 | Struck-through secondary text |
| `body-2-tabular` | 14 | 400 | 20 | Numeric secondary text (tabular figures) |

### Labels

| Token | Size | Weight | Line height | Use |
|-------|------|--------|-------------|-----|
| `label-large` | 16 | 400 | 20 | Prominent control labels |
| `label-large-bold` | 16 | 600 | 20 | Emphasized prominent label |
| `label-large-striked` | 16 | 600 | 20 | Struck-through prominent label |
| `label-medium` | 14 | 400 | 16 | Standard control labels |
| `label-medium-bold` | 14 | 600 | 16 | Emphasized standard label |
| `label-medium-striked` | 14 | 600 | 16 | Struck-through standard label |
| `label-small` | 12 | 400 | 14 | Compact labels, chips, badges |
| `label-small-bold` | 12 | 600 | 14 | Emphasized compact label |
| `label-small-striked` | 12 | 600 | 14 | Struck-through compact label |

### Caption

| Token | Size | Weight | Line height | Use |
|-------|------|--------|-------------|-----|
| `caption` | 12 | 400 | 16 | Metadata, helper text, footnotes |
| `caption-bold` | 12 | 600 | 16 | Emphasized metadata |
| `caption-italic` | 12 | 400 | 16 | Italic metadata |
| `caption-bold-italic` | 12 | 600 | 16 | Bold italic metadata |
| `caption-link` | 12 | 600 | 16 | Linked microcopy (underlined) |
| `caption-striked` | 12 | 400 | 16 | Struck-through metadata |

## Rules

- Never hardcode font sizes, weights, or line heights. Always use a named token.
- Do not use `caption` or `label-small` as body copy — they are for metadata, helper text, and compact component labels only.
- Use `tabular` variants wherever numbers must align (prices, counters, tables).
- Heading and punchline tokens are responsive: the larger size applies at `md` (768px+). Do not override this.
- Letter-spacing is 0 across all tokens. Do not add custom letter-spacing.
