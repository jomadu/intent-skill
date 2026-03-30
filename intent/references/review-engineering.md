# Review criteria — engineering tree

Use for **AI review** and **second human review** after drafting. **Language:** engineering docs use **precise technical language** where it helps; define terms on first use when needed; keep **shared terminology** aligned with product where concepts overlap.

## Structural consistency (engineering tree)

- **Vertical:** Child artifacts **support** parent promises (engineering root → components). Do not contradict product intent or a higher engineering level without an explicit **ADR**, **PDR** (when product intent shifts), or an **updated parent** artifact.
- **Horizontal:** Sibling components **do not** overlap in mandate without intent and **do not** contradict each other.
- **Traceability:** **New architectural decision** → **ADR**; **meaningful edits** → **CR** at the right scope ([`emit-records.md`](emit-records.md)). **Requirement ↔ component** mapping appears **only** as rows in **`docs/engineering/README.md`**—not duplicated as the authoritative list in requirement or component bodies ([`../assets/CONVENTIONS.md`](../assets/CONVENTIONS.md)).

## Engineering root README

- **System view:** How the product is **realized**—major pieces, constraints, environments, boundaries at a high level.
- **Vertical:** Maps to product outcomes/requirements without contradicting them; gaps explicit.
- **Horizontal:** Shared **terminology** with product where concepts overlap.
- **Mapping table:** The **components** table lists **links to product requirements** per row. Confirm **meaningful** requirement ↔ component relationships; **many-to-many** is shown by repeating the same requirement link on **multiple rows** when several components satisfy one requirement. Template: [`../assets/engineering-root.md`](../assets/engineering-root.md).

## Component (simple or complex)

- **Tangibility:** Reads as **implementable**—not merely a label.
- **Scope:** Responsibilities and **interfaces** (what it does / does not do).
- **Vertical:** Implementation lines up with **product intent**; mismatches are fixed via **ADR**, parent updates, or edits to the **engineering README** mapping—not by silently diverging from the table.
- **Horizontal:** Does not **duplicate** another component’s mandate without explicit split.
- **Traceability:** Do **not** re-list the full requirement ↔ component mapping in the component doc; **`docs/engineering/README.md`** is authoritative.

## ADRs (simple or complex)

- **Decision:** Context, options, **decision**, consequences—**technical/architectural**.
- **Scope:** Matches engineering root vs component; no silent override of root without acknowledgment.
- **Emit rule:** **New architectural decision**—not a stand-in for routine CRs.
