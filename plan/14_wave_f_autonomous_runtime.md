# Wave F — Autonomous Analysis Runtime
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Enable the agent to perform a bounded autonomous analysis loop from paper or problem statement to persisted evidence. Wave F runs three scenarios end-to-end (paper-to-procedure, existing-script execution, missing-script generation) and one failure scenario, demonstrating that the integrated system handles success and failure with operator escalation only at declared decision points.

## Pre-conditions

Wave E closed (`ledger/active_wave.md` shows `active_wave: F`).

## Allowed Write Set

Wave F may write to:

- OBDK `runs/autonomous_*/` directories (run output)
- OBDK `tests/test_autonomous_runtime.py`
- WIKI_VRE pages (created by autonomous run)
- `Agentic_architect/ledger/` and `Agentic_architect/reports/`
- `Agentic_architect/plan/` mirror after any plan amendment

Wave F does NOT:

- modify contracts, recipes, or registry entries;
- modify VRE Phase 10 implementation;
- modify sibling Codex plan;
- promote any claim to `claimed` (claim promotion is in operator decision categories).

## Atomic Tasks

### Task F1 — Autonomy policy

Write `reports/wave_f_autonomy_policy.md` specifying:

- [ ] Maximum unattended runtime per autonomous run (default 1 hour).
- [ ] Maximum download size per ingestion (default 100 MB).
- [ ] Allowed local compute (default: no GPU; CPU bounded by default OS limits).
- [ ] Forbidden public export.
- [ ] Operator escalation thresholds (cost > $0, runtime > 1h, ambiguous method classification, R2 REDIRECT, missing source).
- [ ] Failure retry limits (default 3).

### Task F2 — Paper-to-procedure scenario

Use one real or local paper bundle:

- [ ] Run `obdk ingest-paper` on the paper.
- [ ] Run `obdk extract-methods` on the ingested source.
- [ ] For each extracted method, classify via script registry.
- [ ] If existing script: route to F3 sub-flow.
- [ ] If missing: route to F4 sub-flow.
- [ ] If review-required: stop and escalate per autonomy policy.
- [ ] Expected outputs: source page (VRE), method records (OBDK + VRE), mapped script decisions (OBDK), generated script candidate if needed (sandbox), review-required items.

### Task F3 — Existing script execution scenario

Use a procedure that maps to an existing registered script:

- [ ] Look up script in registry.
- [ ] Instantiate recipe with method-record parameters.
- [ ] Execute recipe via `obdk run`.
- [ ] Validate evidence-package and validation-ladder artifacts.
- [ ] Build review packet via Wave E adapter.
- [ ] Trigger R2 review (or stage if no live R2 reviewer).
- [ ] Persist run + evidence + review verdict to VRE.
- [ ] Expected outputs: run manifest, analysis artifact, evidence package, VRE computed page, R2 review record (or staged).

### Task F4 — Missing script generation scenario

Use a procedure that has no registered script:

- [ ] Trigger sandbox script generation via `obdk generate-script`.
- [ ] Verify test fixture is created first.
- [ ] Execute on minimal fixture.
- [ ] Register generated script with `generated_pending_review` status.
- [ ] Build review packet.
- [ ] Trigger R2 review.
- [ ] Do NOT promote to claim until review passes.
- [ ] Expected outputs: generated script in sandbox, unit test, registration record, review status `generated_pending_review`, no claim promotion.

### Task F5 — Failure scenario

Simulate failures and verify fail-closed behavior:

- [ ] Missing provenance: paper without DOI/PMID; expected: ingestion fails with explicit error, escalation row in `19_operator_decision_register.md`.
- [ ] Failed script test: introduce a bug in generated script; expected: registration fails, status remains `pending_review`, no execution.
- [ ] Vibe review REDIRECT: simulate R2 REDIRECT on a claim; expected: status remains `computed`, findings recorded.
- [ ] Multiple active VRE objectives: create two objectives without supersession; expected: agent creates escalation record.
- [ ] Failed validation command: introduce contract validation failure; expected: agent stops, records error, asks operator.

### Task F6 — Autonomous runtime report

- [ ] Write `reports/autonomous_runtime_report.md` with: commands executed, artifacts created, escalation points hit, failures and recoveries, evidence trace query result for each successful run.

### Task F7 — Append change_log row and update active wave

- [ ] Append closure row.
- [ ] Update `ledger/active_wave.md` to point at `G`.

## Adversarial Review Required

Wave F validates the integrated system in operation. Reviewer verifies:

- autonomy policy thresholds are enforced (not just declared);
- paper-to-procedure scenario produces complete trace;
- existing-script scenario completes without operator path hints;
- missing-script generation does not promote to claim without review;
- failure scenarios fail closed with explicit error and escalation;
- no derailment patterns observed in the autonomous runs (agent stays in scope).

## Closure Criteria

Wave F closes when:

- F1 through F7 checked;
- at least one paper-to-evidence loop completes successfully;
- at least one failure loop demonstrates fail-closed;
- escalation points fire only at declared categories;
- adversarial review ACCEPT or ACCEPT_WITH_MINOR.

## Stop Conditions

Wave F stops and operator is asked if:

- a real paper is needed for F2 and operator must provide one;
- TCGA-OV or other restricted-access data is required for F3 or F4 (operator decision);
- LLM API call is needed for F4 sandbox generation and operator must approve cost;
- R2 reviewer is needed live and the operator has not designated a reviewer agent;
- claim promotion test in F3 or F4 requires operator approval (since claim promotion is in operator decision categories).

## Outputs

After Wave F closure:

- `reports/wave_f_autonomy_policy.md` defines bounds
- 3 successful autonomous run reports (F2, F3, F4)
- 5 failure scenario reports (F5)
- `reports/autonomous_runtime_report.md` summary
- runs/ directory populated with autonomous run artifacts
- VRE pages created by autonomous runs
- ledger rows for all F tasks
- `ledger/active_wave.md` points at G
