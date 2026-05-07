# Test Strategy
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Define test specs that close each wave and prove the integrated system is wired, recoverable, and free of zone morte. Tests are runnable by any agent and re-runnable at any time; they do not depend on chat context.

## Test Categories

| Category | Purpose | Where it lives |
|---|---|---|
| Plan-integrity tests | Verify plan files exist, are indexed, contain required sections, no zone morte | this plan folder + repository scripts |
| Subsystem tests | Verify OBDK / VRE / Phase 10 / Vibe Science work as expected | each subsystem's own test directory |
| Cross-system tests | Verify orchestration adapters, trace query, ledger sync | OBDK tests + WIKI_VRE tools |
| Anti-derailment tests | Verify purpose anchor, derailment patterns, recovery protocol surfaces are present and discoverable | this plan folder |
| Fresh-agent tests | Simulate fresh agent flow without chat context | recipe + report |

## Wave 0 Tests

- **P0.T1 (plan-integrity)**: All 26 plan files listed in `00_INDEX.md` exist on disk.
- **P0.T2 (plan-integrity)**: Each plan file has a header line summarizing its role.
- **P0.T3 (plan-integrity)**: No file in plan folder is missing from `00_INDEX.md` (dynamic check).
- **P0.T4 (subsystem)**: OBDK plan-pack guardrail passes (`pytest tests/test_project_plan_pack.py`).
- **P0.T5 (subsystem)**: OBDK contracts validate (`obdk.cli contracts validate`).
- **P0.T6 (subsystem)**: WIKI_VRE registry check passes OR fallback recorded.

Closure: all P0.T tests pass or operator-accepted deviation.

## Wave A Tests

- **A.T1 (plan-integrity)**: `OVERSHOOT_STATUS.md` exists in OBDK `.vibe-science/`.
- **A.T2 (plan-integrity)**: Every file under OBDK `.vibe-science/RQ-001-d0-first-cycle/` starts with EXPERIMENTAL header (regex check).
- **A.T3 (plan-integrity)**: Cluster D v0.1 status documented in `reports/wave_a_cluster_d_status.md`.
- **A.T4 (plan-integrity)**: Stale prose sweep report exists.
- **A.T5 (subsystem)**: OBDK contracts validate count unchanged from preflight (24 contracts preserved).

## Wave B Tests

- **B.T1 (plan-integrity)**: OBDK `SKILL.md` exists.
- **B.T2 (plan-integrity)**: `SKILL.md` contains required sections (Purpose, When to invoke, When NOT to invoke, Commands, Output interpretation, Escalation rules).
- **B.T3 (plan-integrity)**: `system_orchestration_map.md` exists with diagram + decision table + failure fallback table + ID rules.
- **B.T4 (plan-integrity)**: `14_agent_start_here_card.md` first 10 moves are concrete (each move references an actual file or command).
- **B.T5 (fresh-agent)**: Fresh-agent simulation in `reports/wave_b_fresh_agent_simulation.md` shows agent identifies all required surfaces without operator hints.
- **B.T6 (plan-integrity)**: OBDK wiki seed exists at `onco-bio-discovery-kernel/wiki/index.md` and links contracts, recipes, scripts, runs, OBDK `SKILL.md`, and this integrated plan.

## Wave C Tests

- **C.T1 (subsystem)**: OBDK `pytest --tb=short -q` shows N+ tests passed where N is the count from preflight (no regressions).
- **C.T2 (subsystem)**: OBDK contracts validate shows 24+2 = 26 contracts (paper-source-record + method-extraction-record).
- **C.T3 (subsystem)**: `obdk ingest-paper` runs on a fixture PDF and produces valid `paper_source_record.yaml`.
- **C.T4 (subsystem)**: `obdk extract-methods` runs on the ingested source and produces method records.
- **C.T5 (subsystem)**: Script registry has 5+ entries; lookup test passes for each must-have recipe.
- **C.T6 (subsystem)**: 3 must-have recipes run end-to-end on smoke fixtures.
- **C.T7 (subsystem)**: `obdk export-vre` writes a valid computed page to staging or VRE.
- **C.T8 (plan-integrity)**: `reports/obdk_absorbability_pregate.md` exists and references all C deliverables.

## Wave D Tests

