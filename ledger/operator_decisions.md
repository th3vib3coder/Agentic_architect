# Operator Decisions

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

| Date | Decision ID | Decision | Rationale | Scope |
|---|---|---|---|---|
| 2026-05-07 | OPDEC-PLAN-001 | Pick Claude `integrated-system-claude-plan` as canonical; use `Agentic_architect` as operational implementation workspace | Operator provided immutable facts naming the plan folder and workspace and said to begin | Integrated system implementation |
| 2026-05-07 | OPDEC-GH-001 | Create public GitHub repository `th3vib3coder/Agentic_architect` | Operator explicitly requested GitHub repo creation and public is acceptable | Wave 0 bootstrap |
| 2026-05-07 | ARCH-REF-001 | Treat OpenClaw-style local automation as reference architecture only, not adopted scope | Operator clarified that useful architecture patterns may be studied later, but features are chosen by this project's narrow orchestrator mission | Future optional local cross-agent bridge |
| 2026-05-07 | OPDEC-WORKSPACE-001 | Bind operational ledgers, reports, wiki, README, and GitHub updates to `Agentic_architect` | Claude REDIRECT found Wave 0 wrote to the operator-declared workspace while the plan still named the plan folder; this records the workspace migration explicitly | Wave 0 and all downstream wave evidence |
| 2026-05-07 | OPDEC-PLAN-002 | Keep the original Claude plan folder as local source and maintain a GitHub-tracked mirror at `Agentic_architect/plan/` | Fresh clones of the public repo must contain the plan together with wiki, ledger, reports, README, and GitHub history | Plan distribution and recovery |
| 2026-05-07 | OPDEC-PLAN-003 | Treat sibling Codex plan `integrated-agentic-research-system-plan` as reference-only, not executed | OPDEC-PLAN-001 selected the Claude plan; Claude REDIRECT required making sibling status explicit to prevent fresh-agent ambiguity | Plan reconciliation |
