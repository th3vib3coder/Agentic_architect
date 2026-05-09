# Agentic Architect Wiki

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

This wiki is the durable map of the integrated system implementation. It exists so future agents do not need forensic audits or chat history to understand the project.

## Source Of Truth

| Surface | Path | Role |
|---|---|---|
| Operational workspace | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect` | Repo where implementation orchestration artifacts live |
| Canonical plan | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\integrated-system-claude-plan` | Execution plan to follow word-for-word |
| Versioned plan mirror | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect\plan` | GitHub-tracked mirror of the canonical plan for fresh clones |
| GOAL doctrine | `...\integrated-system-claude-plan\23_project_goal_and_implementation_doctrine.md` | Complete project objective and implementation doctrine |
| OBDK | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel` | Analysis kernel |
| OBDK private remote | `https://github.com/th3vib3coder/onco-bio-discovery-kernel` | Private GitHub mirror selected by `OPDEC-OBDK-REMOTING-001`; OBDK remains in place locally |
| VRE wiki | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\WIKI_VRE` | Long-term memory surface |
| GitHub remote | `https://github.com/th3vib3coder/Agentic_architect` | Public remote for reviewed/pushed implementation state |

## Wiki Map

| Page | Role |
|---|---|
| `project_goal.md` | Human-readable goal and completion criteria |
| `system_map.md` | Where the three subsystems live and how agents should navigate |
| `architecture_references.md` | External architecture references and explicit non-adoption boundaries, including ARCH-REF-002 WIKI_VRE store/view hardening |
| `implementation_log.md` | Narrative companion to ledger rows |

## Active Wave

Current active wave is recorded in `ledger/active_wave.md`.

As of 2026-05-09, Wave B is closed and Carmine has authorized Wave C. The active wave pointer remains `C and D (parallel)`:

- Wave C: `plan\11_wave_c_obdk_completion.md`, C1 report ready at `reports/obdk_contract_completion_scope.md`; C2 paper-source intake plus F1 PDF fallback fix is author-ready at `reports/wave_c_c2_author_handoff_report.md`.
- Wave D: `plan\12_wave_d_vre_phase10_completion.md`, blocked by HB-1 and explicit operator GO.

## Review Status

Wave B author-side evidence is recorded in:

- `reports/wave_b_entrypoint_check.md`
- `reports/wave_b_fresh_agent_simulation.md`
- `reports/wave_b_author_handoff_report.md`

OBDK Path A private remoting is closed. The latest OBDK provider commit for Wave B entrypoints is `5745de3159062a4d9cf3ffcde2be9fb6436cc602`. Wave B final review is recorded as `INTPLAN-WAVE-B-CLAUDE-FINAL-REVIEW-001`.

ARCH-REF-002 is reference-only. It records Karpathy LLM Wiki / agentmemory-style ideas for WIKI_VRE hardening with the binding rule that wiki pages are views, not stores.

Wave C C1 evidence is recorded in `reports/obdk_contract_completion_scope.md`.

Wave C C2 evidence is recorded in `reports/wave_c_c2_author_handoff_report.md`. Initial C2 provider commit was `ceb429153780d6ff53bf17db41efc1eb5f95f32c`; the Claude F1 PDF fallback fix is OBDK private commit `01e3d6c4a76519f8b294894fb0163fae79372d51`.

## No Dead Zones Rule

Every new implementation surface must be linked from this wiki or a subsystem wiki before the related task is closed.
