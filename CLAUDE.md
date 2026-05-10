# CLAUDE.md

## Repository Purpose

GitHub Action that detects affected projects (apps, libs, e2e tests) within an Nx monorepo when running against a base branch comparison.

**Outputs:** `affected-projects`, `affected-apps`, `affected-libs`, `affected-e2e`

## Known Structure

- `experiments/` — contains the action definition and development snapshots; deliberate working area
  - `experiments/superpowers/` — brainstorming specs and implementation plans from Claude sessions (gitignored, local only); check here for prior design decisions before starting new work
- `node_modules/` — exists locally but is gitignored; not committed to the repo

## Tooling

- GitHub Actions SHAs are manually verified and pinned — do not flag pinned SHAs as outdated without checking first
- Renovate: `renovate.json` in `.github/` is the repository-specific Renovate entry point; the `schedule` override there is intentional
- pre-commit hook runs `lint-staged` (Prettier + cspell) on `*.json`, `*.md`, `*.yml`; additionally runs `js-yaml` syntax validation on `*.yml`, `*.yaml`

### Commands

These NPM scripts can be used beside pre-commit-hooks to enforce proper spelling and formatting.

```bash
npm run format:all          # format all JSON/MD/YML files with Prettier
npm run format:all:check    # verify formatting without writing
npm run spell:all:check     # run cspell on the whole repo
npm run spell:dict:search   # search word in available dictionaries; reveals which dict to enable in .cspell.json
npm run yaml:all:check      # validate YAML syntax in .github/workflows
```
