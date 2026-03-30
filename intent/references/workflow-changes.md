# Workflow: Changing existing artifacts

Procedure when **editing** an established doc (product root, outcome, requirement, engineering root, component)—not only net-new files. Typical loop: **draft → AI review → second human review** (see [`context-loading.md`](context-loading.md)).

## Load

1. **Artifact under edit** + **change intent**.
2. **B3** (parents up the chain) and **B4** (peers) if the change might affect boundaries or overlap.
3. **B5** when emitting records: **CR template** + **exact scope** matching the artifact you changed. Add **PDR** or **ADR** templates only if the session introduces a **new** strategic or architectural **decision**—[`emit-records.md`](emit-records.md).

## Review

Use the checklist for the artifact type:

- Product side: [`review-product.md`](review-product.md)
- Engineering side: [`review-engineering.md`](review-engineering.md)
- CR quality: [`review-change-records.md`](review-change-records.md)

Structural consistency: [`consistency.md`](consistency.md).

## Emit sub-step (PDR / ADR / CR)

Respective template from [`../assets/`](../assets/README.md) + minimal parent context + short summary of the decision or change already drafted.

## Scope reference

| You changed | CR scope (typical) |
|-------------|---------------------|
| `docs/product/README.md` | Product root |
| `docs/product/outcomes/.../README.md` | That outcome |
| Requirement under outcome | That requirement path |
| `docs/engineering/README.md` | Engineering root |
| Component under `components/` | That component |

Pair **PDR** with product parents; **ADR** with engineering parents—see [`emit-records.md`](emit-records.md).
