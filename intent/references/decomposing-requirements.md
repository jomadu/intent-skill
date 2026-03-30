# Decomposing outcomes into requirements

Outcomes do not arrive pre-decomposed. Follow **compress, then expand**: first lock **requirement one-liners** (and risk mappings) in each outcome’s **`README.md`** (see [`../assets/outcome.md`](../assets/outcome.md)), then create requirement files or directories under **`outcomes/<O…>/requirements/`**. Expanded requirement docs are **complete for intent**; implementation specs live in engineering when needed.

## Decomposition

- **Why / how / how-else** — From an outcome, ask (1) *“How is this outcome achieved?”* Each distinct answer is a **candidate requirement** (if still abstract, decompose further; if concrete enough to build, treat it as a requirement). (2) *“How else?”* — ask again so you do not lock into one design and so gaps surface. (3) *“Why does this requirement exist?”* — every candidate must trace back to the outcome; if it does not, it is misplaced or unjustified.

- **Risk analysis** — For each outcome, ask *“What could prevent this from being true?”* Each answer is a **risk**. Risks surface requirements you would otherwise discover late. Document each risk in the outcome README and map it to the **mitigating requirement**. Every risk must map to an existing requirement or force a new one.

- **Completeness** — An outcome is sufficiently decomposed when every “how” has a requirement, every risk has a mitigating requirement, every requirement traces back via “why,” and you cannot name a **realistic failure** that nothing addresses. Aim for enough coverage to build, not exhaustive enumeration.

## Review (requirement index)

Before expanding full requirement documents, review the compressed layer as a set:

- Every requirement traces to **exactly one** outcome.
- Requirements are **capabilities** (“the system detects X”), not implementations (“use a regex”).
- No requirement is **redundant** with another under the same outcome.
- Every risk maps to a **mitigating requirement**.
- The set under each outcome is **sufficient** — you cannot describe a realistic failure that nothing addresses.
- Read **all** requirement one-liners **across outcomes**: no contradictory capabilities or overlapping scope between requirements.

## Review (requirement detail)

After expanding files under `requirements/`, keep **vertical** consistency (each requirement matches its one-liner and parent outcome) and **horizontal** consistency across outcomes (no contradictory behaviors or incompatible assumptions). Apply the same bar to every requirement-detail pass under **`docs/product/outcomes/`**.
