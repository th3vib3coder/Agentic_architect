# Integrated System Claude Plan — Index
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Single discovery surface for the Claude-authored completion plan. A fresh agent uses this file to identify reading order, current active wave, and which file answers which question.

## File Role Table

| Order | File | Role | Read when |
|---|---|---|---|
| 1 | `README.md` | Scope, goal, non-goal, distribution | Always first |
| 2 | `00_INDEX.md` | This file (reading order + status) | After README |
| 3 | `23_project_goal_and_implementation_doctrine.md` | Durable complete project goal, current state, final system, and implementation doctrine | Immediately after README in any fresh session |
| 4 | `01_canonical_state_audit.md` | What exists in OBDK/VRE/Vibe today; dependencies; experimental quarantine | Before deciding any wave |
| 5 | `02_purpose_anchor.md` | Immutable objective + decision authority stack | When tempted to renegotiate scope |
| 6 | `03_target_architecture.md` | Final state: how 3 subsystems interact + knowledge graph | When designing cross-system bridges |
| 7 | `04_master_sequence.md` | Waves order + dependencies + parallel safety + effort class | When picking next wave |
| 8 | `05_decision_boundaries.md` | Operator vs agent decision matrix + escalation rules | When tempted to escalate or proceed autonomously |
| 9 | `06_multi_agent_pairing.md` | Codex / Claude / operator role per wave | When two agents work in parallel |
| 10 | `07_anti_derailment.md` | Patterns, recovery, tests, purpose anchor reinforcement | When agent feels lost or tempted to shortcut |
| 11 | `08_wave_0_preflight.md` | State verification before any wave; gate to wave A | First execution turn |
| 12 | `09_wave_a_foundation_cleanup.md` | Mark experimental, ledgers, Cluster D v0.1 closure, stale prose | After wave 0 GREEN |
| 13 | `10_wave_b_agent_entrypoints.md` | OBDK SKILL.md, OBDK wiki seed, cross-system map, fresh-agent simulation | After wave A closure |
| 14 | `11_wave_c_obdk_completion.md` | Paper ingest, method extract, script registry, recipes, VRE export | After wave B + parallel-safe with wave D |
| 15 | `12_wave_d_vre_phase10_completion.md` | Phase 10 source/wiki/query/R2 binding (gated on Phase 9 Wave 5 closure) | After wave B + parallel-safe with wave C |
| 16 | `13_wave_e_orchestration.md` | Bridges OBDK↔VRE, OBDK↔Vibe, ledger sync, trace query | After C and D both closed |
| 17 | `14_wave_f_autonomous_runtime.md` | Paper-to-evidence loop + failure scenarios | After E closed |
| 18 | `15_wave_g_validation_handoff.md` | Final validation, absorbability verdict, handoff to VRE | After F closed |
| 19 | `16_atomic_task_backlog.md` | Atomic tasks per wave with verification | When picking next concrete task |
| 20 | `17_test_strategy.md` | Test specs that close each wave; reusable across plan amendments | When implementing or reviewing a wave |
| 21 | `18_recovery_protocol.md` | Multi-system recovery (OBDK + VRE + Vibe) from fresh context or post-derailment | After context loss |
| 22 | `19_operator_decision_register.md` | Single source of truth for decisions awaiting operator | When operator returns |
| 23 | `20_adversarial_review_packet.md` | Packet for Codex review of this plan | Before plan execution and at each wave closure |
| 24 | `21_handoff_card.md` | Post-completion operational guide | After wave G closure |
| 25 | `22_codex_adversarial_review.md` | Codex review round 1 and patch rationale. Subsequent review artifacts use `<number>_<reviewer>_round_<N>.md`; all rounds are also logged in `ledger/adversarial_reviews.md`. | Before handing the revised plan back to Claude |
| 26 | `24_codex_adversarial_review_round_2.md` | Codex patch round 2 responding to Claude ACCEPT_WITH_MINOR and operator goal/mantra correction | Before Claude round 2 counter-review |

## Subsystems And Authoritative Paths

| System | Path | Status (this plan creation) | Authority |
|---|---|---|---|
| OBDK | `vibe-science/blueprints/private/onco-bio-discovery-kernel` | active, 24/39 contracts, smoke-test E2E green, agent surface incomplete | charter v0.5 + analisi_claude/project_plan + this plan via Wave C |
| VRE | `vibe-science/blueprints/private/WIKI_VRE` | active wiki surface, Phase 10 implementation pending | WIKI_VRE/CLAUDE.md + WIKI_VRE/PROTOCOL-wiki-integrated-implementation.md |
| Phase 10 spec | `vibe-science/blueprints/private/phase10-knowledge-layer` | approved-for-preparation-track, awaiting-implementation-track-gate (HB-1: Phase 9 Wave 5 closure + operator approval) | phase10-knowledge-layer/02-formal-design-spec.md |
| Phase 9 plans | `vibe-science/blueprints/private/phase9-implementation-plan` and `phase9-vre-autonomous-research-loop` | Wave 5 split-series in progress (06d-T5.2..T5.7) | Phase 9 documents themselves |
| Vibe Science | repository root + plugin/protocol surfaces | complete enough for rigor layer | Vibe Science SKILL.md and protocol files |
| Agentic Architect workspace | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect` | operational repo; contains wiki, ledgers, reports, README, and versioned mirror at `plan/` | operator immutable fact + OPDEC-WORKSPACE-001 / OPDEC-PLAN-002 |
| Sibling Codex plan | `vibe-science/blueprints/private/integrated-agentic-research-system-plan` | reference-only, not executed per OPDEC-PLAN-003 | Codex plan files |

## Active Wave Pointer

Until ledgers under `Agentic_architect/ledger/` exist, active wave is **Wave 0 — Preflight**.

Once Wave 0 closes, active wave is **Wave A — Foundation Cleanup**.

The active wave pointer is recorded in `Agentic_architect/ledger/active_wave.md` (created during Wave 0). In the GitHub repository, a mirrored copy of this plan lives under `Agentic_architect/plan/`.

## Plan Amendment Rule

This plan is executed, not renegotiated in chat. To amend:

1. write the proposed amendment as a patch to the relevant file in this folder;
2. submit via `20_adversarial_review_packet.md` for Codex review;
3. record verdict in `Agentic_architect/ledger/adversarial_reviews.md`;
4. only operator can authorize execution of an amendment that changes scope, objective, or hard-boundary constraints.
5. complete the orthodox update packet: wiki update, implementation ledger row, incremental changelog row, relevant README update, GitHub commit and push, or an operator-recorded waiver explaining why a specific item is impossible in the current environment.

## Self-Discovery Tests

`17_test_strategy.md` defines tests that prove this plan is discoverable, complete, and free of zone morte. The tests are runnable by any agent and must pass before wave G closure.
