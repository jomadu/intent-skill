---
name: intent
description: >-
  Product and engineering documentation methodology: outcomes, requirements,
  phased P1–P4 / E1–E2, docs/product and docs/engineering structure. Use when
  creating or reviewing product intent, engineering specs, O/R traceability,
  or consistency across outcomes and components.
---

# Product and Engineering Documentation

This document defines the model for product and engineering documentation. **Product** documentation describes who we're building for, what we're building, and why — outcomes and requirements at the level of *intent*. **Engineering** documentation describes where in the system each capability lives and how the system is built — component-centric architecture, implementation specifications (schemas, interfaces, protocols), and references to product requirements. Together they provide a complete picture: product is the source of truth for intent (who, what, why); engineering is the source of truth for implementation (where and how — structure, placement, and the hard specs implementers build from).

## Structure

```
docs/
  product/
    README.md                        # Index of all outcomes
    O001-<slug>/                     # Outcome dirs use three-digit zero-padded IDs
      README.md                      # Outcome definition (risks, requirement one-liners)
      R001-<slug>.md                 # Requirement — complete for intent (IDs zero-padded to three digits)
  engineering/
    README.md                        # Overview: diagram, design principles, component list with O/R assignments
    components/
      <component>.md                 # Component: responsibility, interfaces, implementation specs; O/R only in README
      <component>/                   # Or component as directory (README + schema docs, design notes as needed)
```

Product answers *who*, *what*, and *why* at the level of intent. Engineering answers *where* and *how*: structure, placement, and the implementation specifications (e.g. config schema, APIs, protocols) that implementers build from. Engineering does not re-specify user-facing intent; it owns the hard specs for how the system is implemented and references product requirements by ID (e.g. O001/R002, O004/R001).

### Product Hierarchy

**Outcome** — A measurable change in the world when this product exists. Outcomes are user-facing and verifiable. They answer *who* we're building for, *what* is true when we succeed, and *why* it matters.

**Requirement** — A capability needed to deliver an outcome. Each requirement belongs to exactly one outcome. The requirement document is **complete for intent**: it contains the capability statement, acceptance criteria, edge cases, and examples that define *what* we're committing to and how we'll verify it. Detailed implementation specifications (schemas, wire formats, algorithms, strict interfaces) may live in engineering; when they do, the requirement states the capability and may reference the engineering doc. The requirement is the single source of truth for *intent*; engineering is the source of truth for the implementation spec. Requirements elaborate the *what* from the outcome: *"what must be true?"* in enough detail that stakeholders and implementers understand the commitment; implementers use engineering docs for the buildable spec.

Every requirement traces to an outcome. If a requirement has no outcome above it, it's unjustified.

### Engineering Hierarchy

**Architecture** — The structure of the system: major components, their responsibilities, and how they interact. Documented in `docs/engineering/` with a component-centric layout.

**Component** — A named part of the system (e.g. orchestrator, config, api, reporting). A component is documented either as a single file (`components/<component>.md`) or as a directory (`components/<component>/`). A component directory standardly includes a README.md as the primary doc, plus optional supporting files (e.g. a strict schema doc for config YAML, API contracts, state diagrams). Requirement assignments (which O/R IDs a component satisfies) live only in the engineering README; component docs do not duplicate that list. Each component's primary doc states responsibility, key interfaces, and the **implementation specifications** that implementers build from — schemas, protocols, data structures — and references the engineering README for the list of requirements it implements. Product is the source of truth for *intent* (what we're committing to); the engineering README is the source of truth for *which component implements which requirements*; the component doc is the source of truth for *how* that component is implemented (where it lives, how it connects, and the strict specs it adheres to).

## Consistency

### Product

Internal consistency is a first-class concern at every step. Each layer of the product tree introduces more documents and more surface area for contradiction.

At every step boundary, before locking, perform a consistency review across two dimensions:

- **Vertical consistency** — Does each document agree with the layer above it? Outcome detail files must match the index. Requirements must match their parent outcome.
- **Horizontal consistency** — Do documents at the same level agree with each other? Outcome files must not make contradictory claims or assume incompatible models of the system. Requirements across different outcomes must not prescribe conflicting behaviors.

Inconsistency at any layer invalidates everything below it. Catching it early is cheap; catching it in implementation is worse.

### Engineering

