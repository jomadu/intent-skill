# Template: Outcome README — `O001-<slug>/README.md`

*Used in **P2** (outcome detail through **Non-outcomes**) and **P3** (append **Risks** and **Requirements** tables).*

Each outcome directory has a README that fully defines the outcome. Link to requirement docs with `R001-<slug>.md` (three-digit zero-padded IDs).

**Fields:** Who (users/roles/personas), Statement, Why it matters, Verification, Non-outcomes, Risks (table), Requirements (table). Risks and requirements tables are appended in P3. In **P2**, the outcome README stops after **Non-outcomes**; the full template including those tables applies once **P3** begins. Verification here is outcome-level (user-observable evidence); requirement-level testability is captured in each requirement's Acceptance criteria.

```markdown
# O001: <Title>

## Who

<Who this outcome is for: users, roles, or personas.>

## Statement

<One sentence. Present tense. What is true when this outcome is delivered.>

## Why it matters

<The pain without this. What the user suffers today.>

## Verification

<How a user knows this outcome was delivered. Observable evidence, not test cases.>

## Non-outcomes

- <What this does not cover>
- <What this is not responsible for>

## Risks

| Risk | Mitigating Requirement |
|------|----------------------|
| What could prevent this outcome | [R001 — <Title>](R001-<slug>.md) |
| ... | ... |

## Requirements

| ID | Requirement | Status |
|----|-------------|--------|
| [R001](R001-<slug>.md) | One-line summary | draft / ready / built / verified |
| [R002](R002-<slug>.md) | ... | ... |
```
