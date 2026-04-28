# RevTabs

Covers RevTabItem, which is the individual tab within a tab bar. RevTabItem is not exposed independently.

## When to use

For switching between content sections within the same page or view. Each tab reveals a different panel without navigating away.

Do not use tabs for multi-step forms or wizards — use RevStepper instead. Do not use more than 5 tabs in a single bar; if more are needed, consider a different navigation pattern.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for optional leading icons on tabs

## Variants

| Variant | Description |
|---------|-------------|
| `default` | Full-width tab bar, tabs share available space equally |
| `scrollable` | Tabs overflow horizontally and can be scrolled |

## Props

### RevTabs

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `value` | `string` | required | The `value` of the currently active tab |
| `variant` | `'default' \| 'scrollable'` | `'default'` | Layout mode |
| `onChange` | `(value: string) → void` | — | Called when the active tab changes |
| `children` | `node` | required | RevTabItem components |

### RevTabItem

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `value` | `string` | required | Unique identifier for this tab |
| `label` | `string` | required | Visible tab label |
| `icon` | `node` | — | Optional leading icon |
| `disabled` | `boolean` | `false` | Disables the tab |
| `children` | `node` | — | Panel content shown when this tab is active |

## Structure

```
┌───────────────────────────────────────────────────────┐
│  [TabItem]  [TabItem]  [TabItem]  [TabItem]           │
│  ──────────────────────────────────────────────────── │
│  [Active panel content]                               │
└───────────────────────────────────────────────────────┘
```

The active tab has an underline indicator. The panel content sits below the tab bar.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Tab bar background | — | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Tab bar bottom border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Tab label | inactive | `text.action.default.low` | `hsl(223, 4%, 33%)` |
| Tab label | active | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Tab label | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Tab label | hovered | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Active indicator (underline) | — | `border.action.default.hi` | `hsl(223, 7%, 20%)` |
| Tab icon | inactive | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |
| Tab icon | active | `text.action.default.hi` (via currentColor) | `hsl(225, 21%, 7%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Tab label (inactive) | `body-1` | 16px / weight 400 / line-height 24px |
| Tab label (active) | `body-1-bold` | 16px / weight 600 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Tab item | Vertical padding | `16` | 16px |
| Tab item | Horizontal padding | `16` | 16px |
| Tab item | Horizontal gap between icon and label | `8` | 8px |
| Active indicator | Bottom offset from tab bar baseline | — | 0px (flush with bottom border) |
| Active indicator | Thickness | — | 2px |
| Tab bar bottom border | Width and style | — | 1px solid |
| Active indicator (underline) | Width and style | — | 2px solid |

## Accessibility

- The tab list must use `role="tablist"`.
- Each RevTabItem must use `role="tab"` and `aria-selected` to reflect active state.
- Each panel must use `role="tabpanel"` and `aria-labelledby` pointing to its tab.
- Arrow keys (left/right) navigate between tabs; Home and End move to the first and last tab.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
