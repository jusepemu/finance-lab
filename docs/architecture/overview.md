# Architecture decisions

## SPA mode (no SSR)

**Decision:** Tranqui uses SvelteKit in SPA mode (`adapter-static` with `fallback: '200.html'`).

**Why:**
- It's a local-first app. There is no server, no remote database.
- All logic runs on the client (IndexedDB via Dexie).
- SSR adds no value when there are no server-side data to hydrate.
- Deployment is trivial: static files on any CDN.

**Where it manifests:**
- `src/routes/+layout.ts` forces `ssr = false`.
- `svelte.config.js` uses `adapter-static` with `fallback`.
- SvelteKit blocks at build time any `+page.server.ts` or `+server.ts` that tries to use `$lib/server/`.

**Implications:**
- No `+page.server.ts` or `+server.ts` files in production.
- All data loading happens via `+page.ts` (universal) or directly in client components.

## Dexie as local database

**Decision:** IndexedDB via Dexie.js as the single source of truth.

**Why:**
- Local-first: user data never leaves their device.
- Native offline support (IndexedDB is part of the browser).
- Dexie abstracts away the complexity of the native IndexedDB API.

**Where it manifests:**
- `src/lib/db.ts` holds the global Dexie instance.
- It's the only runtime dependency (non-dev) in the project.

**Alternatives considered:**
- `localStorage`: no queries, no indexes, 5MB limit.
- SQLite via OPFS: more powerful but less mature browser ecosystem and more complex tooling.

**Current state:** the Dexie instance is created but has no table schema yet. Tables will be defined as features are implemented (incomes, expenses, etc.).

## PWA with auto-update

**Decision:** The app registers as a PWA with the `autoUpdate` strategy.

**Why:**
- A local-first app benefits from being installable like a native app.
- `autoUpdate` is the simplest strategy: the new service worker activates without asking the user.
- With no server-side state to preserve, there's no risk of data loss during updates.

**Where it manifests:**
- `vite.config.ts` configures `SvelteKitPWA` with `registerType: 'autoUpdate'`.

## pnpm as package manager

**Decision:** `pnpm` instead of `npm` or `yarn`.

**Why:**
- `package.json` explicitly declares it with `"packageManager": "pnpm@11.5.2"` and a `pnpm-workspace.yaml` exists.
- Faster, stricter installs (no hoisting by default), which prevents phantom dependencies.

## TypeScript strict

**Decision:** `tsconfig.json` has `"strict": true`.

**Why:**
- The project is in its early stages — the lowest-cost moment to enforce strict typing.
- Dexie's generic types leverage strict mode to catch query errors at compile time.
