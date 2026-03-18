# Release notes

This document describes **where to find release notes** for intent-skill and how releases are produced.

## Where to find release notes

- **Location:** GitHub Releases for this repository. Each tagged release (created by semantic-release on push to `main`, `rc`, `alpha`, or `beta`) has a release page with notes.
- **Content:** For each release, the notes are generated from conventional commits (feat, fix, docs, etc.). Pre-releases (`rc`, `alpha`, `beta` branches) produce prerelease tags; `main` produces stable versions.
- **Asset:** Each release attaches the **`intent/`** folder (the Cursor skill: `SKILL.md` and any sibling files) as a downloadable asset labeled **intent**.

## Release process

Releases are fully automated:

- **Conventional commits:** Use commit types such as `feat:`, `fix:`, `docs:`, `chore:` (and optional scope/body). Commit messages are validated in CI and locally via the husky `commit-msg` hook (after `npm install`).
- **Branches:** Pushes to `main` (stable), `rc`, `alpha`, or `beta` (prereleases) trigger semantic-release. It determines the next version from commits since the last tag, creates the tag, and publishes the GitHub release with generated notes.
- **Dry-run:** From the repo root, run `npm run semantic-release` to see what version would be released and which commits would be included (no tag or release is created).

## Development

- **Commits** — Conventional commits (validated by commitlint; husky `commit-msg` hook). See this doc and [commitlint.config.js](../commitlint.config.js).
- **Releases** — Semantic-release on push to `main`, `rc`, `alpha`, or `beta`. The `intent` folder is published as a release asset.
