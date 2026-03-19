---
name: semantic-release
description: >-
  Set up and use semantic-release for versioning and GitHub releases from
  conventional commits. Use when adding or updating semantic-release in a repo,
  configuring branches/plugins/assets, wiring commitlint and GitHub Actions, or
  when the user asks how to release with conventional commits.
license: GPL-3.0
---

# Semantic release

This skill guides agents through configuring **semantic-release** so that versions and GitHub releases are driven by **conventional commits**: commitlint, releaserc, and a single release workflow.

## When to use this skill

- Adding or updating semantic-release in a repository.
- Configuring branches (main + rc/alpha/beta), plugins (commit-analyzer, release-notes-generator, github), and release assets.
- Wiring commitlint and a GitHub Actions release workflow.
- Explaining or debugging version bumps and release notes from conventional commits.

## Directory layout

Typical layout for a repo using semantic-release with commitlint and GitHub Actions:

```
repo/
├── .releaserc.json          # branches, plugins, github assets
├── .github/workflows/release.yml
├── package.json             # semantic-release, commitlint, husky scripts and deps
├── commitlint.config.js
└── .husky/commit-msg
```

The **asset** in `.releaserc.json` is the path (file or directory) to attach to each GitHub release.

## .releaserc.json

- **Branches:** `main` for stable; `rc`, `alpha`, `beta` for prereleases (each with `prerelease: "<name>"`).
- **Plugins:** Use `@semantic-release/commit-analyzer` and `@semantic-release/release-notes-generator` with `preset: "conventionalcommits"`. Use `@semantic-release/github` with `assets` listing the path(s) and label(s) to attach to each release.
- **Do not** add `@semantic-release/npm` unless the repo is an npm package you intend to publish.

## GitHub Actions release workflow

1. **Commitlint job** — On push and pull_request to main/rc/alpha/beta: checkout with `fetch-depth: 0`, set base ref (PR base, or `event.before`, or merge-base with main/rc, or `HEAD~1`), run `npx commitlint --from <base> --to <head>`.
2. **Release job** — On **push** only to main/rc/alpha/beta; `needs: [commitlint]`; `contents: write`; run `npm ci` then `cycjimmy/semantic-release-action@v4` with `GITHUB_TOKEN`.

So: PRs must pass commitlint; after merge, semantic-release runs and may create a release and upload the asset.

## package.json

- Use `"private": true` if not publishing to npm.
- Scripts: `"semantic-release": "semantic-release"`, `"commitlint": "commitlint --edit"`, `"prepare": "husky"`.
- DevDependencies: `@commitlint/cli`, `@commitlint/config-conventional`, `conventional-changelog-conventionalcommits`, `husky`, `semantic-release`.

## commitlint

- Extend `@commitlint/config-conventional`.
- Use `header-max-length: 100` and the standard `type-enum` (feat, fix, docs, style, refactor, perf, test, build, ci, chore, revert).

## Husky

- In `.husky/commit-msg`, run `npx --no-install commitlint --edit "$1"` so every commit is validated locally.

## Conventional commits → versions

- `feat:` → minor (or prerelease on rc/alpha/beta).
- `fix:` → patch.
- `BREAKING CHANGE:` or `feat!:` → major.
- Other types (docs, chore, etc.) do not trigger a release unless configured.

## Common edge cases

- **No release on PR:** The release job must run only on `push`, not `pull_request`, so that semantic-release runs after merge.
- **Base ref for commitlint:** On push, use `github.event.before` when valid; otherwise merge-base with `origin/main` or `origin/rc` so only new commits are checked.
- **Asset path:** The `path` in `@semantic-release/github` must point to the directory or file to attach to the release (e.g. a built artifact or content directory), not the repo root.
