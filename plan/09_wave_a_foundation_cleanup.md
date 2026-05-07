# Wave A — Foundation Cleanup
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Remove ambiguity in the filesystem before completing OBDK or VRE. Historical research-grade overshoot inside OBDK `.vibe-science/RQ-001-d0-first-cycle/` is marked experimental at file and directory level. Cluster D v0.1 closure status is resolved or explicitly deferred. Stale prose in OBDK control plane is swept.

## Allowed Write Set

Wave A may write to:

- `Agentic_architect/ledger/` and `Agentic_architect/reports/`
- `Agentic_architect/plan/` mirror after any plan amendment
- OBDK `.vibe-science/OVERSHOOT_STATUS.md` (new directory-level marker)
- OBDK `.vibe-science/RQ-001-d0-first-cycle/**/*.md` — header block prepended only (no content removal)
- OBDK `analisi_claude/project_plan/ledger/*` — append rows only (no deletion)
- OBDK `analisi_claude/project_plan/plan/00_current_state.md` — Cluster D status update
- OBDK `analisi_claude/project_plan/plan/06_d0_first_cycle_roadmap.md` — stale prose corrections only

Wave A does NOT:

- delete any file;
- modify any contract;
- modify any test;
- modify any production code;
- write to VRE, Phase 10, Phase 9, or Vibe Science folders;
- modify the sibling Codex plan folder.

## Pre-conditions

Wave 0 must be closed (`ledger/active_wave.md` shows `active_wave: A`).

## Atomic Tasks

### Task A1 — Mark experimental quarantine at directory level

- [ ] Create `vibe-science/blueprints/private/onco-bio-discovery-kernel/.vibe-science/OVERSHOOT_STATUS.md`.
- [ ] Content: explain that `.vibe-science/RQ-001-d0-first-cycle/` is research-grade overshoot from prior derailment, not the active implementation plan; reference active plan mirror at `Agentic_architect/plan/README.md`; preserve traceability rule (do not delete; do not block waves unless operator reactivates); allowed reuse (methods, confounders, review discipline as reference material).

### Task A2 — Mark experimental quarantine at file level

For each file under `.vibe-science/RQ-001-d0-first-cycle/`, prepend a header block:

```markdown
> **EXPERIMENTAL — historical overshoot. See `../OVERSHOOT_STATUS.md`.**
> This file is research-grade material from a prior derailment. Not part of the active implementation plan. Do not treat as binding for tool completion.
```

Files to mark (from `01_canonical_state_audit.md`):

- [ ] `STATE.md`
- [ ] `PROGRESS.md`
- [ ] `CLAIM-LEDGER.md`
- [ ] `ASSUMPTION-REGISTER.md`
- [ ] `SERENDIPITY.md`
- [ ] `RQ-001-d0-first-cycle/RQ.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/context.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/landscape.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/gaps.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/data-audit.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/hypotheses.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/triage.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/A2_memo_open_questions_resolved.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/A3_pathway_record_substrate_gap.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/A4_extended_confounder_list.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/A5_replicate_floor_pre_specification.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/B4_rots_stage2_preregistration.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/D1_cohort_metadata_audit.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/D5_skepticism_policy_charter_rfc.md`
- [ ] `RQ-001-d0-first-cycle/00-brainstorm/D6_cohort_record_substrate_gap.md`
- [ ] `RQ-001-d0-first-cycle/05-reviewer2/brainstorm-review.md`
- [ ] `RQ-001-d0-first-cycle/05-reviewer2/brainstorm-review-pass2.md`
- [ ] `RQ-001-d0-first-cycle/05-reviewer2/brainstorm-review-pass3.md`
- [ ] `RQ-001-d0-first-cycle/05-reviewer2/B0_gate_verdict.md`
- [ ] `RQ-001-d0-first-cycle/05-reviewer2/pass4-pre-stage1-review.md`
- [ ] `RQ-001-d0-first-cycle/01-stage1/cohort_pmi_audit.md`
- [ ] `RQ-001-d0-first-cycle/01-stage1/F3_gsva_pre_registration.md`
- [ ] `RQ-001-d0-first-cycle/01-stage1/TASK16_reference_quantification_preregistration.md`

If new files are discovered under the same directory not in the list above, mark them too and update this list before closing the task.

