# Components overview

## Naming

All components use the `Rev` prefix: `RevButton`, `RevCard`, `RevInputText`, etc.

## Variant prop

Most components expose a `variant` prop that controls visual style. Valid values are listed in each component's guideline file. Never pass a value not in the documented list.

## Color and theme

Mood and theme are inherited from the application context. To shift the theme of a section, apply the mood at the wrapping container level using the `default` or `mood-inverse` token set. See `guidelines/foundations/colors/overview.md`. Two mood contexts are supported: `default` and `mood-inverse`.

## Primitive vs composite components

Some components are low-level primitives not for direct use in product UIs:

| Primitive | Use instead |
|-----------|------------|
| `RevButtonBase` | `RevButton`, `RevButtonIcon`, `RevButtonCard` |
| `RevCheckboxBase` | `RevCheckbox` |
| `RevRadioBase` | `RevRadio` |
| `RevModalBase` | `RevDialog`, `RevDrawer` |

---

## Actions

```
Triggering an action (no navigation)?
  → Has a text label            → RevButton
  → Icon only                   → RevButtonIcon
  → Entire card surface clicks  → RevButtonCard

Navigating to a URL or route?
  → Inline text link            → RevLink
  → Entire card surface clicks  → RevButtonCard (pass href or to)
```

| Component | File | Description |
|-----------|------|-------------|
| RevButton | `actions/RevButton.md` | Labelled button for triggering actions or navigating |
| RevButtonIcon | `actions/RevButtonIcon.md` | Icon-only button for space-constrained or universally understood actions |
| RevButtonCard | `actions/RevButtonCard.md` | Card-shaped interactive surface where the entire area is the hit target |
| RevLink | `actions/RevLink.md` | Inline text link for navigation within body copy |

---

## Feedback

```
Persistent page-level message (full width)?
  → RevBanner

Large embedded feedback block with icon + title?
  → RevInfoBlock

Small count or status indicator?
  → RevBadge

Transient notification (auto-dismisses)?
  → RevToast (triggered via useToast)

Indeterminate loading state?
  → Button or inline loading  → RevSpinner
  → Content placeholder       → RevSkeleton
```

| Component | File | Description |
|-----------|------|-------------|
| RevSpinner | `feedback/RevSpinner.md` | Animated indeterminate loading indicator |
| RevSkeleton | `feedback/RevSkeleton.md` | Pulsing placeholder shape shown while content loads |
| RevBadge | `feedback/RevBadge.md` | Small count or status dot positioned alongside an icon or label |
| RevBanner | `feedback/RevBanner.md` | Full-width page-level notification bar for persistent messages |
| RevInfoBlock | `feedback/RevInfoBlock.md` | Embedded feedback block with icon, title, and optional actions |
| RevToast | `feedback/RevToast.md` | Auto-dismissing transient notification triggered via useToast |

---

## Layout

```
Constrain page content to the responsive grid?    → RevContainer
Separate sections or list items visually?          → RevDivider
Structured editorial section (heading + body + image + CTA)?  → RevContentBlock
Chat bubble or message thread item?                → RevMessage
```

| Component | File | Description |
|-----------|------|-------------|
| RevContainer | `layout/RevContainer.md` | Responsive max-width wrapper that enforces grid margins and gutters |
| RevDivider | `layout/RevDivider.md` | Visual separator line between content sections or list items |
| RevMessage | `layout/RevMessage.md` | Conversational message bubble for chat threads and message history |
| RevContentBlock | `layout/RevContentBlock.md` | Editorial section combining heading, body copy, image, and CTA buttons |

---

## Media

```
Display a single image?                                        → RevImage
Inspectable gallery (zoom, full-screen, multi-image)?          → RevMediaViewer
Country indicator (locale, shipping, phone)?                   → RevCountryFlag
Person or entity identifier?                                   → RevAvatar
Show a colour option or palette chip?                          → RevColorSwatch
```

