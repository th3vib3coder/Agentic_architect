# Adversarial Review Packet
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Specification for adversarial review of this Claude-authored plan by Codex (or another reviewer agent). The reviewer evaluates the plan as a coordination plan for completing OBDK + VRE Phase 10 + orchestration + anti-derailment, not as a biological research proposal.

## When To Use

- Before plan execution begins (initial review).
- At each wave closure (per-wave incremental review of the artifacts produced).
- At Wave G final review (closure of the project).

## Reviewer Instruction

You are reviewing a coordination plan for completing an integrated agentic research system. The target is whether the plan will:

1. preserve the operator's stated objective (complete OBDK + Phase 10 + orchestration + anti-derailment);
2. avoid treating Vibe Science as the master plan;
3. correctly separate OBDK / VRE / Vibe Science responsibilities;
4. respect VRE Phase 10 hard boundaries (HB-1..HB-13);
5. give a fresh agent enough to start without chat context;
6. catalog operator decision points explicitly and minimally;
7. avoid hidden zones morte (artifacts without indexing, provenance, or memory);
8. attach tests/checks to implementation surfaces;
9. avoid research-grade biological analysis when it should be completing tooling;
10. avoid unfilled stubs, vague actions, or unbounded tasks.

## Files To Review

Required reading for the reviewer:

1. `README.md`
2. `23_project_goal_and_implementation_doctrine.md`
3. `00_INDEX.md`
4. `01_canonical_state_audit.md`
5. `02_purpose_anchor.md`
6. `03_target_architecture.md`
7. `04_master_sequence.md`
8. `05_decision_boundaries.md`
9. `06_multi_agent_pairing.md`
10. `07_anti_derailment.md`
11. `08_wave_0_preflight.md` through `15_wave_g_validation_handoff.md` (8 wave files)
12. `16_atomic_task_backlog.md`
13. `17_test_strategy.md`
14. `18_recovery_protocol.md`
15. `19_operator_decision_register.md`
16. `21_handoff_card.md`

Optional comparison:

- Sibling Codex plan at `vibe-science/blueprints/private/integrated-agentic-research-system-plan/`.

## Required Review Questions

For each question below, the reviewer answers Yes / No / Partial with citation:

1. Does the plan preserve the operator's stated objective (Complete OBDK + Phase 10 + orchestration + anti-derailment + return to VRE)?
2. Does the plan avoid treating Vibe Science as the master plan?
3. Does the plan correctly separate OBDK, VRE, and Vibe Science responsibilities?
4. Are VRE Phase 10 hard boundaries (HB-1..HB-13) respected?
5. Are OBDK completion tasks concrete enough to execute (not "improve OBDK" but specific contracts/CLI/recipes)?
6. Does the plan give a fresh agent enough to start without chat context (6-file recovery path including the GOAL doctrine)?
7. Are operator decision points explicit and minimal (the declared categories)?
8. Are there hidden zones morte (artifacts created without indexing, provenance, or memory)?
9. Are tests/checks attached to implementation surfaces (per-wave test specs in `17_test_strategy.md`)?
10. Does any wave perform research-grade biological analysis when it should be completing tooling?
11. Does the plan contain unfilled stubs, vague actions, or unbounded tasks?
12. Is the wave sequence correct (preflight → cleanup → entrypoints → completion → orchestration → autonomy → validation)?
13. Does multi-agent pairing protocol correctly anti-self-certify?
14. Does the recovery protocol cover fresh-context, post-derailment, and partial-state?
15. Does the operator decision register list initial decisions and decision categories?
16. Does the plan enforce the orthodox execution mantra that the plan is executed word-for-word unless patched through review?
17. Does every implementation step and variation require wiki, implementation ledger, changelog, README, and GitHub push evidence?
18. Does every plan file, including each wave file, contain the orthodox mantra or inherit it explicitly?
19. Does `23_project_goal_and_implementation_doctrine.md` make the project understandable to a future operator with no chat history?
20. Is the GitHub push waiver procedure explicit enough to prevent silent waiver?
21. Is OBDK wiki creation assigned to a concrete wave and task?

