---
description: "Migrate legacy prose docs to structured YAML"
argument-hint: "[focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:structured-docs-migration`. Convert deprecated prose-style docs into canonical YAML under the resolved structured docs root. Do not generate Markdown fallback artifacts; root `AGENTS.md` is allowed for harness interoperability when explicitly produced. Focus: $ARGUMENTS.
