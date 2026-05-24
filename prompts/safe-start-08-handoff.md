---
description: "Structured safe-start pass 8 handoff"
argument-hint: "[focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-start` Pass 8. Verify structured artifacts are ready for `safe-change`; update `change-guide.yaml`, `risk-register.yaml`, `repo-inventory.yaml`, `design-issues.yaml`, and `scopes.yaml` as needed. YAML only. Focus: $ARGUMENTS.
