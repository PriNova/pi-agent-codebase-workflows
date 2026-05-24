# Tutorial: Structured Agent Artifacts

This package uses agent-first structured YAML artifacts. Legacy prose docs under `docs/agent/*.md` and scoped Markdown docs are deprecated.

Canonical output lives under a resolved structured docs root:

```text
<docs-root>/repo/*.yaml
<docs-root>/scopes/by-path/<repo-relative-path>/*.yaml
<docs-root>/scopes/by-domain/<slug>/*.yaml
```

Resolution rules:
- resolve `workspace_root` with `git rev-parse --show-toplevel 2>/dev/null` or fallback to `pwd`
- `safe-start` creates and uses the initial repo-local root at `<workspace_root>/docs/agent/api`
- other skills use repo-local only when that root already exists
- otherwise use the global overlay root `~/.pi/agent/workspaces/<workspace-fingerprint>/docs/agent/api`

Root `AGENTS.md` is the only Markdown exception. It is kept for coding-harness interoperability and should mirror compact guidance from `<docs-root>/repo/agent-operating-guide.yaml`.

## Greenfield project

Start with intent:

```text
/safe-start-01-intent build a CLI that summarizes logs
```

Then proceed through the safe-start passes:

```text
/safe-start-02-data-flow
/safe-start-03-architecture
/safe-start-04-contract-docs
/safe-start-05-scaffold-plan
/safe-start-06-validation
/safe-start-07-vertical-slice
/safe-start-08-handoff
```

Expected structured artifacts include:

```text
<docs-root>/repo/project-intent.yaml
<docs-root>/repo/repo-inventory.yaml
<docs-root>/repo/data-flow.yaml
<docs-root>/repo/data-model.yaml
<docs-root>/repo/invariants.yaml
<docs-root>/repo/architecture.yaml
<docs-root>/repo/dependency-rules.yaml
<docs-root>/repo/risk-register.yaml
<docs-root>/repo/testing-strategy.yaml
<docs-root>/repo/validation-baseline.yaml
<docs-root>/repo/change-guide.yaml
<docs-root>/repo/agent-operating-guide.yaml
AGENTS.md
```

## Existing codebase reconstruction

For small repos:

```text
/recon-all
```

For larger repos, run bounded passes:

```text
/recon-01-inventory
/recon-02-architecture
/recon-03-data-invariants
/recon-04-dependency-rules
/recon-05-risk-register
/recon-06-agents
/recon-07-change-guide
/recon-08-consolidate
/recon-09-adr
/recon-10-risk-tests
```

Each pass writes only owner YAML artifacts. Example: risk analysis writes `risk-register.yaml`; it references invariants/entities/flows by stable ID instead of repeating their definitions.

## Scoped reconstruction

Use focus arguments for monorepos or bounded domains:

```text
/recon-01-inventory packages/api
/recon-02-architecture packages/api
/recon-05-risk-register auth flow
```

Path focus writes under:

```text
<docs-root>/scopes/by-path/packages/api/
```

Domain focus writes under:

```text
<docs-root>/scopes/by-domain/auth-flow/
```

`<docs-root>/repo/scopes.yaml` is the registry. Path scopes match by longest prefix. Domain scopes require explicit task, domain, or contract evidence.

## Safe changes

Start with preflight:

```text
/preflight packages/api add request validation
```

Then use the matching workflow:

```text
/bug-diagnose <bug>
/bug-implement <approved plan>
/feature-design <feature>
/feature-implement <approved design>
/refactor-design <goal>
/refactor-implement <approved stage>
/risk-fix <risk-id>
```

Safe-change reads `<docs-root>/repo/scopes.yaml`, selects relevant owner YAML artifacts, and updates only canonical owner files when durable semantics change. It uses repo-local docs only when `<workspace_root>/docs/agent/api` already exists; otherwise it uses the global overlay root. It may update root `AGENTS.md` only when `agent-operating-guide.yaml` changes.

## Review

```text
/review-arch packages/api
```

Review is read-only. It checks diffs against structured artifacts: architecture, dependency rules, data model, invariants, contracts, risk register, testing strategy, validation baseline, and scopes.

## Migrating legacy prose docs

```text
/migrate-structured-docs
```

Migration reads legacy Markdown as input only and writes canonical YAML under the resolved structured docs root. It may regenerate compact root `AGENTS.md` from `agent-operating-guide.yaml`. No prose fallback is generated.

## Validation

Validation is best-effort by agent inspection and re-read.
