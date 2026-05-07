# Atomic Task Backlog
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Single-page reference of every atomic task across waves with verification command. A worker takes one row, completes it, verifies, records evidence, then takes the next.

## Rules

- One task at a time. Mark `in_progress` in `ledger/active_subtasks.md` before starting.
- After completion, mark `completed` and append evidence to `ledger/change_log.md`.
- If blocked, mark `blocked` and write a row to `19_operator_decision_register.md`.
- Every task includes the universal orthodox epilogue below. The epilogue is mandatory even when the task table does not repeat it.
- The task backlog follows the mantra: **il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

## Universal Orthodox Task Epilogue

After the task-specific output and verification pass, the worker completes these five evidence steps before taking another task:

1. **Wiki:** update the project wiki page that explains the changed surface. If the correct wiki page does not exist, create it in the active subsystem wiki or record why Wave 0/active wave must create it first.
2. **Ledger:** append the implementation ledger row with task id, agent, files changed, verification command, and review state.
3. **Changelog:** append the incremental changelog row naming every edited file and why it changed.
4. **README:** update the relevant README or start-here card so a fresh agent sees the new behavior without chat context.
5. **GitHub:** after adversarial review closure, commit and push the change to GitHub, or record an operator-approved no-push waiver.

No task can be marked `completed` without the five epilogue items or a recorded blocker.

**Vibe Science cross-cutting changes:** when a task modifies code that integrates with Vibe Science without modifying Vibe Science core, the ledger row goes in the active subsystem's ledger, usually OBDK `analisi_claude/project_plan/ledger/`, plus this plan's `ledger/change_log.md`. If a task modifies Vibe Science core, stop and request an operator decision for the ledger/wiki location before writing.

## Wave 0 (Preflight)

| ID | Task | Output | Verification |
|---|---|---|---|
| P0.1 | Create ledger directory + 7 seed files | `ledger/active_wave.md`, `change_log.md`, `operator_decisions.md`, `adversarial_reviews.md`, `derailment_log.md`, `multi_agent_pairing.md`, `active_subtasks.md` | all 7 files exist with correct headers |
| P0.2 | Verify subsystem paths | `reports/wave_0_preflight_report.md` | 12 paths checked; missing logged |
| P0.3 | Capture Phase 9 Wave 5 status | report section "Phase 9 Wave 5 status" | reading `phase9-implementation-plan/00-index.md` reflects in report |
| P0.4 | Run baseline validations | report section "Baseline validations" | exit codes recorded for pytest, ruff, obdk validate, node check |
| P0.5 | Append change_log row | row INTPLAN-PRE-001 | row visible |
| P0.6 | Wave 0 closure | `ledger/active_wave.md` updated to A | pointer file shows wave A |

## Wave A (Foundation Cleanup)

| ID | Task | Output | Verification |
|---|---|---|---|
| A1 | Mark experimental directory-level | `OVERSHOOT_STATUS.md` | file exists; references active plan |
| A2 | Mark experimental file-level | 28 files headed | all 28 files start with EXPERIMENTAL header |
| A3 | Cluster D v0.1 closure resolution | `reports/wave_a_cluster_d_status.md` | operator decision row OR explicit deferral row |
| A4 | Stale prose sweep | `reports/wave_a_stale_prose_sweep.md` | findings + dispositions documented |
| A5 | Verification | OBDK plan-pack + contracts + ruff outputs | exit codes recorded |
| A6 | Append change_log row + update active wave | row INTPLAN-A-001 + `active_wave: B` | both visible |

## Wave B (Agent Entrypoints)

| ID | Task | Output | Verification |
|---|---|---|---|
| B1 | OBDK SKILL.md | `vibe-science/blueprints/private/onco-bio-discovery-kernel/SKILL.md` | all required sections present |
| B2 | Cross-system map | `system_orchestration_map.md` in this plan folder | diagram + tables + ID rules |
| B3 | Agent start-here card finalize | `14_agent_start_here_card.md` | first 10 moves listed |
| B4 | Entrypoint presence checks | OBDK test OR PowerShell/POSIX recipe | all paths verified True |
| B5 | Fresh-agent simulation | `reports/wave_b_fresh_agent_simulation.md` | simulation passes without operator hints |
| B6 | Create OBDK wiki seed | `onco-bio-discovery-kernel/wiki/index.md` + seed pages | wiki pages exist and link SKILL.md, contracts, recipes, scripts, runs |
| B7 | Append change_log row + update active wave | row INTPLAN-B-001 + `active_wave: C and D parallel` | both visible |

## Wave C (OBDK Completion)

