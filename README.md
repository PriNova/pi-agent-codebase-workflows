# pi-agent-codebase-workflows

Pi package with skills and prompt templates for safe greenfield starts, documented-codebase changes, reconstruction, and reviews.

Credits: built for [pi](https://github.com/earendil-works/pi-mono), created by Mario Zechner ([GitHub: @badlogic](https://github.com/badlogic), [X: @badlogicgames](https://x.com/badlogicgames)) and the Earendil Works team ([@earendil-works](https://github.com/earendil-works)).

## Included skills

- `safe-start` — create new projects safely with data-first design, project-agent docs, minimal scaffold, validation baseline, and first thin vertical slice.
- `codebase-recon` — reconstruct durable project understanding into `docs/agent/*.md` plus project-root `AGENTS.md`.
- `arch-code-review` — review current diffs against documented architecture, invariants, data model, dependency rules, risks, and tests.
- `safe-change` — preflight, design/diagnosis, implementation, validation, and semantic docs update workflow for safe code changes.

## Usage docs

- [Tutorial](docs/TUTORIAL.md) — end-to-end workflows for small repos, monorepos, scoped reconstruction, safe changes, reviews, consolidation, and legacy docs.
- [Troubleshooting](docs/TROUBLESHOOTING.md) — common reconstruction, scoping, contract, review, and validation issues.

## Included prompt templates

Reconstruction:

- `/recon-all`
- `/recon-01-inventory`
- `/recon-02-architecture`
- `/recon-03-data-invariants`
- `/recon-04-dependency-rules`
- `/recon-05-risk-register`
- `/recon-06-agents`
- `/recon-07-change-guide`
- `/recon-08-consolidate`
- `/recon-09-adr`
- `/recon-10-risk-tests`

Safe-start workflow:

- `/safe-start-all`
- `/safe-start-01-intent`
- `/safe-start-02-data-flow`
- `/safe-start-03-architecture`
- `/safe-start-04-contract-docs`
- `/safe-start-05-scaffold-plan`
- `/safe-start-06-validation`
- `/safe-start-07-vertical-slice`
- `/safe-start-08-handoff`

Safe-change workflow:

- `/preflight`
- `/bug-diagnose`
- `/bug-implement`
- `/feature-design`
- `/feature-implement`
- `/refactor-design`
- `/refactor-implement`
- `/risk-fix`
- `/review-arch`

## Install

From git after repository is published:

```bash
pi install git:github.com/PriNova/pi-agent-codebase-workflows
```

From npm after package is published:

```bash
pi install npm:pi-agent-codebase-workflows
```

Local development/test:

```bash
pi install /absolute/path/to/pi-agent-codebase-workflows
# or one-off
pi -e /absolute/path/to/pi-agent-codebase-workflows
```

## Focus/scoping arguments

Reconstruction prompts accept optional `[focus]` arguments. Use them to scope analysis to a module, package, app, service, directory, or bounded domain area, especially in monorepos.

Example:

```bash
/recon-01-inventory packages/api
/recon-02-architecture apps/mobile auth flow
/recon-all services/billing
```

Without focus, reconstruction writes the traditional top-level `docs/agent/*.md` artifacts. With focus, reconstruction writes hierarchical scoped artifacts and updates `docs/agent/SCOPES.md`:

```text
docs/agent/
  SCOPES.md
  scopes/
    by-path/packages/api/
      README.md      # optional local index for large/complex scopes
      ARCHITECTURE.md
      CONTRACTS.md
    by-domain/auth-flow/
      README.md      # optional local index for large/complex scopes
      ARCHITECTURE.md
      CONTRACTS.md
```

Top-level docs remain valid as repo-level summaries/fallbacks. This is backward-compatible with repositories reconstructed before scoped artifacts existed. Later `/recon-08-consolidate` can reconcile multiple scoped artifacts into repo-level guidance.

Safe-change and review workflows read `SCOPES.md` when present, match path scopes by longest prefix, and follow scoped `CONTRACTS.md` links for cross-module APIs, shared types, schemas, events, generated clients, and persistence boundaries.

Review and risk-fix prompts also accept scope/focus arguments for targeted reviews or fixes.

## Artifact locations

Skills write durable project-agent docs under:

```text
docs/agent/
docs/agent/scopes/**
```

Project operating instructions stay at project root:

```text
AGENTS.md
```

The workflows intentionally avoid `docs/AGENTS.md` and `docs/agent/AGENTS.md`.

## Package structure

```text
skills/
  safe-start/SKILL.md
  codebase-recon/SKILL.md
  arch-code-review/SKILL.md
  safe-change/
    SKILL.md
    references/*.md
prompts/
  *.md
```

Pi discovers these through the `pi.skills` and `pi.prompts` entries in `package.json`.
