---
description: "Structured recon pass 6 agent operating guide"
argument-hint: "[focus]"
---
Before writing/updating structured artifacts, after loading the selected skill, load shared refs relative to that skill: `../_shared/references/artifact-api.md`, `../_shared/references/schemas/common.schema.json`, and only the matching artifact schema(s). Follow the skill Structured Artifact Write/Update Protocol for scope resolution, stable IDs, upserts, evidence, reference integrity, status transitions, deterministic YAML formatting, and validation. Use `/skill:codebase-recon` Pass 6. Write/update `agent-operating-guide.yaml` and root `AGENTS.md` for harness interoperability. Canonical facts remain in YAML; `AGENTS.md` stays compact and references canonical YAML. Focus: $ARGUMENTS.
