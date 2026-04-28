# Icons

Icon catalog (402 icons): [`icons.json`](icons.json) — standalone SVG files: [`svg/`](svg/)

Each icon is a 24×24 SVG using `fill="currentColor"`, making it colour-agnostic — it inherits whatever foreground colour the rendering context provides.

## Finding an icon

Use `icons.json` to look up any icon by name. The catalog maps each `PascalCase` icon name to its full SVG string. To use an icon, either:

- Embed the SVG string directly from `icons.json`
- Reference the corresponding file in `svg/IconName.svg`

Do not guess icon names. Search the catalog by keyword — icon names are descriptive PascalCase: `IconArrowRight`, `IconCheckSmall`, `IconHeartFilled`.

## Size scale

Icons are designed for the following sizes. Use the intended size for the context rather than scaling arbitrarily:

| Size | px | Use |
|------|----|-----|
| extra-small | 12 | Dense inline contexts |
| small | 16 | Compact UI, secondary actions |
| medium | 24 | Default — most UI contexts |
| large | 48 | Illustrative or hero usage |

Sizes 20px and 32px are also valid but have no named alias.

## Accessibility

- When an icon conveys meaning without surrounding text, provide an accessible label via your platform's equivalent (`aria-label`, `accessibilityLabel`, `contentDescription`, etc.).
- When an icon is purely decorative alongside visible text, hide it from assistive technology (`aria-hidden`, `importantForAccessibility="no"`, etc.).
- Icon colour is always `currentColor` — control it via the parent element's text colour token. Never hardcode a colour on the icon itself.

## Naming conventions

Icons follow the pattern `Icon` + descriptor + optional modifier:

- Direction: `IconArrowDown`, `IconArrowDownLeft`, `IconChevronRight`
- Filled vs outlined: `IconHeartFilled`, `IconHeartBroken`, `IconBellFilled`, `IconBellOutlined`
- Size qualifier: `IconCheckSmall`, `IconCheckLarge`, `IconCrossSmall`
- In-circle variant: `IconArrowDownInCircle`, `IconArrowDownInCircleFilled`

## Icon categories

| Prefix | Description | Examples |
|--------|-------------|---------|
| (none) | General UI icons | `IconSearch`, `IconEdit`, `IconTrash`, `IconHeart` |
| `IconArrow*` | Directional arrows | `IconArrowRight`, `IconArrowDownLeft` |
| `IconChevron*` | Chevron navigation | `IconChevronDown`, `IconChevronRight` |
| `IconLogo*` | Third-party logos | `IconLogoBackMarket`, `IconLogoFigma`, `IconLogoGitHub` |
| `IconReassurance*` | Trust and reassurance badges | `IconReassuranceShieldFilled`, `IconReassuranceTruckFilled` |
| `IconTabBar*` | Mobile tab bar icons (active/inactive pairs) | `IconTabBarHome`, `IconTabBarHomeActive` |
| `IconCurrency*` | Currency symbols | `IconCurrencyEuro`, `IconCurrencyDollar` |
| `IconEmoji*` | Sentiment icons | `IconEmojiHappy`, `IconEmojiNeutral` |
| `IconAccessibility*` | Accessibility-related icons | `IconAccessibilityBook`, `IconAccessibilityGuidelines` |