- Every requirement ID in the engineering README's component list must exist in the product tree (assignments live only in the README).
- Component docs must not contradict each other (e.g. two components claiming to implement the same requirement in incompatible ways).
- Component docs do not duplicate the O/R assignment list; the engineering README is the single place for that.
- When product requirements change, engineering docs (including implementation specs) must be updated so component responsibilities and references remain accurate.
- When an engineering implementation spec changes in a way that affects user-facing contract, the product requirement must be updated.

## Phased Development

Product and engineering each follow a **compress, then expand** pattern: write one-liners (or index-level content) first, lock, then expand into full documents. Compressed forms are cheap to review for consistency; expanded forms are reviewed against the locked compression above them.

### Product (P1–P4)

Product work is organized **by outcome**. You move in **sessions**: each session should load only what that moment needs, and when the slice of work is done you end the session so the next one can start without carrying extra baggage. The usual rhythm within a layer is that you draft something, then come back in a **new** session to review it with fresh eyes, then send it through whatever **human review** your team uses—a pull request, a Confluence workflow, or something similar. When a phase eventually touches every outcome, you also plan for a wider **all-up** session that reads the whole layer together for consistency, followed by another human review, before you treat the phase as locked.

#### P1: Outcome Index

This phase establishes the product on a single page: one line per outcome, still without per-outcome directories. You lock it only after a dedicated review session and human approval.

Spend one session doing nothing but drafting the outcome index. The [product index template](assets/product-index.md) shows the expected shape for `docs/product/README.md` (product summary and outcomes table). Let the README read naturally; tables or prose are both fine, and you do not need to force everything into bullets or numbered lists. The point is a single root `docs/product/README.md` where **each outcome gets one clear line**. Keep verification out of the index—it belongs in each outcome README from P2 onward, which avoids compressing verification into one line and keeps index and detail from drifting apart. Links down into outcome folders are optional here—clarity matters more than navigation. Do not create outcome directories or outcome detail yet. When the draft index feels complete, close the session.

Open a new session when you are ready to **review** that index. Load enough context to judge it fairly: this methodology, the repository’s main README (who the product serves, and the high-level what and why), and the index itself. Work through the review criteria below; when you are satisfied, close the session.

Send the result through human review. After it is approved, lock the index before you begin P2.

**Review criteria:**
- Each outcome is a present-tense assertion about the world, not a feature description
- Each outcome is clear about *who* it is for (users, roles, or personas) and *why* it matters
- Outcomes don't overlap — if two outcomes could share a requirement, they may be the same outcome
- The set of outcomes is complete — together they describe the whole product (who, what, why)
- The set is minimal — removing any outcome would leave a gap

#### P2: Outcome Detail

Here you expand every line in the locked outcome index into a full outcome README. The [outcome README template](assets/product-outcome.md) shows the full layout; in P2 you only fill it through **Non-outcomes**—leave **Risks** and **Requirements** for P3. You walk the outcomes **one at a time**: for each, you draft in one session, review in another, pass human review, and only then move on. When every outcome has been through that loop, you run one more session that reads **all** outcome READMEs together for horizontal and vertical consistency, then you pass human review again before locking P2.

Take the outcomes in whatever order suits you, but always the same pattern. In a **draft** session, load this methodology, the locked index, and any outcome READMEs you have already written so the voice and assumptions stay aligned. Create that outcome’s directory and README—who it is for, the statement, why it matters, verification, and non-outcomes—using that template shape, and stop when the draft feels complete; then close the session. Later, in a **review** session, load the methodology, the index, this outcome’s README, and peer READMEs if comparing them helps. Judge the file against the criteria below, close the session when you are done, and send the change through your human review gate before you start the next outcome.

After **every** outcome has a detail README that has been drafted, reviewed in its own session, and approved by humans, schedule an **all-up** session. Load the index and all outcome READMEs at once and read them as a set for consistency—using the same criteria below, but across the full surface. When that session ends, submit for human review again so you can lock P2.

**Review criteria:**
- Each outcome detail is consistent with its one-liner in the index — if they diverge, fix the index first
- Each outcome explicitly states *who* it is for and *why* it matters
- Verification criteria are defined here (in the outcome README) and are observable by a user, not by a test suite
- Non-outcomes are clear enough that someone could push back on scope and point to this list
- Read all outcome files as a set: no two outcomes make contradictory claims, imply overlapping scope, or assume incompatible models of who we're building for, the system, or the domain

Lock outcome detail before proceeding. Changes after this point ripple through everything below.

