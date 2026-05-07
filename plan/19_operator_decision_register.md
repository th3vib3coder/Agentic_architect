# Operator Decision Register
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Single source of truth for decisions awaiting operator. The agent writes to this file when it identifies a decision in one of the declared categories from `05_decision_boundaries.md` and stops the relevant action.

## How To Read

| Column | Meaning |
|---|---|
| Decision ID | `OPDEC-<wave>-<sequence>-<short-name>` |
| Wave | Active wave when decision was raised |
| Category | One declared category from `05_decision_boundaries.md` |
| Description | One-sentence summary of the decision |
| Options | Concrete options the operator can pick |
| Recommendation | Agent's preferred option with rationale (advisory only) |
| Status | `awaiting_operator`, `decided`, `superseded` |
| Decision rationale | Filled when status becomes decided |
| Reference | Link to ledger row in `ledger/operator_decisions.md` |

## Active Decisions Awaiting Operator

(Empty at plan creation. Wave 0 may seed initial entries during preflight.)

## Decision Categories

The declared categories where operator decision is required:

1. **Objective change** — modifies immutable objective in `02_purpose_anchor.md`.
2. **Scope change** — adds or removes waves; modifies allowed write set.
3. **Irreversible state change** — file deletion, ledger rewrite, force-push.
4. **Public/private boundary change** — public export, claim-edge sharing, wiki publication.
5. **Claim status promotion** — claim from proposed to claimed.
6. **External cost or compute** — paid APIs, cloud compute, long-running jobs.
7. **Gate relaxation** — relax R2, LAW 9, LAW 13, HB-1..HB-13.
8. **GitHub push waiver** — close a task, variation, or wave without GitHub push.

## Initial Decisions (Pre-Plan-Execution)

These decisions exist at plan creation. Operator addresses them before or during Wave A.

### OPDEC-A-001 — Cluster D v0.1 closure

- **Wave**: A
- **Category**: Scope change (closes a previously deferred OBDK closure)
- **Description**: Decide whether to close `CLUSTER-D-HAT3-ACCEPT-002` (OBDK Cluster D v0.1 reviewer ACCEPT pending operator closure) or formally defer with explicit reason.
- **Options**:
  - (a) Close now: append closure row to OBDK `analisi_claude/project_plan/ledger/operator_decisions.md`.
  - (b) Defer with reason: append deferral row stating the reason and trigger for future closure.
  - (c) Re-open: declare the v0.1 ACCEPT no longer valid and request re-review (rare).
- **Recommendation**: (a) Close now if no outstanding concern; the reviewer ACCEPT is solid and v0.2 is operator-closed already.
- **Status**: closed
- **Decision rationale**: Operator provided immutable plan/workspace facts and told the team to begin; `Agentic_architect/ledger/operator_decisions.md` records the Claude plan as canonical and the sibling Codex plan as reference-only.
- **Reference**: `Agentic_architect/ledger/operator_decisions.md` rows `OPDEC-PLAN-001`, `OPDEC-PLAN-002`, and `OPDEC-PLAN-003`.

### OPDEC-WORKSPACE-001 — Operational workspace binding

- **Wave**: 0 (cross-cutting)
- **Category**: Scope clarification (where the orthodox update packet lives)
- **Description**: The operator-declared implementation workspace is `Agentic_architect`; plan ledgers, reports, wiki, README, and GitHub updates are written there, while the original plan folder remains local source and is mirrored into `Agentic_architect/plan/`.
- **Options**:
  - (a) Use `Agentic_architect` for operational ledgers/reports/wiki and mirror the plan there.
  - (b) Keep ledgers/reports inside the plan folder and use a separate GitHub strategy.
- **Recommendation**: (a), because it satisfies the operator-declared workspace and public GitHub recovery requirement.
- **Status**: closed
- **Decision rationale**: Claude REDIRECT found a repo split; the patch records `Agentic_architect` as the operational evidence surface.
- **Reference**: `Agentic_architect/ledger/operator_decisions.md` row `OPDEC-WORKSPACE-001`.

### OPDEC-D-001 — Phase 10 implementation track GO

- **Wave**: D
- **Category**: Scope change (opens implementation of Phase 10 layer)
- **Description**: Phase 10 implementation cannot start until Phase 9 Wave 5 closes AND operator gives explicit GO via `vre phase10 implementation-track-start --confirm` (or recorded equivalent decision).
- **Options**:
  - (a) Confirm GO once Phase 9 Wave 5 closes (record decision row authorizing Wave D start when Phase 9 Wave 5 reaches closed status).
  - (b) Defer Phase 10 implementation; Wave D paused indefinitely; Wave C continues solo.
  - (c) Decide alternative implementation path (rare; would change Phase 10 spec).
