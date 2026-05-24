---
description: "Structured feature implementation"
argument-hint: "[approved design/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` feature implementation. Follow approved design. Implement minimal change, add tests, validate, update owner YAML artifacts only for durable semantic changes. No legacy Markdown docs except root `AGENTS.md` when `agent-operating-guide.yaml` changes. Design/focus: $ARGUMENTS.
