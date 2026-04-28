# RevDocument

## When to use

Displays a single file attachment with its name, file type, size, and controls to download or remove it. Used in messaging threads, order details, and upload confirmation flows.

## Dependencies

- RevButtonIcon (`guidelines/components/actions/RevButtonIcon.md`) — used for the download and remove action buttons
- RevImage (`guidelines/components/media/RevImage.md`) — used for image file previews
- RevSpinner (`guidelines/components/feedback/RevSpinner.md`) — shown during upload or processing

## Variants

| Variant | Description |
|---------|-------------|
| `default` | File icon, name, size, and action buttons |
| `image` | Thumbnail image preview with name and actions |

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | `string` | required | File name including extension |
| `size` | `string` | — | Human-readable file size (e.g. `'2.4 MB'`) |
| `type` | `string` | — | MIME type or file extension label |
| `src` | `string` | — | URL of the file. Required for `image` variant and for the download action. |
| `variant` | `'default' \| 'image'` | `'default'` | Layout mode |
| `loading` | `boolean` | `false` | Shows a spinner, indicating upload or processing is in progress |
| `error` | `boolean` | `false` | Shows the file in an error state |
| `onDownload` | `() → void` | — | Called when the download button is clicked |
| `onRemove` | `() → void` | — | Called when the remove button is clicked. When omitted, the remove button is hidden. |

## Structure

Default variant:

```
┌──────────────────────────────────────────┐
│  [FileIcon]  [Name]        [↓]  [✕?]    │
│              [Size / Type]               │
└──────────────────────────────────────────┘
```

Image variant:

```
┌──────────────────────────────────────────┐
│  ┌───────────┐  [Name]       [↓]  [✕?]   │
│  │[Thumbnail]│  [Size / Type]            │
│  └───────────┘                           │
└──────────────────────────────────────────┘
```

## Tokens

### Color

| Part | State | Token | Fallback (default mood) |
|------|-------|-------|------------------------|
| Card background | default | `background.static.default.low` | `hsl(0, 0%, 100%)` |
| Card background | error | `background.static.danger.low` | `hsl(6, 100%, 96%)` |
| Card border | default | `border.static.default.low` | `hsl(225, 15%, 89%)` |
| Card border | error | `border.static.danger.hi` | `hsl(351, 84%, 39%)` |
| File name | default | `text.static.default.hi` | `hsl(225, 21%, 7%)` |
| File name | error | `text.static.danger.hi` | `hsl(351, 84%, 39%)` |
| File meta (size / type) | default | `text.static.default.low` | `hsl(223, 4%, 37%)` |
| File icon | — | `text.static.default.low` (via currentColor) | `hsl(223, 4%, 37%)` |

### Typography

| Part | Token | Fallback |
|------|-------|---------|
| File name | `body-2-bold` | 14px / weight 600 / line-height 20px |
| File size / type | `caption` | 12px / weight 400 / line-height 16px |

### Spacing

| Part | Property | Token | Value |
|------|----------|-------|-------|
| Card | Padding — all sides | `12` | 12px |
| File icon + content | Horizontal gap | `12` | 12px |
| Name + meta | Vertical gap | `2` | 2px |
| Actions | Horizontal gap between buttons | `4` | 4px |
| Card border | Width and style | — | 1px solid |

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Card | `radius.md` | 8px |
| Image thumbnail | `radius.sm` | 6px |

## Accessibility

- The download button must have an accessible label (e.g. "Download [filename]").
- The remove button must have an accessible label (e.g. "Remove [filename]").
- When `loading` is true, the file name must still be visible and the spinner indicated with `aria-label` (e.g. "Uploading [filename]").
