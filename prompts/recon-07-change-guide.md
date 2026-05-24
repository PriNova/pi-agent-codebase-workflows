---
description: "Structured recon pass 7 change guide"
argument-hint: "[focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:codebase-recon` Pass 7. Write/update `change-guide.yaml` with routing/checklists and owner artifact refs. YAML only; no Markdown. Focus: $ARGUMENTS.
