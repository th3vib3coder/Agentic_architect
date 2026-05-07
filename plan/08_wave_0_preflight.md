# Wave 0 — Preflight
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Verify the state of OBDK, VRE, and Vibe Science before any other wave starts. Create the ledger surface that the rest of the plan depends on. Establish the active wave pointer.

## Why Wave 0 Exists

The other waves assume:

- ledgers under `ledger/` exist;
- `ledger/active_wave.md` records the current wave;
- subsystem paths cited in `01_canonical_state_audit.md` are reachable;
- Phase 9 Wave 5 status is known so Wave D can decide when to start.

Without Wave 0, the agent would create ledgers ad-hoc and risk inconsistency or treat plan files as ledgers (incorrect).

## Allowed Write Set

Wave 0 may create:

- `Agentic_architect/ledger/active_wave.md`
- `Agentic_architect/ledger/change_log.md`
- `Agentic_architect/ledger/operator_decisions.md`
- `Agentic_architect/ledger/adversarial_reviews.md`
- `Agentic_architect/ledger/derailment_log.md`
- `Agentic_architect/ledger/multi_agent_pairing.md`
- `Agentic_architect/ledger/active_subtasks.md`
- `Agentic_architect/reports/wave_0_preflight_report.md`
- `Agentic_architect/plan/**` (versioned mirror of this plan source)

Wave 0 does NOT modify:

- any OBDK, VRE, Phase 10, Phase 9, or Vibe Science file;
- the sibling Codex plan folder;
- any plan file outside this folder except the `Agentic_architect/plan/` mirror.

## Atomic Tasks

### Task P0.1 — Create ledger directory and seed files

- [ ] Create directory `ledger/` (Write tool autocreate via first file).
- [ ] Create `ledger/active_wave.md` with content:
  ```
  active_wave: 0
  since: <ISO 8601 timestamp>
  last_updated_by: <agent>
  last_updated_reason: wave 0 preflight starting
  blocked_by: none
  ```
- [ ] Create `ledger/change_log.md` with header table: `| Date | Change ID | Files | Summary | Status |`.
- [ ] Create `ledger/operator_decisions.md` with header table: `| Date | Decision ID | Decision | Rationale | Scope |`.
- [ ] Create `ledger/adversarial_reviews.md` with header table: `| Date | Review ID | Reviewer | Scope | Verdict | Findings |`.
- [ ] Create `ledger/derailment_log.md` with header table: `| Date | Pattern | Trigger | Action | Prevention Hook |`. Seed with the four cataloged past derailments from `07_anti_derailment.md`.
- [ ] Create `ledger/multi_agent_pairing.md` with header table: `| Date | Wave/Task | Implementer | Reviewer | Verdict | Evidence Ref |`.
- [ ] Create `ledger/active_subtasks.md` with header table: `| Started | Wave/Task | Agent | Status |`.

### Task P0.2 — Verify subsystem paths exist

For each path in `01_canonical_state_audit.md`, check existence and recordability:

- [ ] `vibe-science/blueprints/private/onco-bio-discovery-kernel/` — directory exists
- [ ] `vibe-science/blueprints/private/onco-bio-discovery-kernel/charter-v0.5.md` — file exists
- [ ] `vibe-science/blueprints/private/onco-bio-discovery-kernel/obdk/cli.py` — file exists
- [ ] `vibe-science/blueprints/private/onco-bio-discovery-kernel/recipes/d0_eaoc_syndecan_upr.yaml` — file exists
- [ ] `vibe-science/blueprints/private/onco-bio-discovery-kernel/.vibe-science/RQ-001-d0-first-cycle/` — directory exists (experimental quarantine target)
- [ ] `vibe-science/blueprints/private/WIKI_VRE/` — directory exists
- [ ] `vibe-science/blueprints/private/WIKI_VRE/CLAUDE.md` — file exists
- [ ] `vibe-science/blueprints/private/WIKI_VRE/index.md` — file exists
- [ ] `vibe-science/blueprints/private/WIKI_VRE/tools/build-registries.mjs` — file exists
- [ ] `vibe-science/blueprints/private/phase10-knowledge-layer/02-formal-design-spec.md` — file exists
- [ ] `vibe-science/blueprints/private/phase9-implementation-plan/00-index.md` — file exists
- [ ] `vibe-science/blueprints/private/integrated-agentic-research-system-plan/README.md` — sibling Codex plan exists

