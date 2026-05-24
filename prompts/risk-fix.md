---
description: "Structured risk fix"
argument-hint: "[risk/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` risk-fix workflow. Select one risk from `<docs-root>/**/risk-register.yaml` or a failing risk-derived test. Fix minimally, validate, update risk/testing YAML refs. No legacy prose docs. Risk/focus: $ARGUMENTS.
