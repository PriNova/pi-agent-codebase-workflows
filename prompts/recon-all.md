---
description: "Structured codebase reconstruction all passes"
argument-hint: "[focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:codebase-recon` all-in-one mode. Produce canonical YAML artifacts under the resolved structured docs root; root `AGENTS.md` may be generated in Pass 6 for harness interoperability. No other Markdown docs. Focus: $ARGUMENTS. If repo is too large, finish current pass and recommend next pass.