| Component | File | Description |
|-----------|------|-------------|
| RevImage | `media/RevImage.md` | Standard image with lazy loading and async decoding defaults |
| RevAvatar | `media/RevAvatar.md` | Circular visual identifier for a person or entity |
| RevColorSwatch | `media/RevColorSwatch.md` | Square chip for displaying a colour option in a product selector |
| RevCountryFlag | `media/RevCountryFlag.md` | Inline country flag image for locale and shipping indicators |
| RevMediaViewer | `media/RevMediaViewer.md` | Full-screen gallery modal for inspecting and navigating images |

---

## Selection

```
Binary on/off setting that applies immediately?    → RevToggle
Multiple independent options (pick many)?          → RevCheckbox (group)
Single choice from a set (pick one)?               → RevRadio (group)

Interactive filter tag (clickable)?                → RevChip
Read-only content label?                           → RevTag
Status indicator with optional action?             → RevPill

Continuous numeric value?                          → RevSlider
Star-based score display?                          → RevRating
```

Notes:
- For more than 7 options in a single-choice set, use RevInputSelect instead of RevRadio.
- RevTag is never interactive. For clickable tags, use RevChip.
- RevRating is display-only. For a star-input picker, build a custom component.

| Component | File | Description |
|-----------|------|-------------|
| RevCheckbox | `selection/RevCheckbox.md` | Checkbox input for multi-select within a group |
| RevRadio | `selection/RevRadio.md` | Radio button for single-select within a group |
| RevToggle | `selection/RevToggle.md` | Binary on/off switch that applies immediately without a submit action |
| RevChip | `selection/RevChip.md` | Interactive filter tag that can be selected, deselected, or cleared |
| RevPill | `selection/RevPill.md` | Status indicator with optional action affordance |
| RevTag | `selection/RevTag.md` | Read-only content label for classification or metadata display |
| RevSlider | `selection/RevSlider.md` | Continuous numeric value input with a draggable handle |
| RevRating | `selection/RevRating.md` | Star-based score display (read-only) |

---

## Forms

```
Need a wrapper for inputs that submit together?     → RevForm

What type of value are you collecting?
  Single-line freeform text                         → RevInputText
  Multi-line freeform text                          → RevInputTextarea
  Number with increment/decrement controls          → RevInputNumber
  Password (masked entry)                           → RevInputPassword
  Phone number with country code selector           → RevInputPhone
  Date with calendar picker                         → RevInputDate
  Single choice from a predefined list              → RevInputSelect
  Single choice from a long list (with filtering)   → RevInputSelectSearchable
  Freeform text with dynamic suggestions            → RevInputAutocomplete
  Multiple choices from a predefined list           → RevInputMultiSelect
```

Notes:
- For binary choices that apply immediately (no submit), use RevToggle (see `selection/`).
- For in-form yes/no or multi-select, use RevCheckbox (see `selection/`).
- For in-form single-select with 2–7 options visible at once, use RevRadio (see `selection/`).
- For more than 7 options or when space is limited, use RevInputSelect.

| Component | File | Description |
|-----------|------|-------------|
| RevForm | `forms/RevForm.md` | Wrapper for grouped inputs that submit together |
| RevInputText | `forms/RevInputText.md` | Single-line freeform text input — the base for most other inputs |
| RevInputNumber | `forms/RevInputNumber.md` | Number input with increment and decrement controls |
| RevInputPassword | `forms/RevInputPassword.md` | Password input with masked entry and reveal toggle |
| RevInputPhone | `forms/RevInputPhone.md` | Phone number input with country code selector |
| RevInputTextarea | `forms/RevInputTextarea.md` | Multi-line freeform text input |
| RevInputDate | `forms/RevInputDate.md` | Date input with calendar picker |
| RevInputSelect | `forms/RevInputSelect.md` | Single-choice dropdown from a predefined list |
| RevInputSelectSearchable | `forms/RevInputSelectSearchable.md` | Single-choice dropdown with inline text filtering |
| RevInputAutocomplete | `forms/RevInputAutocomplete.md` | Freeform text input with dynamic suggestions |
| RevInputMultiSelect | `forms/RevInputMultiSelect.md` | Multi-choice selection from a predefined list |

---

## Navigation

```
Show position within a page hierarchy?             → RevBreadcrumbs
Switch between content sections within a view?     → RevTabs
Pin actions to the bottom (or top) of the screen?  → RevStickyBar
```

