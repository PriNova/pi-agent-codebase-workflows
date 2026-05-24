---
description: "Structured bug diagnosis"
argument-hint: "[bug/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` bug diagnosis. Use canonical YAML artifacts only under the resolved structured docs root. Bug/focus: $ARGUMENTS. Diagnose violated invariant/contract/risk refs, root cause, minimal fix, regression test, validation command refs. Do not edit code.
