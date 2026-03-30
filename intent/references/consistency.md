# Consistency and traceability (structural)

Use alongside artifact-specific review checklists in [`review-product.md`](review-product.md) and [`review-engineering.md`](review-engineering.md). **Product vs engineering language** is covered there—not here.

## Vertical consistency

Child artifacts **support** parent promises:

- Product: product root → outcomes → requirements.
- Engineering: engineering root → components.

Do not contradict a higher level without an explicit **PDR** or **ADR**, or an **updated parent** artifact.

## Horizontal consistency

Sibling artifacts at the same level:

- Do **not** overlap in scope without intent.
- Do **not** contradict each other.
- **Together** cover the parent’s intent where a “complete set” is required (e.g. outcomes as a set, requirements under an outcome).

## Traceability (summary)

- **Meaningful edits** to an in-scope artifact → **CR** at the correct scope (see [`emit-records.md`](emit-records.md)).
- **New product/strategic decision** → **PDR**; **new architectural decision** → **ADR**—not every edit is a decision record.
- **Requirement ↔ component** mapping: **only** as rows in **`docs/engineering/README.md`**—not duplicated as the authoritative list in requirement or component bodies. See [`../assets/CONVENTIONS.md`](../assets/CONVENTIONS.md).
