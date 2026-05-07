# Multi-System Recovery Protocol
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Enable a fresh agent (no chat history) to recover the integrated system state and resume work. Covers full fresh-context recovery, post-derailment recovery, and partial-state recovery (e.g. ledger missing).

## Three Recovery Scenarios

### Scenario 1: Full fresh-context recovery

Agent has no chat history but has filesystem access. Goal: identify active wave, list pending tasks, resume execution or escalate to operator.

### Scenario 2: Post-derailment recovery

Agent realizes it has deviated from the plan (matched a pattern from `07_anti_derailment.md`). Goal: stop, mark experimental any artifacts created during derailment, return to active wave.

### Scenario 3: Partial-state recovery

Some part of the filesystem is unexpected (ledger missing rows, plan file modified, contradictory state). Goal: identify the inconsistency, document it, ask operator if not unambiguously fixable.

## Scenario 1 Procedure (Fresh-Context)

Six-file recovery path:

1. Read `Agentic_architect/README.md`, then `Agentic_architect/plan/README.md` — repo entry point plus plan scope, goal, non-goal.
2. Read `23_project_goal_and_implementation_doctrine.md` — complete durable goal, current state, final system, and implementation doctrine.
3. Read `00_INDEX.md` — file role table, active wave pointer, source systems table.
4. Read `01_canonical_state_audit.md` — what exists in OBDK/VRE/Vibe, dependencies, experimental quarantine.
5. Read `04_master_sequence.md` — wave order, dependencies, parallel safety.
6. Read `Agentic_architect/ledger/active_wave.md` — current active wave; if file does not exist, default Wave 0.

After these six reads, the agent knows:

- what the system is and what it's not;
- where each subsystem lives;
- what the active wave is;
- what to read next.

Seventh read: the active wave file (e.g. `09_wave_a_foundation_cleanup.md`).

Eighth read: `16_atomic_task_backlog.md` — pick next task from the active wave's section.

## Scenario 1: Active wave determination

If `ledger/active_wave.md` does not exist: active wave is Wave 0 (preflight). Execute Wave 0.

If `ledger/active_wave.md` shows `active_wave: A` and `ledger/change_log.md` has no INTPLAN-A-001 closure row: Wave A in progress; check `ledger/active_subtasks.md` for in-progress task.

If `ledger/change_log.md` shows INTPLAN-G-001 closure row: project is closed; agent reads `21_handoff_card.md` for operational use.

If `ledger/active_wave.md` shows `paused: true` or `blocked_by: <decision_id>`: read the operator decision register entry referenced; agent waits or escalates.

## Scenario 1: Subsystem state

After identifying active wave, verify subsystem state:

```
cd vibe-science/blueprints/private/onco-bio-discovery-kernel
python -m pytest tests/test_project_plan_pack.py -q  # smoke OBDK plan-pack
python -m obdk.cli contracts validate --charter charter-v0.5.md  # smoke OBDK contracts
node vibe-science/blueprints/private/WIKI_VRE/tools/build-registries.mjs --check  # smoke WIKI_VRE
```

If any smoke fails, agent records in `reports/recovery_smoke_<date>.md` and escalates if blocking.

## Scenario 1: Operator decisions awaiting

Read `19_operator_decision_register.md`. If any decision is required to proceed (status `awaiting_operator`), agent stops and reports.

## Scenario 2 Procedure (Post-Derailment)

Trigger: agent matches a derailment pattern from `07_anti_derailment.md`.

1. Stop all writes immediately.
2. Identify pattern ID (P1-P5).
3. Read `02_purpose_anchor.md` to re-anchor the immutable objective.
4. Read `07_anti_derailment.md` for the pattern's corrective action.
5. Read `04_master_sequence.md` and active wave file to recall scope.
6. Mark any artifacts created during derailment as experimental:
   - file-level: prepend `> EXPERIMENTAL — derailment artifact, see ledger/derailment_log.md` header
   - directory-level: create `EXPERIMENTAL_STATUS.md` in the directory
7. Write a row to `ledger/derailment_log.md`:
   ```
   | <ISO date> | P<n> | <trigger description> | <action taken> | <prevention hook proposal> |
   ```
8. Ask operator whether to archive, keep as reference, or promote via formal plan patch.
9. Resume only after operator decision recorded in `ledger/operator_decisions.md` (if archive or promote needed) or after agent confirms experimental marking suffices.

## Scenario 3 Procedure (Partial-State)

If the agent encounters unexpected filesystem state (e.g. ledger row missing that the plan expected, plan file modified by unknown actor, contradictory pointer):

1. Stop the action that surfaced the inconsistency.
2. Capture the inconsistency in detail in `reports/recovery_partial_state_<date>.md`:
   - file path
   - expected content (per plan)
   - observed content
   - hypothesized cause (concurrent agent, manual edit, partial commit, etc.)
3. Do NOT modify the inconsistent state.
4. Ask operator to:
   - investigate the cause;
   - decide on resolution (revert, accept, patch with new operator decision);
   - record decision in `ledger/operator_decisions.md`.
5. Resume after operator decision.

## Cross-System Recovery

If recovery requires cross-subsystem state:

- OBDK state: `analisi_claude/project_plan/01_RECOVERY_PROTOCOL.md` (single-system OBDK)
- VRE state: `WIKI_VRE/CLAUDE.md` (single-system WIKI_VRE)
- Phase 10 state: `phase10-knowledge-layer/02-formal-design-spec.md` HB-1
- Vibe Science state: repository root SKILL.md and protocol files

The integrated recovery (this file) coordinates the three. If a subsystem is missing or inconsistent, the agent uses the subsystem's own recovery before continuing the integrated recovery.

## Recovery Test

`17_test_strategy.md` defines tests that verify:

- six-file recovery path works (manually run by Wave G fresh-agent drill);
- subsystem smoke checks complete in less than 5 minutes;
- operator decision register is queryable;
- derailment log seeded.

These tests run at Wave G closure and at any operator-requested audit.

## Recovery Time Targets

| Scenario | Target time |
|---|---|
| Scenario 1 (fresh-context) | 10 minutes (6 reads + smoke) |
| Scenario 2 (post-derailment) | 5 minutes (read + mark + log + escalate) |
| Scenario 3 (partial-state) | 5 minutes (capture + escalate) |

If recovery exceeds target time, the agent records the overrun in `reports/recovery_overrun_<date>.md` and considers the recovery surface itself a candidate for improvement (Wave G can patch).

## Anti-Stale-Recovery Discipline

The recovery protocol must be re-validated when:

- a wave closes (Wave G fresh-agent drill);
- a plan amendment changes any of the six recovery files;
- the operator requests audit;
- a new derailment pattern is added to `07_anti_derailment.md`.

Re-validation is recorded in `reports/recovery_validation_<date>.md`.
