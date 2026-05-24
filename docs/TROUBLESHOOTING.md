# Troubleshooting Structured Agent Artifacts

## No YAML artifacts were written

Expected canonical root:

```text
<docs-root>/repo/
```

Resolve `<docs-root>` by using repo-local `<workspace_root>/docs/agent/api` only when it already exists, except `safe-start`, which creates that initial repo-local root. Otherwise use the global overlay root `~/.pi/agent/workspaces/<workspace-fingerprint>/docs/agent/api`.

If a prompt produced only chat output, check whether it was a design/approval step. Scaffold plans and diagnoses may stop before writing files.

## Markdown docs were created unexpectedly

Legacy project-agent Markdown is deprecated. Workflows should not create `docs/agent/*.md` or scoped Markdown docs. The only Markdown exception is root `AGENTS.md`, used for harness interoperability and generated from `agent-operating-guide.yaml`.

If other Markdown docs were created:
1. Move durable facts into the correct owner YAML artifact.
2. Replace duplicated facts with ID references.
3. Remove or ignore the accidental Markdown artifact.

## Scope went to the wrong place

Path-like focus writes to:

```text
<docs-root>/scopes/by-path/<focus>/
```

Domain-like focus writes to:

```text
<docs-root>/scopes/by-domain/<slug>/
```

Check `<docs-root>/repo/scopes.yaml`:
- path scopes should use longest-prefix matching
- domain scopes should have explicit domain/task/contract evidence
- cross-scope ownership should identify owner and consumer contracts

## Duplicate facts appear across artifacts

Use owner mapping:

- scope routing -> `scopes.yaml`
- command status -> `validation-baseline.yaml`
- entities/schemas -> `data-model.yaml`
- rules -> `invariants.yaml`
- import boundaries -> `dependency-rules.yaml`
- failure modes -> `risk-register.yaml`
- APIs/events/schemas between scopes -> `contracts.yaml`
- test gaps/priorities -> `testing-strategy.yaml`

Non-owner artifacts should reference stable IDs, not repeat definitions.

## IDs changed unexpectedly

Stable IDs should not be regenerated because order, names, or paths changed. Fix by restoring the old ID and updating source-of-truth fields/evidence. New IDs should use deterministic slugs and collision discriminators, not random suffixes.

## Dangling references

If a `*_ref` points nowhere:
1. Add the missing owner record as a compact stub, or
2. Mark the ref external/unknown, or
3. Create a `design-issues.yaml` ownership-gap issue.

## Existing legacy docs need migration

Run:

```text
/migrate-structured-docs
```

Migration reads legacy prose as input, writes YAML under the resolved structured docs root, collapses duplicate facts into owner artifacts, and may regenerate root `AGENTS.md` from `agent-operating-guide.yaml`.

## Validation command fails on legacy docs

Root `AGENTS.md` is allowed. Other `docs/agent/*.md` files indicate incomplete migration or accidental fallback output. Migrate or remove them after confirming facts exist in YAML.

## Artifact status confusion

Use these transitions:

```text
planned -> partial -> current
current -> stale -> current
current|stale|partial -> deprecated
```

`current` needs observed evidence. `partial` means useful but incomplete. `stale` means contradicted or missing source path. `deprecated` means superseded and should include `replacement_ref` when known.
