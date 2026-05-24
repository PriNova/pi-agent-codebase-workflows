---
description: "Structured refactor implementation"
argument-hint: "[approved refactor/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` refactoring implementation. Preserve behavior. Follow approved stage. Update owner YAML only when durable structure/rules changed. No legacy Markdown docs except root `AGENTS.md` when `agent-operating-guide.yaml` changes. Focus: $ARGUMENTS.
