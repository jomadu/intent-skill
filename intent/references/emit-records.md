# When to emit PDR, ADR, and CR

| Record | Meaning |
|--------|---------|
| **PDR** (product decision record) | A **product / strategic** decision. |
| **ADR** (architectural decision record) | A **technical / architectural** decision. |
| **CR** (change record) | **What changed** and why, for **traceability** on a defined **scope**. |

## PDR

Emit **only** when there is a **new product/strategic decision**. If there is no new decision, **do not** create a PDR.

## ADR

Emit when there is a **new architectural decision** at the appropriate scope (engineering root vs component). Same spirit as PDR—**decision**, not every edit.

## CR

Emit for **every meaningful edit** to the scopes the CR applies to:

- product **root**
- product **outcome**
- product **requirement**
- **engineering root**
- **component** directories (meaningful component-level edits get CRs too)

**Meaningful change** → **CR** at the right scope. **New strategic/architectural decision** → **PDR** or **ADR** (not replaced by a CR; the CR may **reference** the decision record).

Edge cases: CRs on engineering/component changes may be optional only when trivial; default to **recording meaningful changes**.

## Separation

A **decision** belongs in **PDR/ADR**; the **CR** describes the change and can **point to** the decision record.
