---
description: "Structured recon pass 10 risk-to-tests"
argument-hint: "[focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:codebase-recon` Pass 10. Write/update `testing-strategy.yaml` with test topology, coverage gaps, and risk-to-test priorities. YAML only. Focus: $ARGUMENTS.