If any path is missing, the agent stops and asks the operator.

### Task P0.3 — Capture Phase 9 Wave 5 status

- [ ] Read `vibe-science/blueprints/private/phase9-implementation-plan/00-index.md`.
- [ ] Identify whether Wave 5 split-series (06d-T5.2..T5.7) is in progress, completed, or paused.
- [ ] Record finding in `reports/wave_0_preflight_report.md` under section "Phase 9 Wave 5 status".

This status is the gate for Wave D Task D1.

### Task P0.4 — Run baseline validation commands

Run each command and record output (or exact error if command unavailable):

- [ ] OBDK plan-pack guardrail:
  - bash/POSIX:  `cd vibe-science/blueprints/private/onco-bio-discovery-kernel && python -m pytest tests/test_project_plan_pack.py -q`
  - PowerShell:  `cd vibe-science/blueprints/private/onco-bio-discovery-kernel; python -m pytest tests/test_project_plan_pack.py -q`
  - Expected: pass.

- [ ] OBDK contracts validate:
  - any shell:  `python -m obdk.cli contracts validate --charter charter-v0.5.md`
  - Expected: `contracts=24 fixtures=202 unexpected=0` or current target.

- [ ] OBDK ruff:
  - any shell:  `python -m ruff check .`
  - Expected: clean.

- [ ] OBDK full pytest (read-only):
  - any shell:  `python -m pytest --tb=short -q`
  - Expected: 231+ passed.

- [ ] WIKI_VRE registry check:
  - any shell:  `node vibe-science/blueprints/private/WIKI_VRE/tools/build-registries.mjs --check`
  - Expected: exit 0 or recorded fallback if Node unavailable.

Record exact output in `reports/wave_0_preflight_report.md`.

### Task P0.5 — Append change_log row

- [ ] Append to `ledger/change_log.md`:
  ```
  | <ISO date> | INTPLAN-PRE-001 | ledger/* and reports/wave_0_preflight_report.md | wave 0 preflight: ledgers seeded, subsystem paths verified, baselines captured | open |
  ```

### Task P0.6 — Wave 0 closure

- [ ] All P0.1 - P0.5 tasks checked.
- [ ] `reports/wave_0_preflight_report.md` exists with all P0.2, P0.3, P0.4 evidence.
- [ ] No subsystem path missing (or operator notified if any missing).
- [ ] Append closure row to `ledger/change_log.md` with status `closed`.
- [ ] Update `ledger/active_wave.md` to point at Wave A.

## Closure Criteria

Wave 0 closes when:

- all 7 ledger files exist with correct headers;
- preflight report records all subsystem path checks;
- baseline validation outputs are captured (or fallback recorded for unavailable commands);
- Phase 9 Wave 5 status is documented;
- `ledger/active_wave.md` updated to Wave A;
- no operator decision is required (Wave 0 is verification-only).

## Stop Conditions

Wave 0 stops and operator is asked if:

- a subsystem path cited in `01_canonical_state_audit.md` does not exist;
- the OBDK plan-pack test fails (indicates pre-existing breakage);
- WIKI_VRE registry check fails AND Node is unavailable;
- the agent realizes Wave 0 ledger creation conflicts with existing files (ledger already exists from a prior partial run);
- contracts validate output deviates from `contracts=24 fixtures=202 unexpected=0` (indicates state drift since plan creation).

## Output

The output of Wave 0 is:

- 7 files under `ledger/`;
- 1 file under `reports/wave_0_preflight_report.md`;
- updated `ledger/active_wave.md` pointing at Wave A;
- 1 row in `ledger/change_log.md` closing Wave 0.

After Wave 0 closure, Wave A becomes active and the agent reads `09_wave_a_foundation_cleanup.md`.
