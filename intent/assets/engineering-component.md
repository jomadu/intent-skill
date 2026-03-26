# Template: Component — `docs/engineering/components/<component>.md` or `docs/engineering/components/<component>/`

*Used in **E2** (component detail and implementation specs).*

A component may be a single file (e.g. `orchestrator.md`) or a directory (e.g. `orchestrator/`). Use a directory when one file is insufficient.

**When using a single file:** the file contains responsibility and interfaces (below). Do not list O/R IDs; those live only in the engineering README.

**When using a directory:** the component has its own folder. Standard practice is to include a README.md as the primary entry, with the same content as below. Additional files in the directory may cover **implementation specifications** (e.g. a strict config YAML schema doc, API contract), sub-components, data flow, or design notes.

**Fields (in the component's primary doc):**

- **Responsibility** — What this component does in one or a few sentences.
- **Requirements** — Do not duplicate the O/R list. The engineering README is the single source of truth for which requirements are assigned to this component. The component doc may include a one-line reference (e.g. "Implements the requirements assigned to this component in the [engineering README](../README.md).").
- **Interfaces** — Key boundaries: what this component consumes (e.g. config, input) and produces (e.g. exit code, result), and which other components it calls or is called by.
- **Implementation spec** *(or linked doc)* — The authoritative spec implementers build from: e.g. the canonical config YAML schema (all keys, types, nesting, validation), API contracts, state machines, protocols. This is where the "hard" specification lives; product requirements state intent and may reference this doc.

Optional: data flow, invariants, or notes that help implementers place code correctly. Intent (who, what, why) stays in product; implementation specs stay in engineering.
