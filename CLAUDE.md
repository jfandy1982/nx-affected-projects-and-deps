# CLAUDE.md

## Repository Purpose

GitHub Action that detects affected projects (apps, libs, e2e tests) within an Nx monorepo when running against a base branch comparison.

**Outputs:** `affected-projects`, `affected-apps`, `affected-libs`, `affected-e2e`

## Known Structure

- `experiments/` — contains the action definition and development snapshots; deliberate working area
- `node_modules/` — exists locally but is gitignored; not committed to the repo

## Tooling

- GitHub Actions SHAs are manually verified and pinned — do not flag pinned SHAs as outdated without checking first
- Renovate: `renovate.json` in `.github/` is the repository-specific Renovate entry point; the `schedule` override there is intentional
- pre-commit hook runs `lint-staged` (Prettier + cspell) on `*.json`, `*.md`, `*.yml`
