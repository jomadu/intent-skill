# Template: Requirement — `R001-<slug>.md`

*Used in **P4** (requirement detail, complete for intent).*

Each requirement file is **complete for intent**: it contains the requirement statement and all detail needed to define what we're committing to and how we'll verify it. No separate "Specification" section; use whatever structure makes the requirement unambiguous (e.g. Detail, Edge cases, Examples, plus Acceptance criteria and Dependencies). Where implementation specifications (schemas, formats, algorithms) live in engineering, the requirement states the capability and may reference the engineering doc.

**Fields:**

- **Outcome** — Which outcome this requirement serves (traceability upward).
- **Requirement** — What the system must do. Written as a capability statement.
- **Detail** — Whatever is needed to make the requirement complete for intent: edge cases table, examples, behavioral rules. Use subsections (e.g. Edge cases, Examples) as needed. Where the authoritative implementation spec (e.g. config schema, API) lives in engineering, reference it here. Implementers use this doc for intent and the engineering doc for the buildable spec.
- **Acceptance criteria** — Concrete conditions that must be true for this requirement to be considered met.
- **Dependencies** *(optional)* — Other requirements or system capabilities that must exist first. Omit if self-contained.

**Standard subsections when useful:**

- **Edge cases** — Table of boundary conditions and expected behavior.
- **Examples** — Concrete scenarios: Input, Expected output, Verification.

```markdown
# R001: <Title>

**Outcome:** O001 — <Outcome title>

## Requirement

<What the system must do. Capability statement.>

## Detail

<Detail needed for intent: edge cases, examples, behavioral rules. Use subsections as needed. If the implementation spec (e.g. schema, API) lives in engineering, add: "See [engineering doc](link) for the authoritative schema/interface.">

### Edge cases

| Condition | Expected Behavior |
|-----------|-------------------|
| <Boundary condition> | <How the system responds> |

### Examples

#### <Scenario name>

**Input:** <Input data, command, or setup>

**Expected output:** <Output data, behavior, or result>

**Verification:** <How to verify the outcome>

## Acceptance criteria

- [ ] <Concrete, testable condition>
- [ ] <...>

## Dependencies

- <O001/R001 — Requirement that must exist first>
```
