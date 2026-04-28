# RevLink

## When to use

Inline text link for navigation within body copy or alongside other text. Use when the interactive element is a word or phrase within a sentence.

Do not use `RevLink` as a standalone CTA — use `RevButton` for that. Do not use it for actions that do not navigate anywhere.

## Dependencies

None.

## Variants

None. RevLink has a single visual style.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `underlined` | `boolean` | `true` | Shows underline at rest. When `false`, underline appears on hover only. |
| `disabled` | `boolean` | `false` | Marks the link as non-interactive. Remains visible but cannot be activated. |
| `to` | `object` | — | Route object — delegates to navigation context |
| `href` | `string` | — | URL string — renders as a hyperlink |
| `replace` | `boolean` | `false` | Replaces the current history entry instead of pushing a new one |
| `children` | `node` | — | Link label |

## Structure

RevLink is an inline element. It renders within the surrounding text flow.

```
... sentence text  [Label]  sentence text ...
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Text | base | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Text | hover | `text.action.default.hi` (hover state) | — see `text.json` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Link label | `body-1-link` | 16px / weight 600 / line-height 24px / underlined |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Focus outline rounding | `radius.sm` | 6px |

## Accessibility

- Link text must describe the destination — avoid generic labels like "click here" or "read more".
- Focus ring: `focus.default-hi` — color `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
