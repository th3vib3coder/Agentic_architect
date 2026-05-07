# Anti-Derailment Discipline
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Prevent the recurrence of derailment patterns observed in past sessions. This file is the operational reference for how an agent recognizes derailment, stops, recovers, and prevents recurrence.

## Five Catalogued Derailment Patterns

| ID | Pattern Name | Symptom | Trigger | Correction |
|---|---|---|---|---|
| P1 | Framework capture | Agent treats Vibe Science (or any framework) as the master plan instead of rigor layer | "/vibe" invocation interpreted literally; agent runs Phase 0 BRAINSTORM as if doing real research | Read `02_purpose_anchor.md` and active wave; framework is rigor layer, plan is master |
| P2 | "Minimum viable" shortcut | Agent proposes a faster alternative that skips written tasks | Agent feels plan is too long or that smoke-test is enough | Execute the plan or patch the plan via `20_adversarial_review_packet.md`; do not bypass |
| P3 | Smoke-test theater | Agent calls fixture run "we touched data" or "we ran the analysis" | Test passes on `tests/fixtures/` and agent reports it as data execution | State exact source path, command, and scope; smoke-test on fixture is not real data |
| P4 | Research-grade overshoot | Tool completion task becomes publication-grade biological analysis | Agent adds confounder harness pre-registrations, GSVA params, falsification hooks for tool work | Mark such material as reference only; return to active wave scope |
| P5 | Operator correction ignored | Agent proposes a third option after operator says "not this, do that" | Agent reframes the correction or proposes "yet another way" | LAW 11: follow correction immediately, write derailment row, do not argue |

## Detection Heuristics

The agent self-checks for derailment when any of these appear:

- about to write a file outside the active wave's allowed write set;
- about to invoke a framework's full discipline (Phase 0 BRAINSTORM, R2 ensemble, full Vibe Science) without an active wave that requires it;
- about to declare "minimum viable", "smoke-test enough", "skip this for now", "let's just";
- about to claim "we touched data" when only fixture or smoke-test ran;
- about to propose a third path after the operator narrowed to two;
- about to add scientific discipline (cohort metadata audit, GSVA params, falsification hooks) without explicit operator request;
- about to interpret a framework skill as overriding the plan.

If any heuristic fires, the agent STOPS and runs the recovery protocol below.

## Recovery Protocol

When derailment is detected:

1. **Stop all writes immediately**. Do not save any file in progress.
2. **Identify the pattern ID** from the table above.
3. **Read three files in order**:
   - `02_purpose_anchor.md`
   - `04_master_sequence.md` (active wave)
   - The active wave file
4. **Write a row** to `ledger/derailment_log.md` with: ISO date, pattern ID, trigger description, action taken, prevention hook proposal.
5. **Mark any artifacts created during the derailment as experimental** (header block) if they are outside the active wave's scope.
6. **Ask the operator** whether to archive, keep as reference, or promote via formal plan patch.
7. **Resume only after** the operator records a decision in `ledger/operator_decisions.md` (if archive or promote) or after the agent confirms the artifact stays as experimental reference (no operator needed).

## Prevention Hooks

### Pre-Action Check (mandatory before non-trivial action)

Before any non-trivial write or run command, the agent answers:

1. Which active wave permits this action?
2. Which file will record the result?
3. Which command or test will prove it worked?
4. Does this change tooling scope or biological research scope?
5. Does this require operator decision per `05_decision_boundaries.md`?

If any answer is unclear or "STOP", the agent reads the active wave file. If still unclear, the agent asks the operator.

### Automatic Stop Rules

The agent stops immediately if:

- a task requires deleting or rewriting an append-only ledger;
- a proposed action changes the project objective or non-objective in `02_purpose_anchor.md`;
- a task requires public export;
- the agent starts optimizing biological analysis details not requested by the active wave;
- the agent wants to skip a wave because a shortcut feels faster;
- a validation command cannot be run and no fallback evidence is possible;
- the active wave is Wave D and HB-1 (Phase 9 Wave 5 closure + operator GO) is not satisfied.

### Test-Enforced Guardrails

`17_test_strategy.md` defines tests that verify:

- existence of `02_purpose_anchor.md` with the immutable objective and the five patterns;
- existence of `07_anti_derailment.md` with the recovery protocol;
- existence of `21_handoff_card.md` (created in Wave G);
- existence of `ledger/active_wave.md` (created in Wave 0);
- no new top-level file in this plan folder without an entry in `00_INDEX.md`;
- no file in this plan folder without a header line summarizing its role.

These tests run as part of Wave G validation and can be re-run at any time.

## Vibe Science Coexistence Rules

Vibe Science is the rigor layer, not the master plan. The boundary:

| Vibe Science is invoked when | Vibe Science is not the driver |
|---|---|
| A claim or quantitative result is being promoted (R2 review) | A wave task is selecting a script from registry |
| LAW 9 confounder harness applies to a quantitative claim | LAW 9 is interpreted as universal pre-registration discipline |
| A negative result needs Salvagente seed | A failed validation command needs more than retry |
| A schema-validated gate enforces an artifact format | A wave step needs to produce a tool artifact |

If Vibe Science discipline conflicts with the active wave, the active wave wins, and the agent records the conflict in `ledger/derailment_log.md` so the conflict can be resolved at plan amendment.

## Operator Questions Are Not Failure

The agent should ask the operator only at the declared decision categories from `05_decision_boundaries.md`. Asking outside those categories is over-asking. Not asking inside those categories is governance failure. The matrix is the boundary.

## Cross-Plan Reconciliation

This plan and the sibling Codex plan must reconcile via adversarial review. If the two plans disagree on a derailment correction, the operator decides. Until then, both plans treat their own anti-derailment discipline as authoritative for their own scope.

## Cataloged Past Derailments (reference)

The following derailments occurred before this plan was written and informed the patterns above:

| Date | Pattern | Trigger | Outcome |
|---|---|---|---|
| 2026-05-07 | P1 | "/vibe" invoked → Phase 0 BRAINSTORM with 6 files + 5 BLOCKING demands + Pass 4 BLOCK Stage 1 + Wave 1 setup tasks | Operator corrected; experimental quarantine via Wave A |
| 2026-05-07 | P2 | Proposed "minimum viable smoke-test" to bypass Pass 4 setup tasks | Operator corrected; returned to plan |
| 2026-05-07 | P3 | Called fixture E2E test "we touched data" | Operator corrected; smoke-test on fixture distinguished from real data |
| 2026-05-07 | P5 | Proposed "skip Pass 4, go to Phase 1.1 minimum viable" after operator said "execute the plan" | Operator corrected with LAW 11; plan execution resumed |

These rows seed `ledger/derailment_log.md` when Wave 0 creates that file.

## Key Mantras

- The plan is executed; it is not reinterpreted in chat.
- Vibe Science is rigor, not the master plan.
- Smoke-test on fixture is not real data.
- Operator correction is followed immediately, not argued.
- A shortcut that bypasses written tasks is a derailment, not productivity.
