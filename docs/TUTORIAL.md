# Tutorial

This package provides pi skills and prompt templates for starting new projects safely, reconstructing codebase knowledge, making safe changes, and reviewing architecture drift.

## Install

From git:

```bash
pi install git:github.com/PriNova/pi-agent-codebase-workflows
```

Local development/test:

```bash
pi install /absolute/path/to/pi-agent-codebase-workflows
# or one-off
pi -e /absolute/path/to/pi-agent-codebase-workflows
```

## Start a new project safely

For small/simple greenfield projects, run all safe-start passes:

```text
/safe-start-all build a small habit tracker web app
```

For larger, higher-risk, or learning-oriented projects, run numbered passes so each decision is reviewable:

```text
/safe-start-01-intent
/safe-start-02-data-flow
/safe-start-03-architecture
/safe-start-04-contract-docs
/safe-start-05-scaffold-plan
/safe-start-06-validation
/safe-start-07-vertical-slice
/safe-start-08-handoff
```

Safe-start is data-first:

```text
input data -> validation/normalization -> domain transformation -> output data/side effects
```

Module boundaries are derived after data flow is understood.

At the start, choose guidance level:

```text
Freshman  - more explanations, command notes, simple questions
Standard  - concise but guided
Expert    - compact, assumption-driven, contract/ADR oriented
```

Safe-start creates project operating docs such as:

```text
README.md
AGENTS.md
docs/agent/PROJECT_INTENT.md
docs/agent/DATA_FLOW.md
docs/agent/DATA_MODEL.md
docs/agent/INVARIANTS.md
docs/agent/ARCHITECTURE.md
docs/agent/DEPENDENCY_RULES.md
docs/agent/RISK_REGISTER.md
docs/agent/TESTING_STRATEGY.md
docs/agent/CHANGE_GUIDE.md
docs/agent/VALIDATION_BASELINE.md
```

After `/safe-start-08-handoff`, use `/skill:safe-change` or safe-change prompts for normal feature, bug, and refactor work.

## Reconstruct a small repo

For small/simple repos, run all reconstruction passes:

```text
/recon-all
```

This creates repo-level docs under:

```text
docs/agent/
```

and project operating guidance at:

```text
AGENTS.md
```

## Reconstruct a large repo or monorepo

Start with inventory:

```text
/recon-01-inventory
```

Use the inventory's recommended targets for scoped passes:

```text
/recon-02-architecture packages/api
/recon-03-data-invariants packages/api
/recon-04-dependency-rules packages/api
/recon-05-risk-register packages/api

/recon-02-architecture apps/mobile
/recon-03-data-invariants apps/mobile
```

Focused path passes write hierarchical scoped docs:

```text
docs/agent/scopes/by-path/packages/api/
  README.md          # optional local index for large/complex scopes
  ARCHITECTURE.md
  DATA_MODEL.md
  INVARIANTS.md
  DEPENDENCY_RULES.md
  DESIGN_ISSUES.md
  RISK_REGISTER.md
  CHANGE_GUIDE.md
  CONTRACTS.md
```

Focused domain passes write:

```text
docs/agent/scopes/by-domain/auth-flow/
```

`docs/agent/SCOPES.md` indexes scoped docs for later workflows.

## Understand generated docs

Repo-level docs:

```text
docs/agent/ARCHITECTURE.md
docs/agent/DATA_MODEL.md
docs/agent/INVARIANTS.md
docs/agent/DEPENDENCY_RULES.md
docs/agent/RISK_REGISTER.md
docs/agent/CHANGE_GUIDE.md
```

Use repo-level docs as summaries and fallback guidance.

Scoped docs:

```text
docs/agent/scopes/by-path/<path>/...
docs/agent/scopes/by-domain/<slug>/...
```

Use scoped docs for package/module/service/domain-specific facts.

`CONTRACTS.md` documents cross-module APIs, shared types, schemas, events, generated clients, persistence boundaries, and ownership.

## Make a safe change

Start with preflight:

```text
/preflight fix login refresh bug in packages/api
```

For a bug:

```text
/bug-diagnose fix login refresh bug in packages/api
/bug-implement approved plan
```

For a feature:

```text
/feature-design add export endpoint to packages/api
/feature-implement approved plan
```

For a refactor:

```text
/refactor-design split billing service adapter
/refactor-implement approved stage 1
```

Safe-change reads `docs/agent/SCOPES.md` when present, matches path scopes by longest prefix, reads scoped docs first, then falls back to repo-level docs.

## Review architecture

Review current diff:

```text
/review-arch
```

Review with explicit focus:

```text
/review-arch packages/api
```

Review checks architecture drift, data consistency, invariants, dependency direction, public contracts, side-effect boundaries, and tests.

## Consolidate scoped findings

After several scoped passes, reconcile them:

```text
/recon-08-consolidate
```

Consolidation keeps detailed facts in scoped docs and summarizes stable repo-level guidance into top-level docs.

## Legacy reconstructed repos

Repos reconstructed before scoped artifacts still work.

If only top-level `docs/agent/*.md` exists:
- safe-change uses those docs
- review uses those docs
- a later focused recon pass creates `docs/agent/SCOPES.md` and scoped artifacts additively
- existing top-level docs are not deleted

Use consolidation later to reconcile old repo-level details with newer scoped docs.
