# Structured Artifact API Runtime Reference

Read this file only when creating/updating structured artifacts or validating artifact shape.

## Schema loading

Before writing any artifact, read this shared schema set only for outputs being written:

- common envelope: `schemas/common.schema.json`
- artifact schema: `schemas/<artifact-file-base>.schema.json`

Examples:
- `risk-register.yaml` -> `schemas/risk-register.schema.json`
- `repo-inventory.yaml` -> `schemas/repo-inventory.schema.json`
- `agent-operating-guide.yaml` -> `schemas/agent-operating-guide.schema.json`

Do not read all schemas. Do not use templates.

## Artifact to schema mapping

- `scopes.yaml` -> `scopes.schema.json`
- `repo-inventory.yaml` -> `repo-inventory.schema.json`
- `project-intent.yaml` -> `project-intent.schema.json`
- `architecture.yaml` -> `architecture.schema.json`
- `data-flow.yaml` -> `data-flow.schema.json`
- `data-model.yaml` -> `data-model.schema.json`
- `invariants.yaml` -> `invariants.schema.json`
- `dependency-rules.yaml` -> `dependency-rules.schema.json`
- `design-issues.yaml` -> `design-issues.schema.json`
- `risk-register.yaml` -> `risk-register.schema.json`
- `change-guide.yaml` -> `change-guide.schema.json`
- `testing-strategy.yaml` -> `testing-strategy.schema.json`
- `validation-baseline.yaml` -> `validation-baseline.schema.json`
- `contracts.yaml` -> `contracts.schema.json`
- `adr.yaml` -> `adr.schema.json`
- `agent-operating-guide.yaml` -> `agent-operating-guide.schema.json`

## Runtime rule

Schemas are contracts. Skills/prompts describe behavior. Project docs outside these shared runtime refs are maintainer aids and are not runtime instructions unless user explicitly asks about this package itself.
