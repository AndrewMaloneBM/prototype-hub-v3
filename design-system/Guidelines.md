# Revolve Design System Guidelines

Revolve is Back Market's design system. It provides the foundations, components, and content standards used to build consistent, accessible, and brand-aligned interfaces across Back Market's products.

These guidelines are platform-agnostic. Token values, component behaviour, and content rules apply regardless of framework or target platform. All resolved token values are provided as JSON files co-located with their documentation.

## Critical rules

- Never hardcode color values. Always use the semantic color token layer — never raw palette values directly.
- Never hardcode spacing, size, or radius values. Always use a token from the scale.
- Never hardcode font sizes, weights, or line heights. Always derive them from a typography token.
- All components use the `Rev` prefix: `RevButton`, `RevCard`, `RevInputText`.
- Mood and theme are set at the container level and inherited by all components within. Never override colors per-component. See `guidelines/context.md`.
- Application-level context (mood, navigation, image loading) must be wired up once at the root before any component is used. See `guidelines/context.md`.

## How to use these guidelines

Load only the file relevant to your current task — do not load all files upfront.

- Setting up application context → `guidelines/context.md`
- Picking a color, spacing, typography, or other token → `guidelines/foundations/overview.md`, then the relevant file
- Using an icon → `guidelines/icons/icons.md`
- Building a component → `guidelines/components/overview.md`, then the relevant component file
- Assembling a multi-component layout → `guidelines/composition/overview.md`
- Writing or reviewing UI copy → `guidelines/content/overview.md`

## What is in each folder

| Path | Contents |
|------|----------|
| `guidelines/brand/` | Logo versions, clearspace, minimum sizes, colour rules, and prohibited uses |
| `guidelines/context.md` | Application-level contract: mood, navigation, image loading |
| `guidelines/foundations/` | Token system — colors, typography, spacing, radius, shadows, breakpoints. Each topic has a `.md` guidance file and a co-located `.json` with resolved values |
| `guidelines/icons/` | Icon catalog (`icons.json`), standalone SVG files (`svg/`), and usage guidance |
| `guidelines/components/` | All `Rev*` components — when to use, props, variants, decision trees |
| `guidelines/composition/` | Patterns combining multiple components |
| `guidelines/content/` | UI copy rules: tone of voice, microcopy, state messaging, grammar |

## Brand philosophy

Back Market's UI is human, clear, and trustworthy. Interfaces should be bold without getting in the way of tasks. Accessibility and inclusivity are non-negotiable — all patterns target WCAG AA compliance. Tone is consistent across touchpoints; visual emphasis adapts to context.