| ID | Task | Output | Verification |
|---|---|---|---|
| C1 | Pending contract scope reconciliation | `reports/obdk_contract_completion_scope.md` | all 15 pending classified |
| C2 | Paper source bundle contract + CLI | `contracts/paper-source-record-v0.1.md` + `obdk/paper_ingest.py` + tests | contract validates; CLI ingests fixture |
| C3 | Method extraction record + CLI | `contracts/method-extraction-record-v0.1.md` + `obdk/method_extraction.py` + tests | contract validates; CLI extracts fixture methods |
| C4 | Script registry | `obdk/script_registry.py` + `registry/scripts/*.yaml` (5+ entries) + tests | lookup tests pass |
| C5 | Sandbox generation runtime | `obdk/sandbox_runtime.py` + CLI + tests | missing-script generation creates artifact |
| C6 | Recipe library expansion (3 must-have) | 3 new recipes + tests | each runs end-to-end on smoke fixture |
| C7 | OBDK to VRE export adapter | `obdk/export_vre.py` + tests | smoke export to VRE staging works |
| C8 | OBDK absorbability pre-gate report | `reports/obdk_absorbability_pregate.md` | all C deliverables linked with evidence |
| C9 | Append change_log row + update active wave | row INTPLAN-C-001 + active wave update | visible |

## Wave D (VRE Phase 10 Completion)

| ID | Task | Output | Verification |
|---|---|---|---|
| D1 | Phase 10 implementation gate | `reports/wave_d_phase9_dependency.md` + operator decision row | HB-1 satisfied or paused |
| D2 | Source bundle store | Phase 10 source layer | LAW 13 fail-closed verified |
| D3 | Wiki compile pipeline | Phase 10 compile layer | `wiki-lint --json` exits 0 |
| D4 | Query agent | Phase 10 query layer | citations returned; no-source returns insufficient-evidence |
| D5 | R2 audit binding | Phase 10 R2 binding | unauthorized claimed synthesis blocked |
| D6 | Operator steering | Phase 10 steering layer | objective mutation creates escalation/supersession |
| D7 | Serendipity preservation | Phase 10 seed layer | seed survives wiki sync |
| D8 | Completion report | `reports/vre_phase10_completion_report.md` | all D tasks referenced |
| D9 | Append change_log row + update active wave | row INTPLAN-D-001 + active wave update | visible |

## Wave E (Orchestration And Memory)

| ID | Task | Output | Verification |
|---|---|---|---|
| E1 | Cross-system IDs | section in `system_orchestration_map.md` | all 7 IDs defined |
| E2 | OBDK run to VRE page | `obdk/orchestration_vre_export.py` + tests | computed page created |
| E3 | Vibe review packet adapter | `obdk/orchestration_vibe_review.py` + tests | packet validates |
| E4 | Review result persistence | persistence flow + tests | ACCEPT/REDIRECT/VETO update both surfaces |
| E5 | Active objective resolver | `obdk/orchestration_objective.py` + tests | single/none/multiple objectives handled |
| E6 | End-to-end trace query | trace query + tests | full chain returned |
| E7 | Orchestration report | `reports/wave_e_orchestration_report.md` | all E deliverables linked |
| E8 | Append change_log row + update active wave | row INTPLAN-E-001 + active wave update | visible |

## Wave F (Autonomous Runtime)

| ID | Task | Output | Verification |
|---|---|---|---|
| F1 | Autonomy policy | `reports/wave_f_autonomy_policy.md` | all thresholds documented |
| F2 | Paper-to-procedure scenario | `reports/wave_f_scenario_paper_to_procedure.md` | source page + method records + script decisions |
| F3 | Existing-script execution scenario | `reports/wave_f_scenario_existing_script.md` | run + evidence + VRE page + R2 review |
| F4 | Missing-script generation scenario | `reports/wave_f_scenario_missing_script.md` | sandbox script + test + registration + review status |
| F5 | Failure scenarios | `reports/wave_f_scenario_failure.md` | 5 failure modes verified fail-closed |
| F6 | Autonomous runtime summary | `reports/autonomous_runtime_report.md` | all F deliverables linked |
| F7 | Append change_log row + update active wave | row INTPLAN-F-001 + active wave update | visible |

## Wave G (Validation, Absorption, Handoff)

| ID | Task | Output | Verification |
|---|---|---|---|
| G1 | Full validation run | `reports/final_validation.md` | all commands recorded with exit codes |
| G2 | Fresh-agent drill | `reports/wave_g_fresh_agent_drill.md` | agent succeeds without operator hints |
| G3 | Absorbability verdict | `reports/absorbability_verdict.md` | verdict from allowed set |
| G4 | Handoff card finalize | `21_handoff_card.md` | usable by fresh agent |
| G5 | Adversarial review final | review packet record in `ledger/adversarial_reviews.md` | ACCEPT or findings patched |
| G6 | Operator closure | row in `ledger/operator_decisions.md` | closure recorded |
| G7 | Plan archive/reconciliation | reconciliation report or archive directory | one canonical plan remains |
| G8 | Final change_log row | row INTPLAN-G-001 + `active_wave: closed` | visible |

## Total task count

- Wave 0: 6 tasks
- Wave A: 6 tasks
- Wave B: 7 tasks
- Wave C: 9 tasks
- Wave D: 9 tasks
- Wave E: 8 tasks
- Wave F: 7 tasks
- Wave G: 8 tasks

Total: 60 atomic tasks across 8 waves (including preflight).
