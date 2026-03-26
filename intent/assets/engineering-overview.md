# Template: Engineering overview — `docs/engineering/README.md`

*Used in **E1** (engineering overview and O/R map).*

The single engineering index. It holds everything that would have been a separate "component index": overview plus component list with requirement assignments.

- Purpose of engineering docs (structure, placement, and implementation specs; product holds who, what, and why at the level of intent).
- High-level diagram or description of the system (e.g. entry point → config → main flow / reporting; orchestrator, api, etc.).
- Component list: for each component, one-line description and **assigned requirement IDs (O/R) as links** to the product requirement documents. Each O/R must link to the requirement file under `docs/product/` (e.g. `../product/O001-<slug>/R002-<slug>.md` from the engineering README). Links to component docs (files or directories under `components/`) point to implementation specs. Component docs hold the implementation specifications (e.g. config schema, APIs) that implementers build from.

**Assigned requirements column:** Use markdown links so each requirement ID points to its product requirement doc. From `docs/engineering/README.md`, the path to a requirement is `../product/O<n>-<outcome-slug>/R<n>-<requirement-slug>.md`. Example table row:

```markdown
| [orchestrator](components/orchestrator.md) | Coordinates the main workflow; loads config, invokes services, decides next step | [O001/R001](../product/O001-<outcome-slug>/R001-<requirement-slug>.md), [O001/R002](../product/O001-<outcome-slug>/R002-<requirement-slug>.md), ... |
```
