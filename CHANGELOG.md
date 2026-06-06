# Changelog

All notable changes to this project are documented here.

## [Unreleased]

### Added

- Added stronger safe-start schema coverage for `project-intent`, `architecture`, `data-flow`, `data-model`, `risk-register`, `testing-strategy`, `contracts`, and `adr` artifacts so end-users and validators can catch missing greenfield architecture fields.
- Added pass-specific safe-start prompt guidance for prioritized quality attributes, trust boundaries, sensitive data, architecture tradeoffs, reliability, observability, security assumptions, quality-attribute verification, and thin-slice validation.
- Added validation guidance that missing shared schema coverage or missing now-required fields in legacy artifacts should fail `/validate-structured-docs` audits.

### Changed

- Upgraded `safe-start` workflow semantics so greenfield passes explicitly capture prioritized quality attributes, operating constraints, success metrics, trust boundaries, sensitive data handling, architecture alternatives/tradeoffs, reliability expectations, observability expectations, and security assumptions before scaffolding.
- Clarified README/tutorial/runtime docs that shared schemas are user-facing contracts and that validation should treat older artifacts missing newly required fields as invalid until repaired or migrated.

### Fixes

- Clarified envelope `artifact_id` generation across write-capable structured-doc workflows so scoped artifact IDs use `<scope.id>/<artifact-slug>` instead of invalid second-colon form.

## [0.5.1] - 2026-05-25

### Fixes

- Defined exact overlay-path `<workspace-fingerprint>` resolution across all skills, shared runtime refs, prompt templates, README, tutorial, and troubleshooting docs: canonicalize `workspace_root`, strip one leading slash/backslash, replace every slash/backslash/colon with `-`, wrap with `--`. Concrete example included.

## [0.5.0] - 2026-05-24

### Changed

- Switched workflow docs and prompts to treat `docs/agent/api` as a logical layout under a resolved docs root, with `safe-start` creating the initial repo-local root and other workflows defaulting to a global overlay when repo-local docs are absent.
- Removed package-published validator/runtime scripts and deleted bundled examples so the package ships only runtime skill/prompt assets and top-level docs.
- Simplified validation guidance to best-effort agent inspection and re-read instead of packaged validator commands.

### Fixes

- Clarified prompts, skills, README, tutorial, and troubleshooting so third-party repos are not implicitly treated as adopters of repo-local structured docs.

## [0.4.0] - 2026-05-20

### Added

- Added canonical structured artifact runtime references and per-artifact JSON schemas under `skills/_shared/references/`.
- Added `structured-docs-migration` skill and `/migrate-structured-docs` prompt for legacy prose-to-YAML migration.
- Added structured artifact validation scripts and validator tests.
- Added migration and structured artifact examples for risk-register conversion.

### Changed

- Shifted workflows to canonical YAML artifacts under `docs/agent/api/**` as the source of truth.
- Deprecated legacy project-agent prose Markdown artifacts under `docs/agent/*.md` and scoped prose docs.
- Kept root `AGENTS.md` as allowed harness interoperability Markdown output when explicitly produced.
- Updated prompts, skills, README, tutorial, and troubleshooting to structured artifact model.

### Fixes

- Fixed validator dangling-reference checks to include `ev:*` evidence references.
- Fixed read-only review prompt wording to remove write/update protocol mismatch.
- Clarified migration prompt wording: no Markdown fallback artifacts, while allowing root `AGENTS.md` when explicitly produced.

## [0.3.2] - 2026-05-19

### Added

- Added workflow context-budget and non-duplication guidance across safe-start, codebase-recon, safe-change, and architecture review.
- Added artifact ownership guidance to keep agent docs as source-of-truth shards or routers instead of redundant summaries.

### Fixes

- Made `codebase-recon` create `VALIDATION_BASELINE.md` during inventory passes and `TESTING_STRATEGY.md` during risk-to-tests planning, including scoped equivalents when relevant.
- Added safe-change and architecture-review fallbacks when validation baseline or testing strategy docs are missing.

## [0.3.1] - 2026-05-18

### Added

- Added shared artifact compatibility contracts across `safe-start`, `codebase-recon`, `safe-change`, and `arch-code-review`.
- Added safe-start-compatible artifact handling for `REPO_INVENTORY.md`, `PROJECT_INTENT.md`, `DATA_FLOW.md`, `DESIGN_ISSUES.md`, `TESTING_STRATEGY.md`, `VALIDATION_BASELINE.md`, and `SCOPES.md`.
- Added scoped safe-start guidance for monorepos, enterprise-grade systems, dev-tools platforms, infra/IaC repos, and multi-service systems.
- Added planned/observed/currentness header guidance for durable agent docs.
- Added `CHANGELOG.md` and included it in the package files.

### Fixes

- Fixed workflow drift between safe-start outputs, codebase-recon artifacts, safe-change preflight, and architecture review expectations.
- Fixed scoped-doc read ordering so workflows select matching scoped docs before falling back to repo-level inventory and validation baseline docs.

## [0.3.0] - 2026-05-17

### Added

- Added `safe-start` greenfield project workflow with eight passes from intent capture through handoff to safe-change.
- Added safe-start prompt templates for intent, data flow, architecture, contract docs, scaffold planning, validation baseline, vertical slice, handoff, and all-in-one mode.
- Added README and tutorial coverage for greenfield starts.
- Added package metadata for the `safe-start` skill and prompts.

### Fixes

- None.

## [0.2.0] - 2026-05-15

### Added

- Added hierarchical scoped reconstruction docs for path and domain scopes.
- Added `docs/agent/SCOPES.md` guidance for scope discovery, ownership, status, and external contracts.
- Added scoped-doc support to reconstruction, safe-change, and architecture-review workflows.
- Added modular safe-change reference docs for bug fixes, features, refactoring, risk fixes, preflight, docs updates, and scoped docs.
- Added workflow tutorial and troubleshooting documentation.

### Fixes

- Made scoped `README.md` files optional instead of required for each scope.
- Clarified scoped-doc fallback behavior and review/preflight wording.

## [0.1.1] - 2026-05-14

### Added

- None.

### Fixes

- Clarified consolidation disagreement handling so recon preserves disagreement evidence instead of silently deleting contradictions.

## [0.1.0] - 2026-05-14

### Added

- Added initial pi package for codebase workflow skills and prompt templates.
- Added `codebase-recon` workflow for bounded reconstruction passes, consolidation, ADRs, and risk-to-test planning.
- Added `safe-change` workflow for documented-codebase changes across bug fixes, features, refactors, risk fixes, test-only work, and docs-only work.
- Added `arch-code-review` workflow for architecture-aware review of diffs.
- Added prompt templates for reconstruction, safe-change implementation/design flows, risk fixes, and architecture review.
- Added README, package metadata, MIT license, and pi package configuration.
- Added focus/scope argument documentation across workflows and prompts.
- Added project credits.

### Fixes

- Fixed Mario Zechner credit links.
