# Workflow: Components

Procedure for **component** artifacts under **`docs/engineering/components/`** (simple file or complex directory with **`README.md`**). Templates: [`../assets/component-simple.md`](../assets/component-simple.md), [`../assets/component-complex.md`](../assets/component-complex.md). Conventions: [`../assets/CONVENTIONS.md`](../assets/CONVENTIONS.md).

## Draft session

1. **Load:** **B0** ([`../SKILL.md`](../SKILL.md) slice), **B1**, **B3** (**`docs/engineering/README.md`** and the row you will add or update), **B4** (sibling components when checking overlap), minimal product trace (requirement IDs). Optional: [`context-loading.md`](context-loading.md).
2. **Draft** component doc; **update** the engineering root **components table** to match.
3. **Emit:** **CR** for meaningful component edits; **ADR** at component or engineering scope for **new** architectural decisions—[`emit-records.md`](emit-records.md).

## AI review session

1. **Load:** **B2** [`review-engineering.md`](review-engineering.md) (component), draft, updated table snippet, **B4** as needed.
2. **Incorporate** feedback.

## Second human review

**B2**, final component artifact, relevant engineering root row(s)—[`context-loading.md`](context-loading.md).

## Related

- [`workflow-engineering-root.md`](workflow-engineering-root.md) for the parent README.