#### P3: Requirement Index

This phase adds the compressed requirements layer: risk and requirement **one-liners** in tables on each outcome README, still no per-requirement files. The [outcome README template](assets/product-outcome.md) includes **Risks** and **Requirements** tables—use those layouts with one-line cells and links once requirement IDs exist; do not create separate `R*.md` files yet. You repeat the same shape as P2—**per outcome**, draft in one session, review in another, human review, then move on—until every outcome README carries its tables. Then you run an all-up session across **all** outcome READMEs for cross-outcome consistency, pass human review, and lock the requirement index.

For each outcome README in turn, open a **draft** session with this methodology, the outcome index, and that outcome’s detail doc. Derive requirement one-liners and risks using the decomposition guidance below; append the risks and requirements tables (one-line summaries only). Close the session when that outcome’s tables are drafted. In a later **review** session, bring back the methodology, the index, this README, and peer READMEs when you need to compare wording or scope. Check the outcome against the criteria below, close the session, and send the work through human review before you tackle the next outcome.

When every outcome has been through that cycle, run an **all-up** session with the index and **all** outcome READMEs loaded, and read the requirement layer as a single fabric for cross-outcome issues. Close the session, submit for human review, then lock P3.

**Decomposition** (used during each outcome’s draft session)

- **Why/how/how-else chain** (from goal-oriented requirements engineering): Starting from an outcome, ask (1) *"How is this outcome achieved?"* — each distinct answer is a candidate requirement (if still abstract, decompose further; if concrete enough to build, it's a requirement). (2) *"How else?"* — ask again to avoid locking into one design and to surface gaps. (3) *"Why does this requirement exist?"* — every candidate must trace back to the outcome; if not, it's misplaced or unjustified.
- **Risk analysis:** For each outcome, ask *"What could prevent this from being true?"* Each answer is a risk. Risks surface requirements you'd otherwise discover late. Each risk is documented in the outcome README with the requirement that mitigates it. Every risk must map to an existing requirement or surface a new one. Examples: *"The process crashes mid-execution"* → crash recovery; *"Both success and failure signals appear"* → signal precedence rules; *"The user doesn't know which config value is active"* → provenance tracking.
- **Completeness:** An outcome is fully decomposed when every "how" has a requirement, every risk has a mitigating requirement, every requirement traces back via "why," and you can't name a realistic failure that nothing addresses. Sufficiency for building is the goal, not exhaustive enumeration.

This is the compressed form of the requirements layer. All requirement one-liners and risk mappings across all outcomes should be reviewable as a set.

**Review criteria:**
- Every requirement traces to exactly one outcome
- Requirements are capabilities ("the system detects X"), not implementations ("use a regex to scan for X")
- No requirement is redundant with another under the same outcome
- Every risk maps to a mitigating requirement
- The set of requirements under each outcome is sufficient — you can't describe a realistic failure that nothing addresses
- Read all requirement one-liners across all outcomes as a single set: no two requirements prescribe contradictory capabilities or overlap in scope

Lock requirement one-liners before expanding.

#### P4: Requirement Detail (Complete for Intent)

Here each requirement one-liner becomes a **complete-for-intent** requirement document in its outcome folder. The [requirement template](assets/product-requirement.md) describes fields, example markdown, and how intent stays separate from engineering specs. Again you work **outcome by outcome**: draft the requirement files for that outcome in one or more sessions as needed, review them in a separate session against the criteria below, pass human review, then proceed. When every requirement file exists and has been through that loop, run an all-up session that reads across the whole requirement set (and the index and outcome READMEs as anchors), submit for human review, and lock P4.

For a given outcome, a **draft** pass usually means loading the outcome index, the parent outcome README (with IDs and one-liners), and writing **each** requirement under that outcome into its own file (`R<n>-<slug>.md` beside that README). You might finish an entire outcome in one session or spread files across several; either way, keep an eye on consistency with sibling requirements. Close the session when the draft for that outcome’s scope is in place. A **review** session then loads the parent outcome README and every requirement file for that outcome and checks them against the criteria below. After human review, move to the next outcome.

When **all** requirement files exist, an **all-up** session loads the full requirement layer (plus index and outcome READMEs as needed) and looks for cross-outcome contradictions or drift. Close the session, submit for human review, then lock P4.

**Review criteria:**
- Each requirement document is consistent with its one-liner in the outcome README — if they diverge, fix the one-liner first
- The requirement is complete for intent — clear what we're committing to; acceptance criteria are testable; implementers use product for intent and engineering for implementation specs to build
- Edge cases are enumerated where relevant; examples are concrete (input, expected output, verification)
- The requirement doesn't exceed what the outcome justifies (no gold-plating)
- Read all requirement documents across all outcomes as a single set: no two requirements prescribe contradictory behaviors, make incompatible assumptions, or define the same concept differently
- Requirements remain vertically consistent with their parent outcome detail

Lock requirements before proceeding. Requirement changes ripple; keep them stable once locked.

### Engineering (E1–E2)

Engineering is organized **by component**, not by outcome, but the **feel** matches product: short sessions with only the right context, a draft followed by review in a clean session, and human review before you lock a layer or move to the next component. You can start engineering once the product has at least a requirement index (P3); it is calmer if P4 is locked so requirement IDs stay stable.

#### E1: Overview

E1 produces a **single** engineering README: the component list, one-liners, and the full O/R map—no `components/` detail files yet. The [engineering overview template](assets/engineering-overview.md) walks through what belongs on that page (diagram, component table with linked O/Rs, and so on). You typically spend one session drafting that README, another session reviewing it against the product tree and the criteria below, then you submit for human approval before you touch E2.

In the **first** session, load this methodology, the product outcome index, and the requirement index (every outcome README with requirement one-liners and IDs). From that material, derive components, one-liners, and assignments; write only `docs/engineering/README.md`. When the map is drafted, close the session.

When you are ready to **review**, open a new session. Bring back the methodology, the engineering README you just wrote, and the product tree. Treat this pass as E1’s consistency check against the criteria below. Close the session when you are satisfied, then submit for human review. After approval, lock E1 before any component detail work.

**Decomposition**

Use the product requirement set (and outcome index) to derive the component set. Cluster requirements that hang together — by flow (e.g. everything in the main flow), by concern (e.g. config resolution, service invocation), or by user-facing boundary (e.g. reporting vs. execution). For each cluster, name a component and write a one-liner (what this part of the system is responsible for). Ask *"What part of the system is responsible for this requirement?"* to assign each requirement to a component. Refine until the set is distinct, covers the product, and has no overlapping responsibilities. Record the result in the engineering README: component list with one-liners and O/R assignments as links to the product requirement docs (e.g. `orchestrator — Coordinates the main workflow; decides next step — [O001/R002](../product/O001-<slug>/R002-<slug>.md), [O001/R004](../product/O001-<slug>/R004-<slug>.md), ...`).

**Review criteria:**
- Components are distinct; no two components have the same responsibility
- The set gives a plausible coverage of the system (every product area has a home)
- The overview is consistent with the product outcome index (no components that imply outcomes or requirements not in product)
- Every product requirement is assigned to at least one component
- No component is empty (every component has at least one requirement)
- Boundaries are clear — no two components claim the same requirement in conflicting ways
- Every O/R in the README exists in the product tree

#### E2: Component Detail and Implementation Specs

E2 fills in each component named in the locked engineering README: responsibility, interfaces, and the implementation specs implementers build from. The [component template](assets/engineering-component.md) covers a single file or a directory with README plus optional spec docs. You walk **component by component** in the same spirit as P2–P4—draft in one session, review in another, human review—then, when every component has a doc, you run an all-up session that stresses **cross-component** fit (interfaces, shared assumptions, who owns what) before human review locks the layer.

For each component, a **draft** session should load the locked engineering README and every product requirement document tied to an O/R assigned to **that** component. Write or update `components/<component>.md` or a `components/<component>/` tree (README plus supporting spec files as needed). Close the session when that component’s draft feels complete. Later, a **review** session loads the engineering README, this component’s doc, and neighboring component docs or product requirements whenever boundaries matter. Check against the criteria below, close the session, and send the work through human review before you move to the next component.

After **every** component has a detail doc that has been drafted, reviewed, and approved, schedule an **all-up** session whose job is cross-component consistency—do the handoffs between components match, are interfaces described the same way on both sides, does any requirement sit in two places incompatibly. Close the session, submit for human review, and then treat the architecture as stable enough for ongoing evolution.

**Review criteria:**
- Each component doc matches its one-liner in the engineering README — if they diverge, fix the README first
- Component docs do not list O/R IDs; the engineering README is the single place for assignments
- Implementation specs (schemas, interfaces) are complete enough that an implementer can build from them
- Interfaces are consistent across components (what one component produces, another consumes as documented)

Engineering docs are updated as the system evolves (new requirements, code structure changes); when updating, keep the E1 → E2 hierarchy consistent. When an implementation spec change affects user-facing contract, update the product requirement.

### Working with the trees after methodology

This document is a methodology for generating and reviewing the product and engineering trees. It is not a dependency for day-to-day work once the trees exist. The product documents are self-describing for intent; the engineering documents hold implementation specs and point at product. **Implementers** read product first for intent and acceptance, then engineering for the buildable spec (schemas, interfaces, protocols).

### Why This Order Matters

**Product (P1–P4):** The steps alternate between compression and expansion. Compressed forms (outcome one-liners, requirement one-liners) are easy to hold in your head and cheap to review for consistency. Expanded forms (outcome detail, complete requirement documents) add depth but also surface area for contradiction. By locking the compressed form before expanding, you ensure that the detail is anchored to a reviewed, consistent summary. If you write all layers at once, errors in the upper layers silently propagate downward.

**Engineering (E1–E2):** The same pattern. The overview (E1) produces the full map in one place: component names, one-liners, and O/R assignments in the engineering README. Lock it, then expand into component detail (E2) — responsibility and interfaces per component, anchored to that README.

## Templates

Example markdown and field guidance for each artifact live in `assets/` (per [Agent Skills](https://agentskills.io): load these files when drafting or reviewing, not necessarily with the main skill body). Paths are relative to this skill directory (`intent/`).

| Phase | Template |
|-------|----------|
| P1 | [Product index](assets/product-index.md) — `docs/product/README.md` |
| P2, P3 | [Outcome README](assets/product-outcome.md) — `O<n>-<slug>/README.md` |
| P4 | [Requirement](assets/product-requirement.md) — `R<n>-<slug>.md` |
| E1 | [Engineering overview](assets/engineering-overview.md) — `docs/engineering/README.md` |
| E2 | [Component](assets/engineering-component.md) — `components/<component>.md` or `.../<component>/` |

Phased development above links into these files inline where each step applies.

## Rules

### Naming

- **Product:** Outcomes `O<n>-<slug>/`; requirements `R<n>-<slug>.md` within their outcome. The numeric part `<n>` is **zero-padded to three digits** (e.g. `O001`, `O002`, `R001`, `R002`) so that directories and files sort correctly in the filesystem. Numbered for stable reference, slug for readability. `R001` in O001 and `R001` in O002 are different requirements.
- **Engineering:** Component names are lowercase, hyphenated if multi-word (e.g. `orchestrator.md`, `config.md`). Slugs may change; product IDs (O001, R002) are stable.

### Traceability

- **Product:** Every requirement declares its parent outcome. Every outcome README lists its requirements. The product index lists all outcomes. Product is the single source of truth for intent (who, what, why).
- **Engineering:** Requirement assignments (component → O/R IDs) live only in the engineering README. Component docs reference that README and do not duplicate the list. Engineering is the single source of truth for implementation (which component implements which requirements, and the implementation specs — schemas, interfaces, protocols — that each component adheres to). When an implementation spec changes in a way that affects user-facing contract, the product requirement is updated.

### Lifecycle (Product)

- New outcomes are added when a new problem is identified for a user segment (new who/what/why).
- New requirements are added under existing outcomes when a new capability is needed.
- Requirements without outcomes are removed or reassigned.
- Outcomes without requirements are aspirational — they need decomposition before they can be built.
- Status in the outcome README's requirement table:
  - **draft** — requirement identified, detail incomplete
  - **ready** — requirement complete for intent; implementation spec (if any) lives in engineering
  - **built** — implemented, not yet verified
  - **verified** — acceptance criteria confirmed to pass

### Lifecycle (Engineering)

- Add a component when the product has new requirements or an area that doesn't fit existing components; update the engineering README (names, one-liners, O/R assignments) and add the component doc or directory, including implementation specs (e.g. schema doc) as needed.
- Change or merge components when product or code structure warrants it; update the README and any affected component docs so assignments, interfaces, and implementation specs stay consistent.
- Requirement assignments live only in the engineering README; when requirements or component boundaries change, update the README first, then component docs and any schema/interface specs.
- No separate status for components; a component is "done" when its doc (and any implementation spec docs) exists and matches the README.
