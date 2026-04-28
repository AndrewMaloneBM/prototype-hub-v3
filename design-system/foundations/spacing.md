# Spacing

Resolved token values: [`spacing.json`](spacing.json)

4px-based scale. Values in px. Token keys in `spacing.json` are the numeric step value — `"16"` maps to `"16px"`.

## Scale

| Token | Value | Use |
|-------|-------|-----|
| `0` | 0px | No spacing |
| `2` | 2px | Micro gaps — icon-to-label, tight inline elements |
| `4` | 4px | Dense component internals |
| `8` | 8px | Default intra-component gap (e.g. between icon and label) |
| `12` | 12px | Component internal padding, field gaps |
| `16` | 16px | Default component padding, list item vertical rhythm |
| `20` | 20px | Block spacing inside cards and sections |
| `24` | 24px | Section content padding |
| `32` | 32px | Section padding, container gutters on small screens |
| `40` | 40px | Larger section padding |
| `48` | 48px | Page-level spacing, hero content separation |
| `56` | 56px | Large section separation |
| `64` | 64px | Large section separation on desktop |
| `80` | 80px | Large section breaks on desktop |
| `96` | 96px | Landing page hero spacing |

## Rules

- Always use a token from the scale. Never hardcode spacing values outside of it.
- Keep increments within the 4px base. Do not introduce values outside the scale.
- Use spacing tokens for gaps between sibling elements and for padding inside containers, not for positioning or offset.

## Guidance by context

| Context | Typical tokens |
|---------|---------------|
| Icon-to-label gap | `8` |
| Button internal padding | `12`–`16` |
| Card internal padding | `16`–`24` |
| Gap between stacked components | `16`–`24` |
| Section vertical padding | `32`–`48` |
| Page section breaks | `48`–`96` |
