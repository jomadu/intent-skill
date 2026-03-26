# intent-skill

Agent skill for **product and engineering documentation** (building-intent methodology): `docs/product` outcomes and requirements, `docs/engineering` components and implementation specs, phased P1–P4 / E1–E2, and traceability (O/R IDs).

## Layout

| Path | Purpose |
|------|---------|
| [`intent/SKILL.md`](intent/SKILL.md) | Full methodology (same content as `ralph/building-intent.md` in max-ai), plus YAML frontmatter for Cursor skills. |

Install by linking or copying `intent/` (or the folder containing `SKILL.md`) into your skills path (e.g. `.cursor/skills/building-intent/` with `SKILL.md` at that root, or keep `intent-skill/intent/SKILL.md` and point your tooling at `intent/`).

Canonical source in this repo: [`../ralph/building-intent.md`](../ralph/building-intent.md) — update `intent/SKILL.md` when that file changes if you want them to stay in sync.

## Repo layout

| Path | Purpose |
|------|---------|
| `intent/SKILL.md` | Skill definition (building-intent methodology); `name` in frontmatter is `intent` (matches this directory per [Agent Skills](https://agentskills.io)). |
| `intent/assets/*.md` | Document templates (load on demand; keeps `SKILL.md` lean). |
| `docs/release-notes.md` | Where release notes live and how releases are produced. |
| `.github/workflows/release.yml` | CI: commitlint on PR/push; semantic-release on push to release branches. |

## Development

- **Commits** — Conventional commits (validated by commitlint; husky `commit-msg` hook after `npm install`). See [docs/release-notes.md](docs/release-notes.md).
- **Releases** — Semantic-release on push to `main`, `rc`, `alpha`, or `beta`. The **`intent/`** folder is attached as the release asset. Run `npm run semantic-release` for a dry-run.
