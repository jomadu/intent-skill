# <Product name>

<Charter in one short paragraph—highest-level description of what this product doc set is for.>

Omit any **`##` / `###` / `####` section** (or an entire top-level block such as **Job Executor** roles) that does not serve a clear need. **Do not** ship empty placeholders—delete unused headings in the finished README.

## Job Executor

<Optional: who the executor is for this market when it is not obvious.>

### Core Functional Job

**Job statement:** <verb + object + **contextual clarifier**—**solution-agnostic**; defines market framing.>  
**Success in job terms:** <What “done well” means—not a feature list.>

A **job map** is **process** (what must happen to complete the job), not a customer journey or purchase funnel. Group steps however readers will scan them—by phase, by the universal steps below, or a single group. Common universal steps (use, rename, or skip): **Define → Locate → Prepare → Confirm → Execute → Monitor → Modify → Conclude**.

#### <Job step group A — e.g. early in the job>

<Optional one line describing this slice of the process.>

**<Job step>**: <What the customer is trying to get done at this step—solution-independent.>  
**<Job step>**: <…>

| ID | Outcome (one line) |
|----|--------------------|
| [O<NNN>](./outcomes/O<NNN>-<slug>/README.md) | <Desired outcome tied to this part of the job—or leave empty and list only under **Outcomes** below.> |

#### <Job step group B — optional>

**<Job step>**: <…>  
**<Job step>**: <…>

| ID | Outcome (one line) |
|----|--------------------|
| [O<NNN>](./outcomes/O<NNN>-<slug>/README.md) | <…> |

### Related jobs

<Optional: additional functional jobs **before, during, or after** the core job. Omit if none.>

### Emotional and social jobs

<Optional: how the executor wants to **feel** or **be perceived** while doing the core job. Omit if not used.>

## Product Lifecycle Support Team

<Optional: people who **install, transport, repair, maintain, upgrade, dispose of**, or otherwise support the **offering**—**consumption chain** work. Omit if not applicable or if the same people as **Job Executor** with no extra clarity.>

## Buyer

<Optional: **purchase decision**—how the buyer chooses what to acquire (often financial and performance criteria). **Not** a substitute for the **core functional job** above. Omit if the buyer is the same as the executor and adds no separate angle.>

## Boundaries

**In scope:** <…>  
**Out of scope:** <…>

## Outcomes

<Product-level index of outcomes for this doc set. If outcomes already appear only under **Core Functional Job** tables, keep this section as a single index table or merge duplicates—do not maintain two conflicting lists.>

| ID | Outcome (one line) |
|----|--------------------|
| [O<NNN>](./outcomes/O<NNN>-<slug>/README.md) | <Present-tense desired outcome tied to the job> |
| [O<NNN>](./outcomes/O<NNN>-<slug>/README.md) | <…> |

## See also

- Product-scoped decision records: [`./pdrs/`](./pdrs/)
- Product-scoped change records: [`./crs/`](./crs/)
