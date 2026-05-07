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
| `architecture_references.md` | External architecture references and explicit non-adoption boundaries |
| `implementation_log.md` | Narrative companion to ledger rows |

## Active Wave

Current active wave is recorded in `ledger/active_wave.md`.

As of 2026-05-07, Wave 0 is closed and Wave A is active but not started. The active wave file is `plan\09_wave_a_foundation_cleanup.md`.

## Review Status

Wave 0 has Claude Round 2 ACCEPT recorded in `ledger/adversarial_reviews.md` and operator closure recorded in `ledger/change_log.md`. The next review checkpoint is Wave A after its own scoped work, not before reading the active wave file.

OBDK Path A private remoting is implemented and awaiting Claude review. Evidence is in `reports/obdk_private_mirror_report.md`.

## No Dead Zones Rule

Every new implementation surface must be linked from this wiki or a subsystem wiki before the related task is closed.
