# Troubleshooting

## No docs were created

Check that the prompt used a reconstruction command:

```text
/recon-01-inventory
/recon-02-architecture
/recon-all
```

Reconstruction must not edit production code, but it should write `docs/agent/*.md` or scoped docs under `docs/agent/scopes/**`.

If the repo is large, prefer numbered passes over `/recon-all`.

## Agent wrote scoped findings into top-level docs

Expected behavior:
- no focus argument -> top-level `docs/agent/*.md`
- focus argument -> `docs/agent/scopes/by-path/<focus>/...` or `docs/agent/scopes/by-domain/<slug>/...`

Fix:
1. Move or summarize misplaced details into the correct scoped artifact.
2. Update `docs/agent/SCOPES.md`.
3. Run `/recon-08-consolidate` later if top-level summaries need reconciliation.

## `SCOPES.md` missing or stale

`docs/agent/SCOPES.md` is created when first scoped pass runs. It may not exist in purely unscoped or legacy repos.

If scoped docs exist but `SCOPES.md` is missing:
- create/update `docs/agent/SCOPES.md`
- list each scope, docs path, status, ownership, and external contracts

If stale:
- mark outdated scopes as `stale` or `deprecated`
- update evidence paths and status during next scoped pass or consolidation

## Scope path was renamed

Scoped path docs can become historical after source moves.

Fix:
1. Verify whether the source path still exists.
2. If moved, update `SCOPES.md` with new path and status.
3. Treat old scoped docs as historical until revalidated against source.
4. Re-run relevant scoped pass for the new path.

## Too many scoped directories

Avoid creating a scope for every folder.

Prefer scopes for:
- packages
- apps
- services
- bounded domains
- major modules with separate ownership or contracts

Consolidate or deprecate tiny scopes in `SCOPES.md` when they add noise.

## Agent read too many files

For large repos, provide explicit focus:

```text
/recon-02-architecture packages/api
/preflight fix token refresh in packages/api
/review-arch packages/api
```

Scoped workflows should inspect focused area plus immediate dependencies, tests, entry points, and external boundaries only.

If investigation expands too broadly, stop and narrow target path/domain.

## Cross-scope contract ownership unclear

Use `CONTRACTS.md`.

Rules:
- one owner scope per contract
- owner documents source of truth, compatibility rules, tests, and consumers
- consumers link to owner contract and document local usage/risk only

If ownership cannot be determined, record it as:
- known unknown
- drift risk
- follow-up item for consolidation

## Top-level and scoped docs disagree

Do not silently delete disagreement evidence.

Fix:
1. Check source evidence.
2. Prefer latest verified source-backed observation.
3. Keep scope-specific facts in scoped docs.
4. Summarize stable repo-level guidance in top-level docs.
5. Run `/recon-08-consolidate` to reconcile contradictions.

## Existing legacy docs already exist

Legacy top-level docs remain valid.

Safe-change and review use top-level docs when `SCOPES.md` is absent. First focused recon pass adds scoped docs and `SCOPES.md` without deleting old docs.

Use consolidation when enough scoped material exists to update repo-level summaries.

## Monorepo too large for `/recon-all`

Use numbered/scoped passes instead:

```text
/recon-01-inventory
/recon-02-architecture packages/api
/recon-03-data-invariants packages/api
/recon-02-architecture apps/mobile
```

Keep each pass bounded. Let `/recon-08-consolidate` reconcile later.

## Safe-change ignored scoped docs

Check:
- `docs/agent/SCOPES.md` exists
- target path is listed or covered by longest-prefix scope
- scoped source path still exists
- task wording includes relevant path/domain

Fix by providing explicit target:

```text
/preflight fix billing total rounding in services/billing
```

## Review missed a cross-module contract

Check whether touched API/type/schema/event is documented in scoped `CONTRACTS.md`.

If not:
1. Identify owner scope.
2. Add or update owner `CONTRACTS.md`.
3. Link consumer scope to owner contract.
4. Re-run `/review-arch` with explicit scope if needed.

## Validation command unavailable

Use best available focused validation:
- targeted test for changed package/module
- type check for affected package
- lint for affected package
- build/smoke test for affected app/service

If no validation can run, report why and name the next best command for the user to run.
