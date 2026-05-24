---
description: "Structured refactor design"
argument-hint: "[refactor/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` refactoring design. Use canonical YAML artifacts only. Identify design issue/dependency rule refs, behavior to preserve, characterization tests, staged plan, validation refs, rollback. Do not edit code. Focus: $ARGUMENTS.
