## Directory Structure

```txt
docs/
	product/
		README.md
		crs/
			CR001-complex-change-record/
				README.md
				...
			CR002-simple-change-record.md
			...
		pdrs/
			PDR001-complex-product-decision-record/
				README.md
				...
			PDR002-simple-product-decision-record.md
			...
		outcomes/
			O001-outcome/
				README.md
				crs/
					O001-CR001-complex-change-record/
						README.md
						...
					O001-CR002-simple-change-record.md
					...
				pdrs/
					O001-PDR001-complex-product-decision-record/
						README.md
						...
					O001-PDR002-simple-product-decision-record.md
					...
				requirements/
					O001-R001-complex-requirement/
						README.md
						...
					O001-R002-simple-requirement.md
					...
			...
	engineering/
		README.md
		crs/
			CR001-complex-change-record/
				README.md
				...
			CR002-simple-change-record.md
			...
		adrs/
			ADR001-complex-architectural-decision-record/
				README.md
				...
			ADR002-simple-architectural-decision-record.md
			...
		components/
			C001-complex-component/
				crs/
					CR001-complex-change-record/
						README.md
						...
					CR002-simple-change-record.md
					...
				adrs/
					C001-ADR001-complex-architectural-decision-record/
						README.md
						...		
					C001-ADR002-simple-architectural-decision-record.md
					...
				README.md
				...
			C002-simple-component.md
			...
```

- Overview
- Structure
- Product Directory
	- Structure:w
	- Product Root README
		- Links to templates:
			- Simple Product Root README
			- Jobs-to-be-done Product Root README
- Outcomes Directory
- Outcome Directories
	- Outcome README
		- Links to templates:
			- Simple Outcome README
			- Jobs-to-be-done Outcome README
- Requirements Directories
- Simple Requirement Files
	- Links to templates:
		- Simple Requirement File
- Complex Requirement Directories
	- Links to templates:
		- Complex Requirement Directory Structure
	- Complex Requirement README
		- Links to templates:
			- Complex Requirement README
- Product Decision Records (PDRs) Directories
	- Root-Level PDRs Directory
	- Outcome-Level PDRs Directories
- Simple PDR Files
	- Links to templates:
		- Simple PDR File
- Complex PDR Directories
	- Links to templates:
		- Complex PDR Directory Structure
	- Complex PDR README
		- Links to templates:
			- Complex PDR README
- Engineering Directory
	- Engineering Root README
- Components Directory
- Simple Component Files
	- Links to templates:
		- Simple Component File
- Complex Component Directories
	- Links to templates:
		- Complex Component Directory Structure
	- Complex Component README
		- Links to templates:
			- Complex Component README
- Architectual Decision Record (ADRs) Directories
	- Root-Level ADRs Directory
	- Component-Level ADRs Directories
- Simple ADR Files
	- Links to templates:
		- Simple ADR File
- Complex ADR Directories
	- Links to templates:
		- Complex ADR Directory Structure
	- Complex ADR README
		- Links to templates:
			- Complex ADR README
- Change Records (CRs) Directories
	- Product Root-Level CRs Directory
	- Product Outcome-Level CRs Directories
	- Engineering Root-Level CRs Directory
	- Engineering Component-Level CRs Directories
- Simple CR Files
	- Links to templates:
		- Simple CR Files
- Complex CR Directories
	- Links to templates:
		- Complex CR Directory Structure
	- Complex CR README
		- Links to templates:
			- Complex CR README
- Decomposing Products into Outcomes
	- Jobs-to-be-done Approach
		- Links to templates:
			- Jobs-to-be-done Product Root README
			- Jobs-to-be-done Outcome README
- Templates
	- Simple Product Root README
	- Jobs-to-be-done Product Root README
	- Simple CR File
	- Complex CR README
	- Simple PDR File
	- Complex PDR README
	- Simple ADR File
	- Complex ADR README
	- Simple Outcome README
	- Jobs-to-be-done Outcome README
	- Simple Requirement File
	- Complex Requirement README
	- Simple Component File
	- Complex Component README

