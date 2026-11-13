---
name: jotai
description: Build, review, debug, or migrate React state with Jotai v3. Use for v3 atoms, hooks, Provider and stores, async and Suspense, SSR, persistence, utilities, performance, TypeScript, testing, or integrations.
---

# Jotai v3

This skill covers Jotai v3 only. Consult the official docs for v2.

## Workflow

1. Confirm the project uses Jotai v3; inspect its React version, dependencies,
   store boundaries, and existing patterns before changing code.
2. Model independent source state with primitive atoms, calculations with
   read-only derived atoms, and coordinated actions with writable atoms. Do not
   duplicate derivable state without a reason.
3. Use the existing store scope. Provider-less mode uses a default store;
   `<Provider>` or an explicit `createStore()` isolates subtrees, tests, and
   server requests. Keep server state isolated between requests.
4. Choose the simplest hooks and utilities for the behavior. Read the relevant
   reference below before applying advanced APIs.
5. Verify user-visible behavior in the project's existing test and runtime
   setup, including isolation, async states, and persistence when applicable.

## Design rules

- An atom is a config; its value belongs to a store. Define atoms outside render
  or memoize dynamically created atoms with stable dependencies.
- `get` in a read function tracks dependencies; `get` in a write function does
  not. Use writable derived or write-only atoms for actions.
- Use `useAtomValue` for readers and `useSetAtom` for write-only consumers;
  use `useAtom` when both are needed. Split subscriptions where measurement
  warrants it; prefer normal derived atoms before `selectAtom`.
- Async reads suspend with normal hooks. Provide Suspense and error boundaries
  where appropriate, and pass the supplied abort signal to cancellable work.
- For persisted state, account for storage availability, hydration mismatches,
  cross-tab updates, and invalid or untrusted stored values.
- Preserve TypeScript inference; avoid casts that obscure atom write arguments.
  Keep render work cheap and avoid deep chains of derived atoms.

## Jotai v3 requirements

- v3 requires React 18+, TypeScript 5.5+, and Node.js 22.12+; it is ESM-only
  with public entry-point exports. Confirm compatibility before migrating.
- Import `atomFamily` from `jotai-family` and Babel plugins from `jotai-babel`.
  `loadable` and `setSelf` are unavailable; consult the migration guide when
  upgrading existing code.
- v3 `useAtomValue` may miss updates between initial render and subscription;
  the advanced `useAtomValueRawSync` avoids that window but does not unwrap
  promises and uses synchronous rendering. Choose it only if appropriate.

## References

Official Jotai docs, bundled unmodified as MDX from v3.0.2 (commit
`9de9377d10a5ac01388764b89458e2d7091d29d4`; MIT, see `references/LICENSE`).
The v2 migration guide is excluded; where a page mentions older versions,
follow only its v3 guidance. Read only the pages relevant to the task.

- Overview: `references/index.mdx`
- Basics: `references/basics/` — `concepts`, `comparison`,
  `functional-programming-and-jotai`, `showcase`
- Core: `references/core/` — `atom`, `use-atom` (all hooks), `store`,
  `provider`
- Utilities (`jotai/utils`, `jotai-family`): `references/utilities/` —
  `async`, `callback`, `family`, `lazy`, `reducer`, `resettable`, `select`,
  `split`, `ssr`, `storage`
- Guides: `references/guides/` — `async`, `atoms-in-atom`, `composing-atoms`,
  `core-internals`, `debugging`, `initialize-atom-on-render`,
  `migrating-to-v3`, `nextjs`, `performance`, `persistence`, `react-native`,
  `remix`, `resettable`, `testing`, `typescript`,
  `using-store-outside-react`, `vite`, `waku`
- Recipes: `references/recipes/` — `atom-with-broadcast`, `atom-with-compare`,
  `atom-with-debounce`, `atom-with-listeners`, `atom-with-refresh`,
  `atom-with-refresh-and-default`, `atom-with-toggle`,
  `atom-with-toggle-and-storage`, `custom-useatom-hooks`, `large-objects`,
  `use-atom-effect`, `use-reducer-atom`
- Extensions (separate packages): `references/extensions/` — `cache`,
  `effect`, `immer`, `location`, `optics`, `query`, `redux`, `relay`,
  `scope`, `trpc`, `urql`, `valtio`, `xstate`, `zustand`
- Third-party: `references/third-party/` — `bunja`, `eager`, `history`
- Tools: `references/tools/` — `babel`, `devtools`, `rolldown`, `skill`,
  `swc`

Each page is `references/<section>/<name>.mdx`.
