# Context loading (per session)

Principles for **what to read** before drafting or reviewing. Pair with workflow files under [`README.md`](README.md) (Workflows).

## Principles

1. **Minimum sufficient graph:** Load the **artifact in scope**, its **parents** (vertical), and **siblings** only when checking overlap, completeness, or horizontal consistency.
2. **Stable before volatile:** Methodology slice → **template** → **review criteria** → upstream canon → draft under work. In **review** sessions, load **criteria before or with** the draft.
3. **One decomposition style:** Load **one** product root template (simple or JTBD)—not several—in the same session.
4. **Decisions vs edits:** If a session may produce a **PDR/ADR**, load the **decision template** and the **smallest parent scope** the decision affects. For **meaningful edits**, load **CR template** and the **scope** the CR belongs to.
5. **Token discipline:** Prefer **README + one-liners** over full trees; pull **full requirement bodies** only for requirement(s) in scope.
6. **Explicit gaps:** If a parent is missing or stale, note it so the assistant does not invent alignment.

## Bundles (B0–B5)

| Bundle | Contents |
|--------|----------|
| **B0** | Intent skill slice for this workflow (roles, emit rules, steps)—not necessarily all of [`../SKILL.md`](../SKILL.md). |
| **B1** | **Template** for the artifact (simple file vs complex `README` + paths). For **JTBD** product roots, include [`jtbd-primer.md`](jtbd-primer.md) with [`product-root-jtbd.md`](../assets/product-root-jtbd.md). |
| **B2** | **Review criteria** for this artifact type ([`review-product.md`](review-product.md) / [`review-engineering.md`](review-engineering.md) / [`review-change-records.md`](review-change-records.md)). |
| **B3** | **Parent chain:** product root → outcome → requirement; or engineering root → component. |
| **B4** | **Peers:** other outcome READMEs, sibling requirements, sibling components—when horizontal checks are needed. |
| **B5** | **Conditional:** PDR/ADR/CR template + **exact scope** (product root \| outcome \| requirement \| engineering root \| component). |

## Session types

| Session | Goal |
|---------|------|
| **Draft** | Produce or revise text/assets. |
| **AI review** | Validate draft against **B2**. |
| **Second human review** | Human judgment; may use **B2** + artifact for a light assistant pass. |

## Second human review (assistant-light)

Load **B2**, the **final artifact**, and a **one-screen parent summary** (e.g. parent headings). Avoid full peer trees unless the reviewer flags a conflict.
