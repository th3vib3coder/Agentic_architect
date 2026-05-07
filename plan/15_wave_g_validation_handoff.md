# Wave G — Validation, Absorption, Handoff
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Prove the integrated system is complete, documented, recoverable, and ready for routine agent use. Wave G runs final validation, captures absorbability verdict, produces handoff card, and closes the project.

## Pre-conditions

Wave F closed (`ledger/active_wave.md` shows `active_wave: G`).

## Allowed Write Set

Wave G may write to:

- `Agentic_architect/ledger/`, `Agentic_architect/reports/`, `Agentic_architect/plan/`, plus `Agentic_architect/plan/21_handoff_card.md`
- repository-level handoff document (operator decision on path)

Wave G does NOT:

- modify any subsystem (OBDK, VRE, Phase 10, Phase 9, Vibe Science) other than recording closure rows in their ledgers;
- modify sibling Codex plan;
- delete or rewrite any append-only ledger.

## Final Validation Matrix

| Area | Required Evidence |
|---|---|
| OBDK | tests pass, contracts validate, recipes run, paper/method/script paths work |
| VRE Phase 10 | LAW 13 lint passes, query works, R2 binding blocks unauthorized claims |
| Vibe Science | review packets persist, assumptions/claims/seeds are not lost |
| Orchestration | source-to-evidence trace query works |
| Fresh agent | follows `21_handoff_card.md` successfully |
| Anti-derailment | derailment log and purpose anchor are active and tested |

## Atomic Tasks

### Task G1 — Full validation run

Run all available validations:

```
cd vibe-science/blueprints/private/onco-bio-discovery-kernel
python -m pytest --tb=short -q
python -m ruff check .
python -m obdk.cli contracts validate --charter charter-v0.5.md
```

Run WIKI_VRE validations:

```
node vibe-science/blueprints/private/WIKI_VRE/tools/build-registries.mjs --check
node vibe-science/blueprints/private/WIKI_VRE/tools/sync-mirror.mjs --check
```

- [ ] Record exact output in `reports/final_validation.md`.
- [ ] If any validation fails, document deviation and route to operator decision (G6) for accept-with-deviation or fix.

### Task G2 — Fresh-agent drill

Start from a new session prompt using only the repository root and `Agentic_architect/plan/README.md`:

- [ ] Identify active objective.
- [ ] Find OBDK.
- [ ] Find VRE memory.
- [ ] Ingest or locate a paper.
- [ ] Identify method extraction path.
- [ ] Identify script routing path.
- [ ] Identify review/persistence path.
- [ ] Name operator decision points.
- [ ] Record agent narrative in `reports/wave_g_fresh_agent_drill.md`.

If the agent cannot do any of these without operator hints, the corresponding plan file is patched and the drill re-runs.

### Task G3 — Absorbability verdict

Write `reports/absorbability_verdict.md` with verdict from this set:

- `ABSORBABLE` — system is complete, can be promoted to VRE proper / production
- `ABSORBABLE_WITH_DEFERRED_TRIGGERS` — system works but specific triggers list deferred items
- `NOT_ABSORBABLE` — system has blocking gaps; specific gaps listed

Required sections:

- [ ] Evidence (links to G1 final validation and G2 fresh-agent drill).
- [ ] Unmet conditions (if any).
- [ ] Deferred triggers (e.g. Cluster E LLM contracts, Cluster F predictive contracts).
- [ ] Operator decision needed (binary: accept verdict or run another wave).
- [ ] Adversarial review packet link.

### Task G4 — Handoff card

Write or finalize `21_handoff_card.md` at this plan root with:

- [ ] What the system is.
- [ ] How to start (first 10 moves for a new agent).
- [ ] How to run common workflows (ingest paper, run recipe, query VRE, trigger R2 review).
- [ ] How to recover (link to `18_recovery_protocol.md`).
- [ ] How to review (link to `20_adversarial_review_packet.md`).
- [ ] How to stop safely (close active wave, persist state, clear `ledger/active_subtasks.md`).

### Task G5 — Adversarial review (final)

Use `20_adversarial_review_packet.md` to request final adversarial review by the non-author agent (Codex if Claude wrote, Claude if Codex wrote).

Required verdict:

- `ACCEPT` — closes the project
- `REDIRECT` — findings to fix; project remains open
- `VETO` — architecture violates purpose; project requires structural rework

If REDIRECT, address findings and re-request review. Maximum three REDIRECT cycles.

### Task G6 — Operator closure

Operator records:

- [ ] Final verdict (consume G3 absorbability verdict).
- [ ] Accepted deferred triggers (operator confirms which deferrals are acceptable).
- [ ] Public/private boundary (operator decides whether the integrated system is ready for non-private use).
- [ ] Next real research objective or maintenance mode.

Closure row in `ledger/operator_decisions.md`:

```
| <ISO date> | OPDEC-G-001-final-closure | <ABSORBABLE | ABSORBABLE_WITH_DEFERRED_TRIGGERS | NOT_ABSORBABLE> | <rationale> | project closure |
```

### Task G7 — Plan archive and reconciliation

If both this plan and sibling Codex plan exist at this point:

- [ ] Reconcile: operator decides which becomes canonical, or merge into a single canonical plan.
- [ ] Move loser to `_archive/<plan-name>/` with README explaining the archive.
- [ ] Update repository-root reference to point at the canonical plan.

### Task G8 — Final ledger row

- [ ] Append final row to `ledger/change_log.md`:
  ```
  | <ISO date> | INTPLAN-G-001 | reports/final_validation.md, reports/absorbability_verdict.md, 21_handoff_card.md, ledger/operator_decisions.md | wave G: validation + verdict + handoff + closure | closed |
  ```
- [ ] Update `ledger/active_wave.md`:
  ```
  active_wave: closed
  since: <ISO date>
  last_updated_by: <agent>
  last_updated_reason: project closed via operator decision OPDEC-G-001-final-closure
  ```

## Closure Criteria

The whole project closes when:

- final validation passes or deviations are accepted by operator;
- adversarial review ACCEPT;
- operator closure recorded in `ledger/operator_decisions.md`;
- `21_handoff_card.md` complete and validated by fresh-agent drill;
- this plan and sibling Codex plan reconciled or one archived;
- `ledger/active_wave.md` shows `active_wave: closed`.

## Stop Conditions

Wave G stops and operator is asked if:

- final validation reveals breakage in OBDK/VRE/Vibe (this should not happen if previous waves closed correctly; if it does, escalate);
- fresh-agent drill fails because a critical entrypoint is missing (return to Wave B);
- absorbability verdict is `NOT_ABSORBABLE` and operator must decide next steps;
- adversarial review issues VETO (rare; requires architectural rework);
- this plan and sibling Codex plan diverge irreconcilably and operator must decide which wins.

## Outputs

After Wave G closure:

- `reports/final_validation.md` with all command outputs
- `reports/wave_g_fresh_agent_drill.md` with agent narrative
- `reports/absorbability_verdict.md` with verdict and rationale
- `21_handoff_card.md` finalized
- adversarial review record in `ledger/adversarial_reviews.md`
- operator closure row in `ledger/operator_decisions.md`
- `ledger/active_wave.md` shows closed
- Optional: archived sibling plan in `_archive/`
