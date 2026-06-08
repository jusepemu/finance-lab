# Folder structure

## Guiding principle

> Start co-located inside the route. Only move to `$lib` when TWO or more routes need it.

This prevents "lib dumping" — throwing everything into `$lib/` just in case — and keeps each feature self-contained and easy to delete or refactor.

## Rules

| Folder | What goes there | When to move to `$lib` |
|--------|-----------------|------------------------|
| `src/routes/[feature]/` | Pages, components, state, and utilities exclusive to that feature | When another route also needs it |
| `src/lib/components/` | Shared UI components (Button, Card, Modal) | — (always shared by design) |
| `src/lib/db.ts` | Dexie instance and table schemas | — (always global, single DB) |
| `src/lib/utils/` | Formatting, helpers, constants used by ≥2 features | If only one feature uses it, it stays in its route |

## Expected future structure

```
src/
├── app.css                  ← global styles (Tailwind)
├── app.html                 ← HTML shell (SvelteKit template)
├── routes/
│   ├── +layout.ts           ← ssr = false (forced for the entire app)
│   ├── +page.svelte         ← home page (dashboard)
│   ├── incomes/
│   │   ├── +page.svelte     ← incomes page
│   │   ├── IncomeForm.svelte     ← only used here
│   │   └── IncomeList.svelte     ← only used here
│   └── expenses/
│       ├── +page.svelte     ← expenses page
│       └── ExpenseForm.svelte
├── lib/
│   ├── db.ts                ← Dexie instance (single source of truth)
│   ├── components/          ← reusable UI components
│   └── utils/
│       └── formatCurrency.ts ← used by incomes AND expenses → justifies living in lib
```

## The "does it belong in lib?" test

To decide whether a module moves to `$lib`:

1. Is it used by more than one route today? → `$lib`
2. Will it clearly be used by more than one route in the immediate future? → `$lib`
3. Is it only used by one route with no concrete reuse plan? → stays in the route

When in doubt, leave it in the route. It's easier to move later than to untangle an overloaded `$lib`.

## What does NOT go in `$lib`

- Feature-specific state or queries (e.g., `useIncomes`). That lives in the feature's route.
- Types used by a single feature.
- Components rendered by a single page.