## Finding Format

```markdown
## Finding N — [Priority] Short title

File: `path`
Section: exact heading
Severity: P0/P1/P2/P3

Issue:
<one-paragraph description>

Why this matters:
<one-paragraph rationale>

Required fix:
<concrete patch or action>
```

## Severity Definitions

- **P0**: Blocking; plan cannot be executed; immediate fix required.
- **P1**: High; significantly impedes execution; fix before relevant wave.
- **P2**: Medium; impedes quality; fix during relevant wave.
- **P3**: Low; cosmetic or future-improvement; address opportunistically.

## Allowed Verdicts

- `ACCEPT` — plan can be executed as-is.
- `ACCEPT_WITH_MINOR` — plan can be executed after non-blocking cleanup; cleanup tracked in `ledger/adversarial_reviews.md`.
- `REDIRECT` — plan has blocking issues; patch before execution; reviewer re-reviews after patches.
- `VETO` — plan violates objective or would cause systemic derailment; structural rework required.

## Reviewer Traps To Avoid

The reviewer must not:

- request publication-grade biological detail in this plan (the plan completes tooling, not research);
- propose to merge Wave C (OBDK completion) with full scientific D0 cycle;
- approve unfilled stubs or "future integration" language without artifacts and checks;
- approve deletion of historical ledgers;
- substitute the reviewer's preferred plan structure for the author's structure if both are functionally equivalent;
- ignore the multi-agent pairing protocol when reviewing (review at wave close requires the non-author agent).
- accept a wave closure that lacks the orthodox update packet, even if tests pass.

## Closure Evidence Expected After Review

After review, the implementer records in `ledger/adversarial_reviews.md`:

```
| <ISO date> | <review id> | <reviewer agent> | <scope: plan or wave> | <verdict> | <findings count + reference> |
```

The review row must also cite the wiki page, implementation ledger row, changelog row, README section, GitHub commit/push evidence, or operator waiver that proves the reviewed artifact was durably recorded.

Each review round gets its own artifact file. Initial Codex review uses `22_codex_adversarial_review.md`; later rounds use `<number>_<reviewer>_round_<N>.md`, e.g. `24_codex_adversarial_review_round_2.md`. Every round is also recorded in `ledger/adversarial_reviews.md`.

If the verdict is REDIRECT, the implementer:

1. Patches the plan to address P0/P1 findings (P2/P3 may be deferred to wave execution).
2. Re-runs verification commands as relevant.
3. Re-requests review.
4. Maximum three REDIRECT cycles per scope; on the fourth, escalate operator.

If the verdict is ACCEPT or ACCEPT_WITH_MINOR, the implementer proceeds to wave execution.

If the verdict is VETO, the implementer escalates operator and pauses execution pending operator decision.

## Cross-Plan Reconciliation

If the reviewer is reviewing this Claude plan and a sibling Codex plan also exists:

- The reviewer notes structural differences (granularity, file count, focus).
- The reviewer does NOT pick a winner; that is operator decision.
- The reviewer flags any contradictions between the two plans as P1 findings.

The operator decides reconciliation per `19_operator_decision_register.md` OPDEC-PLAN-001.

## Sample First Review Outcome (expected for v1 of this plan)

The reviewer is expected to find:

- 0 P0 (no blocking issues; plan is execution-ready)
- 0-2 P1 (structural concerns; possibly multi-agent pairing requires more concrete handoff samples)
- 3-5 P2 (concrete improvements; e.g. Wave C effort estimate refinement, recipe priority clarity, test implementation timing)
- 5-10 P3 (cosmetic; e.g. cross-platform command syntax, Mermaid graph polish, terminology consistency)

Verdict: most likely `ACCEPT_WITH_MINOR`. Reviewer is encouraged to challenge this expectation with empirical findings.
