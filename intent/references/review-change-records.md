# Review criteria — change records (CRs)

Use when drafting or reviewing **CRs** at any scope. Pair with [`emit-records.md`](emit-records.md). PDR/ADR **decision** quality is reviewed under [`review-product.md`](review-product.md) and [`review-engineering.md`](review-engineering.md).

## Change records (CRs)

- **Meaningful change:** What changed, why (brief), and **which scope** (artifact/level)—product root, outcome, requirement, engineering root, or component.
- **Completeness:** Cover every **meaningful** edit at those scopes per team policy.
- **Separation:** A **decision** belongs in **PDR/ADR**; the CR can **reference** it.

## Quality bar

- Reader can understand **what** to re-read in the tree without diff access.
- Scope is **unambiguous** (which README or path).
- No contradiction with [`emit-records.md`](emit-records.md)—CRs for edits, PDR/ADR for new decisions.
