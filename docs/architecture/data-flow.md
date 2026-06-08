# Data flow

## Principle: the DB is the source of truth

No UI component modifies the database directly.
Every write goes through a validation layer before touching Dexie.

## Read flow

```
User navigates to /incomes
        │
        ▼
+page.svelte loads data (onMount, +page.ts, or reactive statement)
        │
        ▼
Data access layer → db.incomes.toArray()
        │
        ▼
Dexie reads IndexedDB → returns data
        │
        ▼
UI updates with the fetched data
```

**Read rules:**
- Dexie queries are async. Every function that reads from the DB returns a `Promise`.
- The data access layer lives in the same folder as the feature that uses it (see `folder-structure.md`). It only moves to `$lib` if another feature needs the same query.
- Every data load must handle three states: loading, error, and empty.

```ts
// Example data access layer for a feature
// src/routes/incomes/incomes.db.ts

import { db } from '$lib/db';

export function loadIncomes(): Promise<Income[]> {
  return db.incomes.toArray();
}
```

## Write flow

```
User fills out form and saves
        │
        ▼
+page.svelte calls addIncome(data)
        │
        ▼
Data access layer:
    1. validateIncome(data)    ← pure validation (no side effects)
    2. If error → throw (form displays the error)
    3. If ok → db.incomes.add(data)
        │
        ▼
Success → reload data → UI reflects the new state
```

**Write rules:**
- Validation is a pure function: receives data, returns `{ ok: true, data }` or `{ ok: false, errors }`. It does not touch the DB.
- The data access layer orchestrates validation + write. The component only calls the function and handles the result.
- After a successful write, the list is reloaded from Dexie to reflect the actual state.

```ts
// Example write flow with validation
// src/routes/incomes/incomes.db.ts

import { db } from '$lib/db';

export function validateIncome(data: unknown): { ok: true; data: Income } | { ok: false; errors: string[] } {
  // ... pure validation logic
}

export async function addIncome(data: unknown): Promise<Income> {
  const result = validateIncome(data);
  if (!result.ok) throw new ValidationError(result.errors);
  const id = await db.incomes.add(result.data);
  return { ...result.data, id };
}
```

## UI states every feature must handle

| State   | What to show                    | When                                             |
|---------|---------------------------------|--------------------------------------------------|
| Loading | Spinner / skeleton              | First load (no data yet, not even an empty array) |
| Empty   | "No data yet" message + CTA     | Load succeeded but the collection is empty        |
| Error   | Error message + retry button    | Load or write failed                              |
| Data    | Rendered data                   | Load succeeded with data                          |

**Don't mix "no data" with "loading".** An empty array after a successful load is different from `undefined` while waiting for the response.
