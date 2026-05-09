# Agentic Architect

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

This repository is the operational implementation workspace for the integrated agentic research system that coordinates:

- **Vibe Science** as rigor, review, provenance, and anti-derailment discipline;
- **VRE** as long-term research memory and wiki-backed evidence store;
- **OBDK** as executable paper-to-evidence kernel using SPARK-derived scripts, recipes, and generated sandboxed analysis code.

The canonical implementation plan source lives at:

`C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\integrated-system-claude-plan`

This repository also tracks a versioned mirror at:

`plan\`

The durable goal file is:

`C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\integrated-system-claude-plan\23_project_goal_and_implementation_doctrine.md`

## First Reads For Any Agent

1. Read this `README.md`.
2. Read `wiki/index.md`.
3. Read `ledger/active_wave.md`.
4. Read `plan\23_project_goal_and_implementation_doctrine.md`.
5. Read the active wave file in `plan\`.
6. Execute the next task exactly as written.

## Current State

Wave 0 preflight is closed after Claude Round 2 ACCEPT and operator `GO Wave 0 closure`.

Active wave:

`A — Foundation Cleanup`

Active wave file:

`plan\09_wave_a_foundation_cleanup.md`

Wave A is closed after Claude final adversarial ACCEPT and Carmine `GO Wave A closure`.

Active wave:

`B — Agent Entrypoints`

Active wave file:

`plan\10_wave_b_agent_entrypoints.md`

Wave B is closed after Claude final adversarial ACCEPT and Carmine `GO Wave B closure`. Codex created OBDK `SKILL.md`, the OBDK wiki seed, the cross-system orchestration map, refreshed the handoff card, ran the entrypoint check and fresh-agent simulation, and pushed the OBDK private provider commit:

`5745de3159062a4d9cf3ffcde2be9fb6436cc602`

Active waves:

`C and D (parallel)`

Active wave files:

- `plan\11_wave_c_obdk_completion.md`
- `plan\12_wave_d_vre_phase10_completion.md`

Wave C started after Carmine `partiamo con wave C`. C1 pending-contract scope reconciliation produced `reports/obdk_contract_completion_scope.md`; Carmine requested formal C1 review before C3 via `OPDEC-WAVE-C-C1-REVIEW-REQUEST`, then selected `(a) + (b)` for the C1 owner-gap finding. C2 paper source record and `ingest-paper` CLI is closed after Claude re-review ACCEPT and operator bookkeeping correction; OBDK private provider commit:

`01e3d6c4a76519f8b294894fb0163fae79372d51`

Wave C C3 method extraction is now author-ready for Claude review. OBDK private provider commit:

`7315da3314c3286e93b98f4f3ed99ac54f158197`

Claude reviewed C3 as `ACCEPT_WITH_MINOR` with no P0/P1/P2 findings and reviewer full pytest `250 passed in 212.95s`. C3 is pending operator closure; C4 has not started. OBDK review bookkeeping commit:

`eb62f01`

Author handoff reports:

`reports/wave_c_c2_author_handoff_report.md`

`reports/wave_c_c3_author_handoff_report.md`

Wave D remains gated by HB-1 and requires explicit operator GO before execution. No Wave D task is authorized by the Wave C GO.

Architecture references:

- `ARCH-REF-001`: OpenClaw-style local automation patterns, reference-only.
- `ARCH-REF-002`: Karpathy LLM Wiki pattern hardening for WIKI_VRE, informed by agentmemory-style retrieval/lifecycle ideas, reference-only. Binding rule: wiki pages are views, not stores; stores win conflicts.

OBDK remoting decision:

- Decision: `OPDEC-OBDK-REMOTING-001`
- Path chosen: Path A, in-place private GitHub mirror
- Local path: `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel`
- Private remote: [th3vib3coder/onco-bio-discovery-kernel](https://github.com/th3vib3coder/onco-bio-discovery-kernel)
- Initial private mirror commit: `44cccf5b520444050eb114b4fecc08f7bcc2250d`
- Current reviewed-head candidate: `7f3c8b54fa961653e6efacaa62df24315101ab19`

This remoting decision did not start Wave A by itself; Wave A later closed cleanly and Wave B later closed after final review.

Claude review status: `INTPLAN-OBDK-REMOTING-CLAUDE-REVIEW-001` ACCEPT, recorded after Carmine `GO commit ACCEPT row`.

## Non-Negotiable Closure Rule

No task is closed until:

1. wiki updated;
2. implementation ledger updated;
3. changelog updated with exact files and reasons;
4. README/start-here updated;
5. GitHub commit and push completed, or an operator-approved no-push waiver is recorded;
6. adversarial review is requested or completed according to the active wave.

## GitHub

Target repository: [th3vib3coder/Agentic_architect](https://github.com/th3vib3coder/Agentic_architect) (public).

Remote:

`https://github.com/th3vib3coder/Agentic_architect.git`

Bootstrap commit:

`1db1a88bfa32ceca7db3fef91feca47c812a9935`

OBDK private repository:

[th3vib3coder/onco-bio-discovery-kernel](https://github.com/th3vib3coder/onco-bio-discovery-kernel)

## Architecture References

Architecture references are recorded in `wiki/architecture_references.md`.

Current references:

- `ARCH-REF-001`: OpenClaw-style local automation patterns are reference-only for a future local cross-agent bridge. No OpenClaw feature is adopted into core scope without an operator decision.
- `ARCH-REF-002`: Karpathy LLM Wiki pattern hardening for WIKI_VRE, informed by agentmemory-style retrieval/lifecycle ideas, is reference-only. Wiki pages are views, not stores.

## Review Status

Claude Code issued `INTPLAN-WAVE0-CLAUDE-REVIEW-002` with verdict `ACCEPT` on the Wave 0 redirect patch. Carmine issued `GO Wave 0 closure`. Wave 0 is closed and Wave A is active but not started.

Claude Code also issued `INTPLAN-OBDK-REMOTING-CLAUDE-REVIEW-001` with verdict `ACCEPT` on OBDK Path A private remoting. Carmine issued `GO commit ACCEPT row`; Codex recorded the ACCEPT without starting Wave A.

Carmine then issued `GO Wave A`. Codex completed A1/A2 and wrote A3/A4 evidence, stopped for operator decisions, resumed after Carmine selected `1: close, 2: authorize`, and handed Wave A to Claude. Claude issued `INTPLAN-WAVE-A-CLAUDE-FINAL-REVIEW-001` with verdict `ACCEPT`; Carmine issued `GO Wave A closure`; Codex recorded the closure and opened Wave B as active_not_started.

Carmine then issued `GO Wave B`. Codex completed the Wave B author-side entrypoint work and requested Claude final adversarial review. Claude issued `INTPLAN-WAVE-B-CLAUDE-FINAL-REVIEW-001`; Carmine issued `GO Wave B closure`; Codex closed Wave B and opened Wave C and Wave D parallel.

Carmine then said `partiamo con wave C`. Codex completed C1 and authored C2. Claude reviewed C2 with `ACCEPT_WITH_MINOR` and raised F1 P2 on untested PDF-bytes fallback. Codex addressed F1 with a persistent PDF fallback test and OBDK private commit `01e3d6c4a76519f8b294894fb0163fae79372d51`. Claude re-reviewed and ACCEPTED C2 after full pytest `245 passed in 198.35s`; Carmine corrected the bookkeeping flow and Codex closed C2. Carmine then requested C1 review before C3 and selected `(a) + (b)` for the owner-gap disposition. Active wave remains `C and D (parallel)` with Wave C ready for C3 operator GO and Wave D HB-1 gated.