- **Recommendation**: (a) Confirm GO when Phase 9 Wave 5 closes, with the integrated plan as the executor.
- **Status**: awaiting_operator (also blocked by Phase 9 Wave 5 status)
- **Decision rationale**: (pending operator decision)
- **Reference**: (pending operator decision)

### OPDEC-PLAN-001 — Reconciliation between Claude plan and Codex plan

- **Wave**: 0 (cross-cutting)
- **Category**: Scope change (decides which coordination plan is canonical)
- **Description**: Two plans exist: this Claude-authored plan at `integrated-system-claude-plan/` and the sibling Codex-authored plan at `integrated-agentic-research-system-plan/`. Both target the same scope. Operator decides reconciliation.
- **Options**:
  - (a) Merge: select canonical features from both, archive the rest.
  - (b) Pick one: declare one canonical, archive the other.
  - (c) Run both in parallel: both plans execute their own waves, with sync points (rare; risk of drift).
- **Recommendation**: (b) Pick the more granular plan (the Claude one, by virtue of dedicated test strategy and recovery protocol files) OR the more concise plan (Codex one, by virtue of Codex's adversarial review on Claude plan). Operator decides based on preference.
- **Status**: awaiting_operator
- **Decision rationale**: (pending operator decision)
- **Reference**: (pending operator decision)

### OPDEC-A-002 — Archive policy for OBDK overshoot

- **Wave**: A
- **Category**: Irreversible state change (decides whether to mark experimental, archive, or delete)
- **Description**: OBDK `.vibe-science/RQ-001-d0-first-cycle/` contains 28+ research-grade overshoot files. Wave A defaults to "mark experimental" (header block + directory marker). Operator can choose archive (move to `_archive/`) or delete (operator decision required).
- **Options**:
  - (a) Mark experimental in place (default Wave A behavior).
  - (b) Archive: move directory to `vibe-science/blueprints/private/_archive_overshoot_2026-05-07/`.
  - (c) Delete: remove the directory (last resort; loses traceability).
- **Recommendation**: (a) Mark experimental in place. Preserves traceability; cheap; reversible.
- **Status**: awaiting_operator
- **Decision rationale**: (pending operator decision)
- **Reference**: (pending operator decision)

## Future Decisions (Wave-Specific)

The following decisions arise during specific waves and are documented in their respective wave files. Operator addresses them when encountered.

| Wave | Decision | Category |
|---|---|---|
| C | TCGA-OV inclusion (if relevant for recipe library) | External access |
| C | Recipe priority must-have vs nice-to-have | Scope |
| C | Operator-provided real paper for end-to-end test | Scope |
| F | Autonomy thresholds (cost / runtime / compute) | External cost |
| F | Real paper for autonomous run scenario | Scope |
| G | Public/private boundary at handoff | Public boundary |
| G | Absorbability verdict acceptance | Final closure |

## Decision Recording Format

When operator decides:

1. Update this file's row: change Status to `decided`, fill Decision rationale.
2. Append a row to `ledger/operator_decisions.md`:
   ```
   | <ISO date> | <decision id> | <decision> | <rationale> | <scope> |
   ```
3. The `Reference` column in this file points to that ledger row.

## Decision Lifecycle

`awaiting_operator` → `decided` (operator acts) OR `superseded` (a later decision replaces this one).

Superseded decisions are not deleted; they remain in this register with status `superseded` and a pointer to the superseding decision.

## GitHub Push Waiver Procedure

A GitHub push waiver is operator-only. A failed push, missing remote, missing credentials, or network outage does not automatically waive the push requirement.

When an agent cannot push reviewed work:

1. Stop before closing the task or wave.
2. Add an active decision entry with id `OPDEC-<wave>-<sequence>-no-push-waiver`.
3. Include the affected task or wave, local commit SHA if available, remote/branch attempted, exact failure reason, proposed waiver duration, and catch-up plan.
4. Wait for operator decision in `ledger/operator_decisions.md`.
5. If approved, cite the operator decision id in the changelog as `commit_local_only_via_waiver: <opdec-id>`.
6. If denied, keep the task or wave open until GitHub push succeeds.

## Anti-Stagnation Discipline

If a decision remains in `awaiting_operator` for more than the agent's session bounds without operator response, the agent:

1. Records the wait in `reports/operator_decision_wait_<date>.md`.
2. Identifies any non-blocking work that can proceed in parallel.
3. Continues parallel work or pauses gracefully (depending on whether the decision is on the critical path).

The agent does not unilaterally decide a decision marked operator-required.
