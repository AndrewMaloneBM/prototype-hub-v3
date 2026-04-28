# Prototype Hub v2

This file is the source of truth for this workspace. Claude reads it at the start of every session.

---

## First-time setup

**Check `index.html` at the start of every session.** If the `HUB` config object still contains `__TEAM_NAME__`, this is a fresh clone. Do not wait for the user to ask — greet them and start setup right away.

Say something like: "Looks like this is a fresh setup — I'll get your hub live in a few minutes. What's your name?" Then:

1. Ask for their name and team name — nothing else, keep it short
2. In `index.html`, replace `__TEAM_NAME__`, `__DESIGNER_NAME__`, `__TEAM_SLUG__` (slug = team name lowercased, spaces → hyphens) in the `HUB` config object
3. Check if `gh` is authenticated: run `gh auth status`. If it returns an error, run `gh auth login` and tell the user: "GitHub needs to verify your account — a one-time code and URL will appear below. Open the URL, enter the code, and come back here." Wait for auth to complete before continuing.
4. Enable GitHub Pages to serve from the branch root (no build step needed):
   ```bash
   gh api repos/{owner}/{repo}/pages --method POST --field build_type=legacy --field "source[branch]=main" --field "source[path]=/"
   ```
   If that fails because Pages already exists, run the same call with `--method PUT` instead.
5. Commit and push:
   ```bash
   git add -A && git commit -m "Initial setup" && git push
   ```
6. Fetch the live URL: `gh api repos/{owner}/{repo}/pages` — read the `html_url` field. Tell the user: "Your hub is live at `<html_url>` — it may take 30 seconds to appear the first time."

The user should not need to touch the terminal at any point.

---

## Who & Why

A code-based prototyping workspace for product designers. No Node.js, no build tools, no npm. Just HTML files powered by Vue 3 and Tailwind (both loaded from CDN). Designers build and share interactive Back Market back-office prototypes via a GitHub Pages URL that's always live.

**Stack:**
- Vue 3 (CDN) — reactivity for the sidebar and prototype content
- Tailwind CSS (CDN) — styling with BM Revolve tokens defined inline
- GitHub Pages (legacy mode) — serves HTML files directly from `main`, no build step

---

## Creating a new prototype

When a user asks to create a new prototype or shares a PRD:

1. Copy `prototypes/_template.html` to `prototypes/[prototype-name].html`
2. In the new file, update the config block at the top:
   - `TITLE` — the prototype name shown in the sidebar
   - `SELLER_NAME` — seller name for the BM shell
   - `PAGE_TITLE` and `TABS` — match the page being prototyped
   - `NAV_ITEMS` — back-office nav tabs relevant to the feature
   - `conceptMeta` — add one entry per concept, fill in name, prdFeature, prdMetric, pros, cons, pages
3. Build the concept screens inside the `v-show="activeConcept === N"` divs using BM Revolve token classes
4. Register it in `index.html` — add an entry to the `inProgress` array:
   ```js
   {
     title: 'Prototype title',
     description: 'One sentence description.',
     problemStatement: 'Optional — the core problem being solved.',
     author: 'Designer name',
     date: 'Apr 2026',
     scope: 'Seller back-office',
     goal: 'Optional goal',
     impact: 'Optional impact',
     concepts: 2,
     link: 'prototypes/prototype-name.html',
     accent: '#18a271',
   }
   ```
5. Deploy (see below)

---

## Deploying

When the user asks to deploy, share, or push:

```bash
git add -A && git commit -m "Update prototypes" && git push
```

GitHub Pages serves the files immediately — no build step, no wait. The live URL is always `https://[username].github.io/[repo-name]/`.

---

## Design tokens (BM Revolve)

Full Revolve guidelines are in `design-system/` at the repo root. Entry point: `design-system/Guidelines.md`. Load only the file relevant to the current task.

Tailwind token classes available in every prototype file:

**Colours:** `bm-surface`, `bm-text-hi/mid/low/muted`, `bm-border`, `bm-border-action`, `bm-green-{50–900}`, `bm-gray-{50–900}`, `bm-danger`, `bm-warning`, `bm-success`, `bm-info`

**Typography — real Revolve fonts (wired up in `_template.html`, files in `fonts/`):**
- `font-heading-primary` — IvarSoft (serif) — h1-level headings (`text-2xl`+)
- `font-heading-secondary` — BMDupletDSP (display sans) — h2/h3-level headings (`text-xl` and below)
- `font-body` — BMDupletTXT (body sans) — all UI text, labels, captions (default)

Never use `font-display` — it no longer exists. Never use Google Fonts for prototypes.

**Icons — Revolve library (402 SVGs in `icons/`, path from prototypes: `../icons/IconName.svg`):**
- Use `<img src="../icons/IconName.svg" class="w-4 h-4" aria-hidden="true" />` for icons that don't need color inheritance
- Keep inline SVG for icons that need `text-*` color classes (img tags can't inherit color)

**Border radius:** `rounded-bm-xs` (2px), `rounded-bm-sm` (6px), `rounded-bm` (8px), `rounded-bm-lg` (12px), `rounded-bm-xl` (16px)

Rules:
- Never hardcode color, spacing, radius, or typography — always use a Revolve token class
- Use semantic tokens (`bm-text-*`, `bm-border`, `bm-surface`) — never raw palette values

---

## Sidebar features

The sidebar is fully wired in every prototype file. Features:
- **Concept switcher** — numbered pills, one per entry in `conceptMeta`
- **Before / After toggle** — `previewMode` ref, use it to conditionally show old vs new UI
- **Pages tree** — auto-generated from each concept's `pages[]`; shows "What's New" changes inline
- **Sub-states** — add `subStates: [{ id, label }]` to any page for deep-linkable UI states (e.g. modal open, panel expanded)
- **Reset button** — calls `resetDismissedUi()`, wire it to re-show any dismissed banners or panels
- **Hotspot flash** — clicking anywhere in the prototype area flashes elements with class `prototype-hotspot`

---

## Adding sub-states to a page

```js
{
  id: 'money',
  label: 'Money',
  navItem: 'Money',
  changes: ['New payout timeline widget'],
  subStates: [
    { id: 'money-default', label: 'Default view' },
    { id: 'money-panel-open', label: 'Breakdown panel open' },
  ],
}
```

Then in `navigateToSubState()` already in the file, the `activeSubStateId` ref updates automatically. Use it in the concept content:

```html
<div v-if="activeSubStateId === 'money-panel-open'" class="...">
  Panel content
</div>
```

---

## Key conventions

- `v-show` (not `v-if`) for concept switching — keeps all concepts mounted so state persists
- Modals go as siblings of the scroll div — never inside the scrollable area. Use `absolute inset-0` positioning.
- `prototype-hotspot` class on any clickable element makes it flash when the user clicks to reveal interactions
- Always use Revolve token classes, never hardcode colours
