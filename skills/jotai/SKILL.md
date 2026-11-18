---
name: jotai
description: Build, review, debug, or migrate React state with Jotai v3. Use for v3 atoms, hooks, Provider and stores, async and Suspense, SSR, persistence, utilities, performance, TypeScript, testing, or integrations.
---

# Jotai v3 documentation router

This skill routes Jotai tasks to bundled official documentation. Jotai is an
atom-based state management library for React: small pieces of source state can
be shared between components, combined into derived values, and updated through
explicit actions. Use it for shared client state, computed state, async reads,
and state that needs persistence or an isolated store.

The skill provides a task-to-document map, not a replacement API manual or a
prescribed application architecture. Its references cover core APIs, utilities,
recipes, integrations, and migration guidance. Start with the matching route
below, read only the relevant pages, and use those pages to guide implementation,
review, or debugging in the project's existing patterns.

This skill covers **Jotai v3 only**. Confirm the installed version before using
it; consult the official docs for v2. Bundled third-party packages are optional,
not dependencies to introduce by default.

## Example tasks and where to start

| Example                                                                                                                                    | Read first                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| Use Jotai to share a shopping cart between unrelated components and derive its total without storing a second copy of that total.          | `references/core/atom.mdx`, `references/core/use-atom.mdx`                                               |
| Use Jotai to coordinate search filters and pagination through a single write action while components subscribe to the values they display. | `references/core/atom.mdx`, `references/guides/composing-atoms.mdx`                                      |
| Use an async atom to load details for the selected item and show pending content through React Suspense.                                   | `references/guides/async.mdx`, `references/core/use-atom.mdx`                                            |
| Persist a user's theme preference in browser storage while accounting for server rendering and hydration.                                  | `references/utilities/storage.mdx`, `references/utilities/ssr.mdx`                                       |
| Give each editor instance its own state, or isolate server requests, using a Provider and the appropriate store scope.                     | `references/core/provider.mdx`, `references/core/store.mdx`, `references/utilities/ssr.mdx`              |
| Investigate unnecessary list rerenders before deciding whether derived atoms, selective subscriptions, or split atoms are appropriate.     | `references/guides/performance.mdx`, `references/utilities/select.mdx`, `references/utilities/split.mdx` |
| Migrate an existing Jotai application to v3 by checking compatibility requirements and changed APIs against its actual usage.              | `references/guides/migrating-to-v3.mdx`                                                                  |

Jotai is not required for every React state value; keep component-local state
local when sharing or composing it would add no value. For an existing codebase,
preserve its state ownership and store boundaries unless the task calls for a
change.

## Routing workflow

1. Inspect the project's Jotai version, dependencies, existing atoms, and store
   boundaries; identify whether the task is implementation, debugging, review,
   migration, or performance work.
2. Choose the closest example above or a topic in the reference index below.
   Read the relevant core page before a recipe or extension that builds on it.
3. Follow links to additional bundled pages only when the task needs them.
   Check package names, compatibility, and API signatures in the references
   rather than treating an example as a complete specification.
4. Apply the smallest appropriate change and verify the requested behavior in
   the project's existing test and runtime setup. Include isolation, async
   states, or persistence checks when those behaviors are involved.

## References

Official Jotai docs, bundled unmodified as MDX from v3.0.2 (commit
`9de9377d10a5ac01388764b89458e2d7091d29d4`; MIT, see `references/LICENSE`). The
v2 migration guide is excluded; where a page mentions older versions, follow
only its v3 guidance. Read only the pages relevant to the task.

- Overview: `references/index.mdx`
- Basics: `references/basics/` — `concepts`, `comparison`,
  `functional-programming-and-jotai`, `showcase`
- Core: `references/core/` — `atom`, `use-atom` (all hooks), `store`, `provider`
- Utilities (`jotai/utils`, `jotai-family`): `references/utilities/` — `async`,
  `callback`, `family`, `lazy`, `reducer`, `resettable`, `select`, `split`,
  `ssr`, `storage`
- Guides: `references/guides/` — `async`, `atoms-in-atom`, `composing-atoms`,
  `core-internals`, `debugging`, `initialize-atom-on-render`, `migrating-to-v3`,
  `nextjs`, `performance`, `persistence`, `react-native`, `remix`, `resettable`,
  `testing`, `typescript`, `using-store-outside-react`, `vite`, `waku`
- Recipes: `references/recipes/` — `atom-with-broadcast`, `atom-with-compare`,
  `atom-with-debounce`, `atom-with-listeners`, `atom-with-refresh`,
  `atom-with-refresh-and-default`, `atom-with-toggle`,
  `atom-with-toggle-and-storage`, `custom-useatom-hooks`, `large-objects`,
  `use-atom-effect`, `use-reducer-atom`
- Extensions (separate packages): `references/extensions/` — `cache`, `effect`,
  `immer`, `location`, `optics`, `query`, `redux`, `relay`, `scope`, `trpc`,
  `urql`, `valtio`, `xstate`, `zustand`
- Third-party: `references/third-party/` — `bunja`, `eager`, `history`
- Tools: `references/tools/` — `babel`, `devtools`, `rolldown`, `skill`, `swc`

Each page is `references/<section>/<name>.mdx`.