- **D.T1 (subsystem)**: Phase 10 source bundle missing-provenance test fails closed.
- **D.T2 (subsystem)**: Phase 10 wiki compile produces valid pages; missing-provenance page fails closed.
- **D.T3 (subsystem)**: Phase 10 query agent returns citation list; no-source returns insufficient-evidence.
- **D.T4 (subsystem)**: Phase 10 R2 binding blocks unauthorized claimed synthesis.
- **D.T5 (subsystem)**: Phase 10 operator steering creates escalation/supersession (not silent edit).
- **D.T6 (subsystem)**: Phase 10 serendipity seed survives wiki sync.
- **D.T7 (plan-integrity)**: `reports/vre_phase10_completion_report.md` exists.

## Wave E Tests

- **E.T1 (cross-system)**: `system_orchestration_map.md` defines all 7 IDs.
- **E.T2 (cross-system)**: OBDK run E2E on smoke recipe creates VRE computed page with backlinks to source/method/script/run/evidence.
- **E.T3 (cross-system)**: Review packet adapter produces packet with all required fields.
- **E.T4 (cross-system)**: ACCEPT updates VRE page status to `validated`; REDIRECT keeps `computed`; VETO downgrades to `archived`.
- **E.T5 (cross-system)**: Active objective resolver returns single/none/multiple correctly.
- **E.T6 (cross-system)**: End-to-end trace query returns all linked artifacts for a known evidence package.
- **E.T7 (plan-integrity)**: `reports/wave_e_orchestration_report.md` exists.

## Wave F Tests

- **F.T1 (cross-system)**: Paper-to-procedure scenario completes without operator hints; produces source page, method records, mapped scripts.
- **F.T2 (cross-system)**: Existing-script scenario completes; produces run + evidence + VRE page + R2 review record.
- **F.T3 (cross-system)**: Missing-script scenario produces sandbox script with test, registration, `generated_pending_review` status; no claim promotion.
- **F.T4 (cross-system)**: Failure scenarios (5 modes) all fail closed with explicit error and escalation.
- **F.T5 (anti-derailment)**: No derailment patterns observed in autonomous runs (manual review of run logs).
- **F.T6 (plan-integrity)**: `reports/autonomous_runtime_report.md` exists.

## Wave G Tests

- **G.T1 (subsystem)**: Full validation suite passes (pytest, ruff, obdk validate, node check).
- **G.T2 (fresh-agent)**: Fresh-agent drill from repository root succeeds; agent identifies all surfaces.
- **G.T3 (anti-derailment)**: Purpose anchor file exists with immutable objective and 5 derailment patterns.
- **G.T4 (anti-derailment)**: Recovery protocol file exists.
- **G.T5 (anti-derailment)**: Derailment log has at least the 4 cataloged past derailments seeded.
- **G.T6 (plan-integrity)**: All ledger files have headers and are append-only (no row deletion in git history).
- **G.T7 (plan-integrity)**: `21_handoff_card.md` exists and validated by G.T2.
- **G.T8 (plan-integrity)**: Absorbability verdict file exists with verdict from allowed set.

## Cross-Wave Standing Tests

These tests run at any time and must always pass:

- **STD.T1**: Plan folder has no zone morte (no file without entry in `00_INDEX.md`).
- **STD.T2**: Plan folder has no unfilled-stub tokens. The implementation script defines the red-flag token list in code and uses exact token boundaries; substrings inside ordinary words do not count.
- **STD.T3**: All cited subsystem paths exist on disk.
- **STD.T4**: `ledger/active_wave.md` is well-formed (active_wave value matches one of {0, A, B, C and D parallel, E, F, G, closed}).
- **STD.T5**: No plan file exceeds 500 lines.
- **STD.T6**: Orthodox execution mantra appears in every plan markdown file, including all wave files.
- **STD.T7**: Every wave closure report includes the orthodox update packet fields: wiki, implementation ledger, changelog, README, GitHub push or operator waiver.
- **STD.T8**: `20_adversarial_review_packet.md` asks reviewers to audit the orthodox update packet.

## Test Implementation

Most tests can be implemented as:

- pytest functions in this plan folder (e.g. `test_plan_integrity.py`)
- bash/PowerShell scripts in `tests_recipes/` for plan-folder structural checks
- OBDK pytest extensions for subsystem tests
- Recipes in `reports/wave_*_*.md` for fresh-agent tests

Implementation is staged: STD tests + Wave 0 tests are created in Wave 0; per-wave tests are created in their respective waves.

## Verification Discipline

Per `superpowers:verification-before-completion`:

- No claim of "wave closed" without running the wave's test suite.
- No claim of "test passes" without showing exit code or output.
- Tests verify the desired behavior, not the implementer's belief about the behavior.
