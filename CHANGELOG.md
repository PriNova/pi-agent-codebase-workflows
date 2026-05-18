# Changelog

All notable changes to this project are documented here.

## [Unreleased]

### Added

- None.

### Fixes

- None.

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