| Component | File | Description |
|-----------|------|-------------|
| RevBreadcrumbs | `navigation/RevBreadcrumbs.md` | Hierarchical trail showing the user's position within the site |
| RevTabs | `navigation/RevTabs.md` | Tabbed interface for switching between content sections within a view |
| RevStickyBar | `navigation/RevStickyBar.md` | Fixed bar that pins actions to the bottom or top of the screen |

---

## Data Display

```
Displaying a list of items where each row may be clickable?
  → Simple text entries only              → RevTextList
  → Rich rows (icons, actions, metadata)  → RevList

Tabular data with rows and columns?                        → RevTable

Expandable/collapsible sections?                           → RevAccordionList

Navigating across multiple pages of results?               → RevPagination

Showing progress through a sequence of steps?              → RevStepper
```

| Component | File | Description |
|-----------|------|-------------|
| RevList | `data-display/RevList.md` | Rich list with support for icons, actions, and metadata per row |
| RevTextList | `data-display/RevTextList.md` | Simple text-only list |
| RevAccordionList | `data-display/RevAccordionList.md` | Expandable and collapsible sections for progressive disclosure |
| RevTable | `data-display/RevTable.md` | Tabular data with rows and columns |
| RevPagination | `data-display/RevPagination.md` | Navigation controls for paging through multiple result sets |
| RevStepper | `data-display/RevStepper.md` | Progress indicator for sequential multi-step flows |

---

## Overlays

```
Blocking overlay behind a modal or drawer?                     → RevBackdrop

Need a positioned floating surface (no chrome)?                → RevModalBase

Focused task or confirmation requiring a response?
  → Centred modal with title and actions                       → RevDialog
  → Slides in from an edge                                     → RevDrawer

Contextual options triggered from a point on the page?
  → Anchored dropdown menu                                     → RevContextualMenu
  → Brief label on hover/focus                                 → RevTooltip
```

Notes:
- RevBackdrop and RevModalBase are building blocks — prefer RevDialog or RevDrawer for complete overlay patterns.
- RevPortal behaviour (rendering outside the component tree) is implemented internally by RevDialog, RevDrawer, and RevToast. It is not exposed as a standalone component.

| Component | File | Description |
|-----------|------|-------------|
| RevBackdrop | `overlays/RevBackdrop.md` | Dimming overlay rendered behind modals and drawers |
| RevModalBase | `overlays/RevModalBase.md` | Unstyled positioned floating surface for building overlay patterns |
| RevDialog | `overlays/RevDialog.md` | Centred modal for focused tasks or confirmations requiring a response |
| RevDrawer | `overlays/RevDrawer.md` | Panel that slides in from a screen edge |
| RevContextualMenu | `overlays/RevContextualMenu.md` | Anchored dropdown menu triggered from a point on the page |
| RevTooltip | `overlays/RevTooltip.md` | Brief descriptive label appearing on hover or focus |

---

## Cards

```
Clickable card that is itself the action (no separate CTA button)?  → RevButtonCard (see actions/)

Static content container with header, body, and optional footer?    → RevCard

Displaying a grid of cards?                                         → RevCardGrid

Horizontally scrollable sequence of cards?                          → RevCardCarousel

Category or section navigation card with image?                     → RevCategoryCard

Editorial card with image, title, and description?                  → RevEditorialCard
```

| Component | File | Description |
|-----------|------|-------------|
| RevCard | `cards/RevCard.md` | Static content container with optional header, body, and footer |
| RevCardGrid | `cards/RevCardGrid.md` | Responsive grid layout for a collection of cards |
| RevCardCarousel | `cards/RevCardCarousel.md` | Horizontally scrollable sequence of cards |
| RevCategoryCard | `cards/RevCategoryCard.md` | Navigation card combining an image with a category label |
| RevEditorialCard | `cards/RevEditorialCard.md` | Content card with image, title, description, and optional CTA |

---

## Documents

```
Single file attachment (preview, download, remove)?  → RevDocument

List of file attachments?                            → RevDocumentList
```

| Component | File | Description |
|-----------|------|-------------|
| RevDocument | `documents/RevDocument.md` | Single file attachment with preview, download, and remove actions |
| RevDocumentList | `documents/RevDocumentList.md` | List of file attachments |
