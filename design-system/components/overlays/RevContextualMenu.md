# RevContextualMenu

## When to use

A dropdown menu anchored to a trigger element. Use for grouped actions or options that are secondary to the main page actions — "more options" menus, sort/filter controls, and action lists.

Use RevInputSelect when the user is choosing a value for a form field. Use RevTooltip for informational labels only (no actions). Keep menus short — if there are more than 7 items, consider a different pattern.

## Dependencies

- RevIcon (`guidelines/icons/`) — used for optional leading icons on menu items

## Variants

None.

## Props

### RevContextualMenu

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `open` | `boolean` | required | Controls visibility |
| `trigger` | `node` | required | The element that opens the menu (typically a RevButtonIcon) |
| `onClose` | `() → void` | — | Called when an item is selected or the menu is dismissed |
| `children` | `node` | required | RevContextualMenuItem components |

### RevContextualMenuItem

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | `string` | required | Item label |
| `icon` | `node` | — | Optional leading icon |
| `variant` | `'default' \| 'danger'` | `'default'` | Use `'danger'` for destructive actions |
| `disabled` | `boolean` | `false` | Disables the item |
| `onClick` | `event → void` | — | Called when the item is selected |

## Structure

```
          [Trigger button]
┌──────────────────────────┐
│  [Icon?]  [Item label]   │
│  [Icon?]  [Item label]   │
│  ────────────────────── │
│  [Icon?]  [Item label]   │  ← danger variant
└──────────────────────────┘
```

A divider can be added between item groups by inserting a separator element between RevContextualMenuItem components.

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Menu panel background | — | `background.float.default.low` | `hsl(0, 0%, 100%)` |
| Menu panel border | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Item background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Item background | hovered | `background.static.default.low` (hover) | `hsl(220, 19%, 94%)` |
| Item background | disabled | `background.static.default.low` (disabled) | `hsla(225, 21%, 7%, 0.05)` |
| Item label | default | `text.action.default.hi` | `hsl(225, 21%, 7%)` |
| Item label | danger | `text.action.danger.hi` | `hsl(351, 84%, 39%)` |
| Item label | disabled | `text.action.default.hi` (disabled state) | — see `text.json` |
| Item icon | default | `text.action.default.low` (via currentColor) | `hsl(223, 4%, 33%)` |
| Item icon | danger | `text.action.danger.hi` (via currentColor) | `hsl(351, 84%, 39%)` |
| Divider | — | `border.static.default.low` | `hsl(225, 15%, 89%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| Item label | `body-1` | 16px / weight 400 / line-height 24px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Item row | Vertical padding | `12` | 12px |
| Item row | Horizontal padding | `16` | 16px |
| Icon + label | Horizontal gap | `8` | 8px |
| Menu panel | Vertical padding | `4` | 4px |
| Menu panel border | Width and style | — | 1px solid |
| Divider | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Menu panel | `radius.md` | 8px |

### Elevation

| State | Token | Fallback |
|-------|-------|---------|
| Menu panel | `shadow.long` | `0px 8px 16px 0px rgba(0, 0, 0, 0.12)` |

## Accessibility

- The menu panel has `role="menu"`. Each item has `role="menuitem"` (or `role="menuitemradio"` / `role="menuitemcheckbox"` as appropriate).
- Arrow keys navigate between items; Enter or Space selects; Escape closes the menu and returns focus to the trigger.
- Disabled items have `aria-disabled="true"` and remain in the tab order for discoverability.
- Focus ring: `focus.default-hi` — `hsl(225, 100%, 60%)`, solid, 2px, offset 2px.
