---
name: intent
description: >-
  Product and engineering documentation under docs/product and docs/engineering:
  outcomes, requirements, tangible components, PDRs, ADRs, CRs, and the nested
  directory layout described in this skill. Use when creating or reviewing intent
  docs, decision records, change records, or consistency across product and
  engineering trees.
compatibility: >-
  Markdown-only skill: no bundled scripts, no network or system packages required.
  Human-authored docs; templates are not validated by CI in this repo.
---

# Intent documentation methodology

This skill guides **human** authors through **draft → AI-assisted review → second human review** workflows. Product docs express **who**, **what**, and **why** (intent). Engineering docs express **where** and **how** (implementation), with **tangible** components. **Traceability** from product requirements to components is maintained in **`docs/engineering/README.md`** (table rows; a requirement may map to **multiple** components).

## Defaults

- **Product root template:** pick **one** of **simple** ([`assets/product-root-simple.md`](assets/product-root-simple.md)) or **JTBD** ([`assets/product-root-jtbd.md`](assets/product-root-jtbd.md)). Default to **simple** unless job-centered framing helps. The JTBD template is **one outline** (executor → core job with optional step groups → other executor job types → lifecycle support → buyer); **omit** sections that do not serve a clear need—do not treat every heading as mandatory. **Do not mix** product-root styles in one coherent product tree.
- **JTBD product roots:** load [`references/jtbd-primer.md`](references/jtbd-primer.md) **with** [`assets/product-root-jtbd.md`](assets/product-root-jtbd.md) (methodology context for assistants—see [`references/context-loading.md`](references/context-loading.md) **B1**).
- **Requirement ↔ component mapping:** maintain rows only in **`docs/engineering/README.md`** (see [`assets/engineering-root.md`](assets/engineering-root.md)); do not treat requirement or component files as the authoritative mapping list.

## Emit records (full rules)

PDR = new **strategic/product** decision; ADR = new **architectural** decision; CR = **meaningful edit** to an in-scope artifact. Details and scopes: [`references/emit-records.md`](references/emit-records.md).

## Gotchas

- **PDR** ≠ **CR**; **ADR** ≠ **CR**. Do not create a PDR or ADR for every edit; do not skip a CR when the scope meaningfully changed.
- **Complex** directories: **`README.md`** is always the canonical narrative; other files are supporting siblings.
- IDs like `O001` / `R001` are **scoped per parent folder**—do not assume they are globally unique across the repo.

## Documentation layout

Canonical tree, simple vs complex, IDs: [`references/docs-layout.md`](references/docs-layout.md).

## Routing (which workflow to open)

| Task | Workflow |
|------|----------|
| Product `README.md` | [`references/workflow-product-root.md`](references/workflow-product-root.md) |
| Outcomes (list + outcome READMEs) | [`references/workflow-outcomes.md`](references/workflow-outcomes.md) |
| Requirements (index + detail) | [`references/workflow-requirements.md`](references/workflow-requirements.md) — methodology: [`references/decomposing-requirements.md`](references/decomposing-requirements.md) |
| `docs/engineering/README.md` | [`references/workflow-engineering-root.md`](references/workflow-engineering-root.md) |
| Components under `components/` | [`references/workflow-components.md`](references/workflow-components.md) |
| Editing existing docs / scope of CR | [`references/workflow-changes.md`](references/workflow-changes.md) |

Supporting references: [`references/context-loading.md`](references/context-loading.md), [`references/consistency.md`](references/consistency.md), [`references/README.md`](references/README.md). JTBD framing: [`references/jtbd-primer.md`](references/jtbd-primer.md) (with [`assets/product-root-jtbd.md`](assets/product-root-jtbd.md)).

## Authoring checklist (short)

- [ ] Use the matching template from [`assets/README.md`](assets/README.md); preserve **fixed section order** among sections you keep. For **JTBD** product roots, load [`references/jtbd-primer.md`](references/jtbd-primer.md) with [`assets/product-root-jtbd.md`](assets/product-root-jtbd.md). For requirement decomposition, see [`references/decomposing-requirements.md`](references/decomposing-requirements.md).
- [ ] **Review** against [`references/review-product.md`](references/review-product.md) or [`references/review-engineering.md`](references/review-engineering.md) as appropriate; CRs: [`references/review-change-records.md`](references/review-change-records.md).
- [ ] **Emit** per [`references/emit-records.md`](references/emit-records.md).

## Templates (`assets/`)

Document templates live in **`assets/`** ([Agent Skills specification](https://agentskills.io/specification.md) optional `assets/` directory). Index: [`assets/README.md`](assets/README.md). Placeholders and naming: [`assets/CONVENTIONS.md`](assets/CONVENTIONS.md). **Section order** inside each template type is fixed—keep headings in order when editing.

| Template | File |
|----------|------|
| Product root (simple) | [`assets/product-root-simple.md`](assets/product-root-simple.md) |
| Product root (JTBD) | [`assets/product-root-jtbd.md`](assets/product-root-jtbd.md) |
| Outcome README | [`assets/outcome.md`](assets/outcome.md) |
| Requirement (simple file) | [`assets/requirement-simple.md`](assets/requirement-simple.md) |
| Requirement (complex dir README) | [`assets/requirement-complex.md`](assets/requirement-complex.md) |
| PDR (simple) | [`assets/pdr-simple.md`](assets/pdr-simple.md) |
| PDR (complex dir README) | [`assets/pdr-complex.md`](assets/pdr-complex.md) |
| CR (simple) | [`assets/cr-simple.md`](assets/cr-simple.md) |
| CR (complex dir README) | [`assets/cr-complex.md`](assets/cr-complex.md) |
| ADR (simple) | [`assets/adr-simple.md`](assets/adr-simple.md) |
| ADR (complex dir README) | [`assets/adr-complex.md`](assets/adr-complex.md) |
| Engineering root | [`assets/engineering-root.md`](assets/engineering-root.md) |
| Component (simple file) | [`assets/component-simple.md`](assets/component-simple.md) |
| Component (complex dir README) | [`assets/component-complex.md`](assets/component-complex.md) |