### Task A3 — Resolve Cluster D v0.1 closure status

- [ ] Read `vibe-science/blueprints/private/onco-bio-discovery-kernel/analisi_claude/project_plan/ledger/gate_review_log.md` and `operator_decisions.md`.
- [ ] Check whether `CLUSTER-D-HAT3-ACCEPT-002` is operator-closed or pending.
- [ ] If pending: write a row to this plan's `ledger/operator_decisions.md` describing the decision needed (close vs intentional deferral) and request operator response.
- [ ] If closed: update OBDK `analisi_claude/project_plan/plan/00_current_state.md` if any reference to "operator closure pending" for Cluster D v0.1 still exists.
- [ ] Record the finding in this plan's `reports/wave_a_cluster_d_status.md`.

### Task A4 — Stale prose sweep

- [ ] Search OBDK `analisi_claude/project_plan/plan/` and `analisi_claude/project_plan/wiki/` for stale tokens that contradict current state:
  - "23 contracts" (current is 24+)
  - "190 fixtures" (current is 202+)
  - "Stage 1 BLOCKED" (Stage 1 is not the active scope)
  - "Wave 1 drafts pending" (Wave 1 is overshoot)
  - "Pass 4 BLOCK" (overshoot)
  - "218 passed" (current is 231+)
  - "kernel as it exists at 23 contracts"
- [ ] For each hit, decide: (a) fix in same commit if the surface is forward-looking and stale, (b) leave historical if the surface is append-only ledger or historical roadmap, (c) operator decision if ambiguous.
- [ ] Record findings and dispositions in `reports/wave_a_stale_prose_sweep.md`.

### Task A5 — Verification

- [ ] Re-run OBDK plan-pack guardrail and confirm pass.
- [ ] Re-run OBDK contracts validate and confirm count unchanged (Wave A does not modify contracts).
- [ ] Confirm red-flag token scan in this plan folder returns zero unfilled-stub hits; the scan must use exact token boundaries so substrings inside ordinary words do not count.
- [ ] Append a row to `ledger/change_log.md`:
  ```
  | <ISO date> | INTPLAN-A-001 | OBDK .vibe-science/* + analisi_claude/project_plan/* + plan/reports/* | wave A: experimental quarantine, Cluster D status, stale prose sweep | closed |
  ```
- [ ] Update `ledger/active_wave.md`:
  ```
  active_wave: B
  since: <ISO date>
  last_updated_by: <agent>
  last_updated_reason: wave A closed; opening wave B
  ```

## Adversarial Review Required

Wave A changes the surface area of the filesystem (new markers, new ledger rows, file headers prepended to many files). Adversarial review by the non-author agent is required:

- Implementer logs handoff in `ledger/multi_agent_pairing.md`.
- Reviewer verifies: file header prepend coverage matches the list, no file content removed, ledger rows append-only, OBDK contracts unchanged.
- Reviewer issues verdict: ACCEPT / ACCEPT_WITH_MINOR / REDIRECT.

If REDIRECT, the implementer addresses findings and re-requests review. Maximum three REDIRECT cycles.

## Closure Criteria

Wave A closes when:

- A1, A2, A3, A4, A5 all checked;
- operator has decided on Cluster D v0.1 (close, defer, or explicit "not yet");
- adversarial review issues ACCEPT or ACCEPT_WITH_MINOR;
- `ledger/change_log.md` has the closure row;
- `ledger/active_wave.md` points at Wave B.

## Stop Conditions

Wave A stops and operator is asked if:

- a file in the experimental quarantine list does not exist on disk;
- a stale prose hit is in an append-only ledger that should not be modified;
- the operator has not responded on Cluster D v0.1 within the agent's session bounds;
- the OBDK plan-pack test breaks because of header prepend (should not happen since headers are valid Markdown).

## Outputs

After Wave A closure:

- OBDK `.vibe-science/OVERSHOOT_STATUS.md` exists at directory level
- 28+ files under `.vibe-science/RQ-001-d0-first-cycle/` carry experimental header
- `reports/wave_a_cluster_d_status.md` documents Cluster D v0.1 closure outcome
- `reports/wave_a_stale_prose_sweep.md` documents sweep findings and dispositions
- `ledger/change_log.md` has rows for all A1-A5 actions and a closure row
- `ledger/active_wave.md` points at Wave B
