# Structured Preflight

Read `<docs-root>/repo/scopes.yaml` if present, match scope, then read only relevant owner YAML artifacts under the resolved structured docs root. Do not read legacy prose docs. Use repo-local docs only when `<workspace_root>/docs/agent/api` already exists; otherwise use the global overlay root. Produce classification, artifacts read, scope, affected files, invariant/contract/risk refs, validation command refs, and approval status.
