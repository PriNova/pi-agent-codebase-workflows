---
description: "Structured safe-start all passes"
argument-hint: "[project intent/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-start` all-in-one mode. Create canonical YAML artifacts under the resolved structured docs root and root `AGENTS.md` for harness interoperability. Do not create README or other prose docs as workflow artifacts. Stop for approval gates unless implementation explicitly requested. Input: $ARGUMENTS.
