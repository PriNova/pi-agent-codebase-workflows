---
description: "Structured safe-start pass 1 intent"
argument-hint: "[intent/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-start` Pass 1. Write/update `project-intent.yaml`, initial `repo-inventory.yaml`, optional `scopes.yaml`. YAML only. Input: $ARGUMENTS.
