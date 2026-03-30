# Review criteria — product tree

Use for **AI review** and **second human review** after drafting. **Language:** product-facing docs use **product language**—who, value, outcomes; **precise** where it helps; avoid undefined jargon. Do not leak implementation-heavy vocabulary into product-only sections where it would confuse intent.

## Structural consistency (product tree)

- **Vertical:** Child artifacts **support** parent promises (product root → outcomes → requirements). Do not contradict a higher level without an explicit **PDR** or an **updated parent** artifact.
- **Horizontal:** Sibling outcomes and sibling requirements **do not** overlap in scope without intent, **do not** contradict each other, and **together** cover the parent’s intent where a complete set is required.
- **Traceability:** **New product/strategic decision** → **PDR**; **meaningful edits** → **CR** at the right scope ([`emit-records.md`](emit-records.md)). Do **not** treat requirement files as the authoritative list of which components satisfy them—that mapping is **only** in **`docs/engineering/README.md`** ([`../assets/CONVENTIONS.md`](../assets/CONVENTIONS.md)).

## Product root README

- **Scope:** Clear **who** you help, **what** problem space, **what value**; boundaries explicit (in/out).
- **Outcomes list:** Each outcome has a **one-line description**; the set is **complete** for the narrative, **non-overlapping**, **non-contradictory**, and uses **one** decomposition style (simple vs JTBD—not mixed).
- **JTBD product root** ([`../assets/product-root-jtbd.md`](../assets/product-root-jtbd.md)): **Core functional job** is **solution-agnostic**; **job step** blocks under **Core functional job** read as **process** (job map), not customer journey or purchase funnel; **Buyer** / **purchase** is not conflated with the core job when both appear; **omit** sections that add no value—no empty placeholder headings.
- **Consistency:** Aligns with methodology and any parent charter.

## Outcomes (list / one-liners in root)

- **Well scoped**, **non-overlapping**, **non-contradictory**, **complete set**, **vertical consistency** with product root, **product language**.

## Outcome README (detail phase)

- **Purpose:** Outcome is **understandable alone**: problem, user/job context, success in product terms.
- **Boundaries:** In vs out; relation to **sibling outcomes** (no duplicate ownership of the same job).
- **Vertical:** Matches one-liner and product root; if something shifted, update product root or add a **PDR**.
- **Horizontal:** Consistent with **other outcome READMEs** (terminology, level of detail, no conflicting claims).

## Requirements (one-liners per outcome)

- **Derivation:** Requirements **trace** to mitigating **risks** to the outcome (when risks are in play) and read as **verifiable needs**, not implementation.
- **Set quality:** **Complete** for the outcome at this level, **non-overlapping** where possible, **non-contradictory**.
- **Vertical:** Each requirement **supports** its outcome; no silent scope expansion without updating the outcome or a **PDR**.
- **Horizontal:** No conflict with sibling outcomes’ requirements unless resolved upstream.
- **Multi-component:** Wording allows **several components** to satisfy one requirement.

## Requirement artifact (simple file or complex directory)

- **Clarity:** What must be true, for whom, why it matters (acceptance-oriented where useful).
- **Scope:** Matches the one-liner; complex dirs: **README canonical**; siblings are supporting.
- **Traceability:** Do **not** treat the requirement file as the place that lists **which components** satisfy it; that list belongs in **`docs/engineering/README.md`**.

## PDRs (simple or complex)

- **Decision:** What was decided, why alternatives were rejected or trade-offs made, and **scope** of applicability.
- **Strategic fit:** Aligns with product root/outcomes; if direction changes, **parents updated** or PDR marks **supersession**.
- **Emit rule:** **New product/strategic decision only**—not a substitute for a CR.
