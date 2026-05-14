---
description: "Run all codebase reconstruction passes when repo size and complexity allow"
---
Use the `codebase-recon` skill in all-in-one mode.

First assess whether the repository is small/simple enough for reliable sequential reconstruction. If yes, run passes 1–10, writing artifacts under `docs/agent/` and keeping `AGENTS.md` at project root.

If the repo proves too large or complex, complete the current pass and tell the user which numbered pass to run next.
