# Template: Product index — `docs/product/README.md`

*Used in **P1** (outcome index).*

Open with a short **product summary**: a statement that describes the product itself — who it is for, what it is, and what it does — and that the outcomes below are the measurable results of that product. Avoid meta-description of the documentation (e.g. "this index is…"); the README should read as a statement about the product. Then the outcomes table.

Link each outcome ID to that outcome's README. From the index, use `./O001-<slug>/README.md` (three-digit zero-padded IDs). Each outcome one-liner should be clear on *who* it is for, *what* is true when achieved, and *why* it matters. Verification is defined in each outcome's README, not in the index.

```markdown
# Product

<Short product summary: who the product is for, what it is, and what it does. This product produces the outcomes below.>

## Outcomes

| ID | Outcome |
|----|---------|
| [O001](./O001-<slug>/README.md) | Statement of what is true when this outcome is achieved |
| [O002](./O002-<slug>/README.md) | ... |
```
