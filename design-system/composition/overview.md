# Composition patterns

Multi-component assemblies for common Back Market product surfaces. Load only the pattern file relevant to your current task.

## When to look here

Use these patterns when assembling multiple components into a complete surface or interaction flow. If you are working on an individual component in isolation, go to `components/overview.md` instead.

```
Async operation result (success / error / info)?           → async-feedback
Single-page data collection form?                          → form
Form inside a dialog for an in-context secondary task?     → modal-form
Filterable, paginated catalog or search results page?      → listing-page
Single product evaluation and purchase page?               → product-detail-page
Multi-step linear transaction flow?                        → checkout
```

## Patterns

| Pattern | File | Description |
|---------|------|-------------|
| Async feedback | `composition/async-feedback.md` | Communicating success or failure after an async operation |
| Form | `composition/form.md` | Single-page data collection form with validation |
| Modal form | `composition/modal-form.md` | Form inside a dialog for in-context secondary tasks |
| Listing page | `composition/listing-page.md` | Filterable, paginated catalog or search results layout |
| Product detail page | `composition/product-detail-page.md` | Product evaluation and purchase layout |
| Checkout | `composition/checkout.md` | Multi-step linear transaction flow |
