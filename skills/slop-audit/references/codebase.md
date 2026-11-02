# Codebase tells

Codebase slop is the same failure as interface slop: a default shape chosen without the domain. These entries are review lenses, not laws. A large file is not automatically wrong, and duplication is sometimes cheaper than the abstraction that removes it.

The fix vocabulary lives in `codebase-design`: **module**, **interface**, **depth**, **seam**, **adapter**, **leverage**, **locality**. The scan workflow lives in `improve-codebase-architecture`.

## Structure and coupling

### Implicit coupling

**Looks like:** modules share a global, a singleton, ambient context, or a database table without an interface. Changing one breaks another with no visible dependency at the call site.

**Why it reads as slop:** the dependency is invisible, so the next change is a surprise. Tests cannot isolate the module without the whole app.

**Evidence to collect:** shared mutable state; ambient context; a table read by several modules; a change in module A that requires editing module B with no interface change; tests that need the full application.

**Fix:** make the dependency explicit at a seam: a parameter, an injected adapter, or an event with a typed payload. Keep shared state behind one module.

**Verdict:** valid.

### Layer-first folders

**Looks like:** `controllers/`, `services/`, `repositories/`, `models/`, and `utils/` at the top, with every feature spread across all of them.

**Why it reads as slop:** the structure mirrors the framework, not the domain. A change to one feature requires opening five folders, which hides locality.

**Evidence to collect:** a feature's files in four or more top-level layers; `utils/` as a dumping ground; no feature or domain folder.

**Fix:** group by feature or domain, and keep the layers inside each feature. Keep cross-cutting infrastructure in its own folder. For a small app with one feature, layers are fine.

**Verdict:** conditional.

### Duplication that must stay in sync

**Looks like:** the same validation in the form, the API, and the database; the same status list in three files; copy-pasted handlers that drift.

**Why it reads as slop:** every copy is a future inconsistency. The cost is not the duplicated lines. It is the coordination.

**Evidence to collect:** two or more definitions of one rule; a bug fixed in one place but not the others; comments that say "keep in sync".

**Fix:** one source of truth for the rule: a schema, a shared module, or a generated type. Do not abstract coincidental similarity. Unify only what must change together.

**Verdict:** conditional. Some duplication is cheaper than a wrong abstraction.

### God files

**Looks like:** one 2,000-line file with routing, data access, formatting, and UI. A `utils.ts` that everything imports.

**Why it reads as slop:** many reasons to change in one place means every change risks everything. It also hides the seams.

**Evidence to collect:** file length, export count, number of distinct responsibilities, and churn.

**Fix:** split by reason to change, not by line count. Extract a deep module with a small interface. Keep related code together.

**Verdict:** valid as a trigger. Length alone is not the problem. Mixed responsibilities are.

### Shotgun surgery

**Looks like:** one logical change requires edits in six files across four folders. Adding a field touches the form, the API, the database, the types, the tests, and the docs.

**Why it reads as slop:** knowledge is spread, so no single place owns the change. It is the inverse of locality.

**Evidence to collect:** `git log` for a feature that touches many files; a checklist of files in a pull request; repeated edits to the same set.

**Fix:** colocate what changes together behind one interface. Move the rule to one module and let callers ask it. Use `improve-codebase-architecture` to find the deepening.

**Verdict:** valid.

### Layering violations

**Looks like:** UI imports the database client. Domain code imports HTTP. A component reads `process.env` and calls a vendor SDK.

**Why it reads as slop:** the dependency direction is inverted, so the core cannot be tested or reused without the edge. Changes in infrastructure leak inward.

**Evidence to collect:** the import graph; framework or vendor imports in domain code; tests that need a network.

**Fix:** point dependencies inward. Keep I/O in adapters at the edge. The core takes an interface. Enforce the direction with lint rules where possible.

**Verdict:** valid.

### Pass-through wrappers

**Looks like:** `getUser()` calls `userService.getUser()` calls `userRepo.getUser()` with no added behaviour. A component that only forwards props.

**Why it reads as slop:** the layer adds navigation cost without leverage. The deletion test exposes it: delete it and complexity does not reappear.

**Evidence to collect:** the wrapper body is one call; props forwarded one for one; no validation, mapping, caching, or policy.

**Fix:** delete the wrapper, or give it a real job: validation, mapping, policy, or a transaction boundary. Keep a seam only when something varies across it.

**Verdict:** valid, covered by `codebase-design`.

## State and boundaries

### Representable illegal states

**Looks like:** `isLoading`, `isError`, and `data` can all be true. `status` is a string. Optional fields must travel together. Booleans can contradict.

**Why it reads as slop:** the type permits states the domain forbids, so every consumer guards against impossible combinations. Bugs live in the gaps.

**Evidence to collect:** flag combinations; optional field groups; stringly-typed enums; runtime assertions that the type should have made unnecessary.

**Fix:** discriminated unions, sum types, branded types, or a parser that returns a valid shape. Make the illegal state unrepresentable, then delete the guards.

**Verdict:** valid.

### Validation away from the boundary

**Looks like:** raw JSON travels through the app. Every function checks `if (!user.id)`. The database rejects what the UI should have caught. Errors are thrown deep and handled at the top.

**Why it reads as slop:** invalid data is allowed past the edge, so every layer pays for it. The boundary is the one place with enough context to reject it.

**Evidence to collect:** repeated guards; `any` or `unknown` in the core; validation in the database and UI but not in the parser; error handling far from the cause.

**Fix:** parse and validate at the edge: the HTTP handler, CLI, queue consumer, or form submit. Convert to a typed domain value. Let the core trust it. Handle errors where there is enough context to act.

**Verdict:** valid.

## Source audit

| Original entry | Verdict | Disposition |
| --- | --- | --- |
| Implicit coupling | Valid | Implicit coupling |
| Layer-first folders | Conditional | Layer-first folders |
| Duplication | Conditional | Duplication that must stay in sync |
| Representable illegal states | Valid | Representable illegal states |
| God files | Valid as a trigger | God files |
| Shotgun surgery | Valid | Shotgun surgery |
| Layering violations | Valid | Layering violations |
| Pass-through wrappers | Valid, duplicate | Pass-through wrappers. Covered by `codebase-design` |
| Errors and validation not at the boundary | Valid | Validation away from the boundary |