## Product Directory (`docs/product/`)

- Outcomes articulate success for customers or the business.
- Requirements define specific conditions that need to be met to achieve outcomes.
- Product Decision Records (PDRs) capture why something was decided, so that outcomes and requirements stay explainable over time.

Must contain a product root README.

Must contain a `outcomes/` directory with at least one outcome.

If any root-level PDRs exist, they are contained in a `pdrs/` directory.

### Product Root README (`docs/product/README.md`)

Provides a high level description of the product and decomposes the product into outcomes.

Template: [product-root-readme-template](./assets/product-root-readme-template.md)

### Outcomes Directory (`docs/product/outcomes/`) 

### Outcome Directory (`docs/product/outcomes/<outcome-slug>/`)

Articulate what success looks like for customers or the business in a durable way.

Must contain an outcome README.

Must contain a `requirements/` directory with at least one requirement. 

Can contain a `pdrs/` directory if there is at least one related PDR.

Outcomes are **directories only** (not a single `.md` file beside sibling outcome folders). That keeps **at least one file per requirement** under `requirements/`, with normal paths and headings to link to—instead of inlining requirements inside one outcome document, which is awkward to reference.

- **Folder per outcome** — Must include `README.md` at `docs/product/outcomes/<outcome-slug>/README.md` as the entry point. Room for narrative, supporting material, and nested `pdrs/` and `requirements/` per the directory structure above, all rolling up to the same success target.

#### Outcome README (`docs/product/outcomes/<outcome-slug>/README.md`)

Template: [outcome-readme-template](./assets/outcome-readme-template.md)

### Requirements

**Role:** Specific, checkable conditions that make an outcome satisfied in practice—what must be true for delivery and validation.

#### Simple Requirements

- **One file** — Linked parent outcome, acceptance criteria, status, and traceability as light or heavy as needed.

#### Complex Requirements

- **Folder** — When one requirement needs decomposition, history, experiments, or many linked artifacts.

### Product Decision Records (PDRs)

**Role:** Capture why something was decided—alternatives, tradeoffs, and implications—so requirements and outcomes stay explainable over time.

#### Simple PDRs

- **Compact decision log** — Standard sections in one place.

#### Complex PDRs

- **Folder** — Same decision with appendices, data, or multi-stakeholder material.

#### Root-Level PDRs

- **Spanning decisions** — Portfolio, platform, or cross-cutting choices that do not belong under a single outcome.

#### Outcome-Level PDRs

- **Local decisions** — Scoped to one outcome and stored with that outcome’s material.

## Engineering

Components name how the system is structured; ADRs record why it is built that way. How you slice components—layers, services, packages, or other shapes—is up to the team. Product docs describe what success means; engineering docs describe how the system realizes it without duplicating product intent.

### Engineering Root

- **What lives here** — How this repo defines engineering documentation (structure of the system and the decisions behind it).
- **How to use it** — When to open the engineering README vs a component vs a root ADR; how IDs and links to product docs work.
- **Conventions** — Naming, ownership, boundaries between component docs and shared or platform docs.

### Components

**Role:** Name and describe units of the system people reason about and change—however you slice them (services, modules, apps, libraries, etc.).

#### Simple Components

- **Single-file components** — Enough for a concise description, boundaries, owners, and pointers when the unit stays small.

#### Complex Components

- **Folder per component** — Room for deeper narrative, diagrams, runbooks, and nested ADRs for decisions that belong to that unit.

### Architectural Decision Records (ADRs)

**Role:** Record why an architectural choice was made—options considered, tradeoffs, and consequences—so components and future changes stay understandable.

#### Simple ADRs

- **Compact decision log** — Standard sections in one file.

#### Complex ADRs

- **Folder** — Same decision with appendices, diagrams, benchmarks, or multi-team context.

#### Root-Level ADRs

- **Cross-cutting decisions** — Standards, platforms, patterns, or org-wide choices that are not owned by a single component.

#### Component-Level ADRs

- **Local decisions** — Scoped to one component; stored with that component’s material (e.g. under its `adrs/`).

