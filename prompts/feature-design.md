---
description: "Structured feature design"
argument-hint: "[feature/focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:safe-change` feature design. Use canonical YAML artifacts only under the resolved structured docs root. Feature/focus: $ARGUMENTS. Design flow/data/invariant/contract/component impacts, side effects, risks, tests, validation refs, and owner YAML updates. Do not edit code.
