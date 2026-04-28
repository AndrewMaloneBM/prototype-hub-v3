# RevAvatar

## When to use

Circular visual identifier for a person or entity. Use in message threads, user profiles, seller cards, and any context where a named entity needs a visual representation.

Use consistently sized avatars within a list or thread.

## Dependencies

- `RevImage` — `guidelines/components/media/RevImage.md`

Must be implemented before building RevAvatar.

## Variants

None. Size is controlled by the `size` prop.

## Recolouring

RevAvatar does not expose a colour prop. Two mechanisms are available:

**Mood context** — wrapping the avatar in a container with `mood-inverse` applied shifts `background.static.default.mid` and `text.static.default.hi` to their inverse values automatically. This is the recommended approach when the avatar appears on a dark surface.

**`children` prop** — passing fully custom content via `children` gives complete control over what renders inside the circle. The circular container and its dimensions are always preserved; only the interior is replaced. Use this for custom coloured initials, branded icons, or any content that needs a specific colour not achievable through the mood system.

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `size` | `'small' \| 'medium' \| 'large'` | required | Avatar dimensions — see size table |
| `label` | `string` | required | Accessible name. Also the source for the initial letter fallback. |
| `thumbnail` | `string` | — | Image URL. Takes precedence over `icon` and initial. |
| `icon` | `component` | — | Icon. Takes precedence over initial. |
| `children` | `node` | — | Custom content. Takes highest precedence over all other display options. |

**Content priority (highest to lowest):** `children` → `thumbnail` → `icon` → first letter of `label`

## Structure

```
┌──────────────────┐
│                  │
│  [Children       │
│   / Thumbnail    │
│   / Icon         │
│   / Initial]     │
│                  │
└──────────────────┘
```

The circular container is always present. Only one content layer renders at a time, resolved by the priority order above.

### Size dimensions

| Size | Diameter |
|------|---------|
| `small` | 20px |
| `medium` | 40px |
| `large` | 80px |

## Tokens

### Color

| Part | Token | Fallback (default mood) |
|------|-------|------------------------|
| Background (initial fallback) | `background.static.default.mid` | `hsl(220, 19%, 94%)` |
| Initial letter | `text.static.default.hi` | `hsl(225, 21%, 7%)` |

### Typography

| Size | Part | Token | Fallback |
|------|------|-------|---------|
| `small` | Initial letter | `body-2-bold` | 14px / weight 600 |
| `medium` | Initial letter | — | 20px / weight 600 (body-1-bold weight, custom size) |
| `large` | Initial letter | — | 44px / weight 600 (body-1-bold weight, custom size) |

Medium and large use body-1-bold font weight and family but with custom sizes proportional to the avatar diameter.

### Radius

| Surface | Token | Fallback |
|---------|-------|---------|
| Avatar container | `radius.round` | 9999px |
| Thumbnail image | `radius.round` | 9999px |

### Spacing

| Size | Icon size |
|------|-----------|
| `small` | 16px |
| `medium` | 24px |
| `large` | 48px |

## Accessibility

- `label` is exposed as `aria-label` on the container — always provide a meaningful name (e.g. the person's name, not "avatar").
- When `thumbnail` is provided, the image uses `label` as its alt text.
- Do not rely on avatar colour to convey identity — always pair with a visible name.
