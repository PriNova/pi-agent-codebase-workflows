# pi-agent-codebase-workflows

Pi package with agent-first skills and prompt templates for structured codebase understanding, safe greenfield starts, safe changes, architecture-aware review, structured-doc validation, and migration from deprecated prose docs.

## Structured artifact model

Legacy prose-style project-agent docs are deprecated. Current workflows treat `docs/agent/api` as a logical layout under a resolved structured docs root:

```text
<docs-root>/repo/*.yaml
<docs-root>/scopes/by-path/<repo-relative-path>/*.yaml
<docs-root>/scopes/by-domain/<slug>/*.yaml
```

Resolution rules:
- resolve `workspace_root` with `git rev-parse --show-toplevel 2>/dev/null` or fallback to `pwd`
- canonicalize `workspace_root` before fingerprinting when possible (`realpath`, `pwd -P`, `Path(...).resolve()`, or equivalent)
- `safe-start` creates and uses the initial repo-local root at `<workspace_root>/docs/agent/api`
- other skills use repo-local only when that root already exists
- otherwise use the global overlay root `~/.pi/agent/workspaces/<workspace-fingerprint>/docs/agent/api`
- compute `<workspace-fingerprint>` exactly from canonical `workspace_root`: strip one leading slash/backslash, replace every slash, backslash, and colon with `-`, then wrap with `--`
- example: `/data/data/com.termux/files/home/CodeProjects/pi-mono` -> `--data-data-com.termux-files-home-CodeProjects-pi-mono--`

No workflow generates `docs/agent/*.md`, scoped Markdown docs, or README files as project-agent artifacts. Structured YAML is the API for further transformation and agent ingestion. Root `AGENTS.md` remains a compact harness interoperability file generated from `agent-operating-guide.yaml`, because not every coding harness consumes these skills/prompts directly.

All skills follow a Structured Artifact Write/Update Protocol: resolve scope and owner artifact first, read before write, preserve stable IDs, upsert by ID/source-of-truth fields, mark unsupported records stale/deprecated instead of deleting, require evidence, validate references, format YAML deterministically, and report validation.

## Included skills

- `safe-start` — create new projects with structured intent, prioritized quality attributes, data, architecture, contracts, validation, and handoff artifacts.
- `codebase-recon` — reconstruct existing codebases into structured YAML artifacts under the resolved structured docs root, including inferred intent/quality/risk context when evidence exists.
- `safe-change` — make documented-codebase changes using structured artifacts and update owner YAML only when durable semantics change, treating schema gaps in older artifacts as blockers or repair work when needed.
- `arch-code-review` — review diffs against structured architecture, data, invariant, dependency, risk, contract, and test artifacts from the resolved structured docs root.
- `structured-doc-validate` — validate structured YAML docs for schema shape, shared schema coverage, reference integrity, evidence quality, coverage, and granularity.
- `structured-docs-migration` — migrate deprecated prose-style docs into canonical structured YAML artifacts under the resolved structured docs root.

## Included prompt templates

Reconstruction:

- `/recon-all`
- `/recon-01-inventory`
- `/recon-02-architecture`
- `/recon-03-data-invariants`
- `/recon-04-dependency-rules`
- `/recon-05-risk-register`
- `/recon-06-agents` — writes `agent-operating-guide.yaml` and root `AGENTS.md`
- `/recon-07-change-guide`
- `/recon-08-consolidate`
- `/recon-09-adr`
- `/recon-10-risk-tests`

Safe start:

- `/safe-start-all`
- `/safe-start-01-intent`
- `/safe-start-02-data-flow`
- `/safe-start-03-architecture`
- `/safe-start-04-contract-docs`
- `/safe-start-05-scaffold-plan`
- `/safe-start-06-validation`
- `/safe-start-07-vertical-slice`
- `/safe-start-08-handoff`

Safe change / review / validation / migration:

- `/preflight`
- `/bug-diagnose`
- `/bug-implement`
- `/feature-design`
- `/feature-implement`
- `/refactor-design`
- `/refactor-implement`
- `/risk-fix`
- `/review-arch`
- `/validate-structured-docs`
- `/migrate-structured-docs`

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

## Scope/focus arguments

Prompts accept optional focus/scope arguments. Path-like focus writes under:

```text
<docs-root>/scopes/by-path/<focus>/
```

Domain-like focus writes under:

```text
<docs-root>/scopes/by-domain/<slug>/
```

`<docs-root>/repo/scopes.yaml` is the canonical scope registry. Path scopes match by longest prefix. Domain scopes require explicit task/domain/contract refs.

## Artifact ownership

- `scopes.yaml`: scope routing and ownership.
- `repo-inventory.yaml`: structure, entry points, command index, boundaries.
- `validation-baseline.yaml`: command status, blockers, validation order.
- `project-intent.yaml`: goals, users, journeys, constraints, prioritized quality attributes, operating constraints.
- `architecture.yaml`: components, style, style rationale, alternatives, side-effect boundaries, reliability/observability/security expectations.
- `data-flow.yaml`: typed flow graph, trust boundaries, sensitive-data handling, error states.
- `data-model.yaml`: entities, IDs, schemas, lifecycles, serialized formats, retention/compliance notes.
- `invariants.yaml`: rules, forbidden states, enforcement.
- `dependency-rules.yaml`: layers, allowed/forbidden dependencies, violations.
- `design-issues.yaml`: drift, deferred decisions, ownership gaps.
- `risk-register.yaml`: failure modes, affected refs, recommended actions, and suggested tests/fixes.
- `contracts.yaml`: APIs, schemas, events, generated clients, persistence/deployment/env/auth/telemetry contracts.
- `testing-strategy.yaml`: test topology, quality-attribute coverage, gaps, risk-to-test priorities.
- `change-guide.yaml`: workflow routing and checklists.
- `adr.yaml`: structured ADR records.
- `agent-operating-guide.yaml`: structured operational rules for agents; root `AGENTS.md` mirrors compact harness-facing guidance.

## Runtime schemas and validation

Runtime schema assets are shared under `skills/_shared/references/`. Skills load `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and the matching artifact schema(s) for files they write. `_shared` has no `SKILL.md`, so Pi does not discover it as a skill.

Project docs outside the shared runtime refs may exist in the source repo, but are not runtime instructions for installed extension users.

Validation is best-effort by agent inspection and re-read. The `structured-doc-validate` skill gives a read-only four-layer audit workflow for schema validity, shared schema coverage, references, evidence, coverage, and granularity. Shared schemas are user-facing contracts too, so older artifacts missing newly required fields should fail validation until repaired or migrated.

## Package structure

```text
skills/
  _shared/references/artifact-api.md
  _shared/references/schemas/*.schema.json
  */SKILL.md
prompts/
  *.md
```

Pi discovers skills and prompts through the `pi.skills` and `pi.prompts` entries in `package.json`.
