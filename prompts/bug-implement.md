---
description: "Structured bug implementation"
argument-hint: "[approved plan/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` bug implementation. Follow approved plan. Use/update canonical YAML artifacts only under the resolved structured docs root when durable semantics changed. No legacy prose docs. Plan/focus: $ARGUMENTS.
