# pi-agent-codebase-workflows

Pi package with skills and prompt templates for documented-codebase workflows.

## Included skills

- `codebase-recon` — reconstruct durable project understanding into `docs/agent/*.md` plus project-root `AGENTS.md`.
- `arch-code-review` — review current diffs against documented architecture, invariants, data model, dependency rules, risks, and tests.
- `safe-change` — preflight, design/diagnosis, implementation, validation, and semantic docs update workflow for safe code changes.

## Included prompt templates

Reconstruction:

- `/recon-all`
- `/recon-01-inventory`
- `/recon-02-architecture`
- `/recon-03-data-invariants`
- `/recon-04-dependency-rules`
- `/recon-05-risk-register`
- `/recon-06-agents`
- `/recon-07-change-guide`
- `/recon-08-consolidate`
- `/recon-09-adr`
- `/recon-10-risk-tests`

Safe-change workflow:

- `/preflight`
- `/bug-diagnose`
- `/bug-implement`
- `/feature-design`
- `/feature-implement`
- `/refactor-design`
- `/refactor-implement`
- `/risk-fix`
- `/review-arch`

## Install

From git after repository is published:

```bash
pi install git:github.com/PriNova/pi-agent-codebase-workflows
```

From npm after package is published:

```bash
pi install npm:pi-agent-codebase-workflows
```

Local development/test:

```bash
pi install /absolute/path/to/pi-agent-codebase-workflows
# or one-off
pi -e /absolute/path/to/pi-agent-codebase-workflows
```

## Artifact locations

Skills write durable project-agent docs under:

```text
docs/agent/
```

Project operating instructions stay at project root:

```text
AGENTS.md
```

The workflows intentionally avoid `docs/AGENTS.md` and `docs/agent/AGENTS.md`.

## Package structure

```text
skills/
  codebase-recon/SKILL.md
  arch-code-review/SKILL.md
  safe-change/SKILL.md
prompts/
  *.md
```

Pi discovers these through the `pi.skills` and `pi.prompts` entries in `package.json`.
