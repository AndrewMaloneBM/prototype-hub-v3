# Application context

Certain design system capabilities depend on services that the host application must provide. These services are not implemented by the design system itself — they are wired up once at the application root and made available to all components.

Components never configure these services themselves. They read from whatever the host application provides.

---

## Mood

The visual theme — light or dark — must be established at the application root or at a section boundary. All components inherit the active mood from their containing context.

**Default mood is light.** To render a section in the inverse (dark) context, apply it to the container that wraps that section.

Components within that container automatically use the `mood-inverse` token values from the relevant JSON files. Never override individual component colors to simulate a theme shift — change the mood context instead.

Two mood contexts are supported: **default** (light) and **mood-inverse** (dark).

---

## Navigation

Components that can navigate — buttons, cards, and links — accept two props for this purpose:

- **`to`** — a route descriptor object for internal navigation. The platform implementation maps this to whatever its router expects: a path string, a typed route object, a navigation intent, a deep link. The design system does not define the shape of `to`; that is determined by the host platform's navigation layer.
- **`href`** — a URL string for external navigation. Renders as a standard hyperlink. No navigation context is required.

Wire the navigation context up once at the application root. When a component has a `to` prop but no navigation context is available, it falls back to `href` if that is also provided. When neither navigation context nor `href` is present, the component renders as a non-interactive element.

---

## Image loading

Components that render remote images (`RevImage`) accept an image URL builder from the host application. This function takes three inputs — a base image path, a target display width in pixels, and optional optimisation hints (preferred format, quality level) — and returns a fully-qualified URL string pointing to the appropriate image variant on the host's CDN or image service.

Provide this once at the application root. Individual image components read from it; they do not construct URLs themselves.

**Fallback:** when no image URL builder is provided, `RevImage` uses the `src` prop value directly as the image URL with no transformation.

---

## Summary

| Context | Scope | Used by |
|---------|-------|---------|
| Mood | Root + section boundaries | All components |
| Navigation | Root | Any component with a `to` prop |
| Image loading | Root | `RevImage` and any component embedding images |
