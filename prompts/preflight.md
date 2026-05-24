---
description: "Structured safe-change preflight"
argument-hint: "[task/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` structured preflight. Read only canonical YAML artifacts under the resolved structured docs root; do not read legacy prose docs. Focus/task: $ARGUMENTS. Output classification, artifacts read, matched scope, affected files, invariant/contract/risk refs, validation command refs, and approval status.
