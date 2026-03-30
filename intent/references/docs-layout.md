# Canonical documentation layout

Use this **nested** layout for new work—not ad-hoc flat trees (for example, outcomes must live under `outcomes/`, not only at `docs/product/O001-…` without that segment). **One engineering tree** per **product** root.

## Product (`docs/product/`)

```txt
docs/product/
  README.md
  crs/
  pdrs/
  outcomes/
    O001-<slug>/
      README.md
      crs/
      pdrs/
      requirements/
        O001-R001-<slug>/
          README.md          # complex requirement
          crs/
          pdrs/
        O001-R002-<slug>.md  # simple requirement
```

## Engineering (`docs/engineering/`)

```txt
docs/engineering/
  README.md
  crs/
  adrs/
  components/
    C001-<slug>/
      README.md
      crs/
      adrs/
    C002-<slug>.md           # simple component
```

## Simple vs complex

- **Simple:** a single **`.md`** file.
- **Complex:** a **directory** with **`README.md`** as the canonical narrative; other files are supporting siblings.

## IDs

Prefixes are **scoped per parent directory** (they need not be unique repo-wide). Padding (`O001`, `R001`, …) is a readability convention—align with [`../assets/CONVENTIONS.md`](../assets/CONVENTIONS.md).
