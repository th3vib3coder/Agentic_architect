# Decision Boundaries
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Define exactly which decisions the agent makes autonomously and which decisions require operator. The matrix is the single source of truth for escalation behavior.

## Operator Decision Categories

The operator must be asked before any of these:

1. **Objective change**: any change to the immutable objective in `02_purpose_anchor.md`.
2. **Scope change**: any addition or removal of waves; any change to a wave's allowed write set.
3. **Irreversible state change**: deletion of files, rewriting of append-only ledgers, force-pushing to public remotes.
4. **Public/private boundary change**: enabling public export, sharing claim-edge to external systems, publishing wiki pages.
5. **Claim status promotion**: promoting any claim from proposed to claimed in VRE; promoting any pathway-record assertion from supposition to claimed.
6. **External cost or compute**: paid API calls, cloud compute beyond local, long-running unattended jobs.
7. **Gate relaxation**: relaxing R2 review, LAW 9 confounder harness, LAW 13 provenance, or any HB-1..HB-13 hard boundary.
8. **GitHub push waiver**: any permission to close a task, variation, or wave without pushing reviewed work to GitHub.

If a task does not fall into any declared operator category, the agent proceeds autonomously after pre-action check passes.

## Pre-Action Check (mandatory before non-trivial action)

The agent answers internally:

1. Which active wave permits this action? Cite file + section.
2. Which file will record the result? Cite path.
3. Which command or test will prove the action worked? Cite command.
4. Does this action change system tooling or biological research scope? If biological research scope: STOP — needs operator.
5. Does this action fall in any declared operator decision category? If yes: STOP — escalate.

If any answer is unclear, the agent reads the active wave file. If still unclear, the agent asks the operator.

## Decision Matrix

| Decision | Agent autonomy | Operator required | Notes |
|---|---|---|---|
| Read any file | yes | no | Always allowed |
| Run validation command (pytest, ruff, obdk validate, node check) | yes | no | Read-only execution |
| Create file in active wave's allowed write set | yes | no | Must update index in same commit |
| Modify existing file in active wave's allowed write set | yes | no | Must preserve append-only history |
| Append row to ledger | yes | no | Must follow ledger schema |
| Select existing registered script for execution | yes | no | Cite script registry entry |
| Instantiate script template within declared recipe bounds | yes | no | Register parameters |
| Generate new script for non-claim exploratory analysis | yes (with sandbox + tests) | no | Unless external cost/compute is high |
| Run smoke-test recipe end-to-end | yes | no | Output marked archive only |
| Build review packet from run artifacts | yes | no | Vibe Science discipline |
| Trigger R2 review request | yes | no | Review packet must be complete |
| Mark claim as proposed | yes | no | Default state |
| Promote claim from proposed to claimed | no | yes | Operator decision; requires R2 ACCEPT and Vibe rigor pass |
| Generate new script whose output may support a claim | partial | yes (before claim promotion) | Generated script may run; claim promotion requires operator |
| Change research objective | no | yes | Must be recorded in `ledger/operator_decisions.md` |
| Relax R2/LAW 9/LAW 13 gate | no | yes | Operator decision with explicit rationale |
| Enable public export | no | yes | Operator decision; routed through VRE export |
| Make external paid API call | no | yes | Cost class threshold defined per wave |
| Long-running unattended compute | no | yes | Threshold: > 1 CPU-hour or > 1 GB transfer |
| Delete file | no | yes (with explicit operator decision row) | Append-only correction preferred |
| Force-push or rewrite git history | no | yes | Almost never authorized |
| Move plan files between subsystems | no | yes | Affects coordination plane |
| Change Phase 10 hard boundary | no | yes | Phase 10 spec is canonical |
| Change OBDK contract scope beyond active wave | no | yes | Recorded in OBDK `operator_decisions.md` |
| GitHub push waiver (no-push permission) | no | yes | Recorded in `ledger/operator_decisions.md` as `OPDEC-<wave>-<seq>-no-push-waiver`; scope must be per-task or per-wave; expiration must be explicit |

## Escalation Procedure

When the agent identifies an action requires operator, it:

1. Stops the action.
2. Writes a row to `19_operator_decision_register.md` describing the decision needed (one-line summary + reference to active wave + proposed options).
3. If the decision blocks the active wave, updates `ledger/active_wave.md` with `blocked_by: <decision_id>`.
4. Reports the blocking decision to the operator in chat (if interactive) or in the closure report (if unattended).
5. Resumes only after operator records decision in `ledger/operator_decisions.md`.

## Operator Decision Recording

When the operator returns and makes a decision, the format in `ledger/operator_decisions.md` is:

```
| <ISO date> | <decision id> | <decision> | <rationale> | <scope> |
```

Decision IDs follow the pattern `OPDEC-<wave>-<sequence>-<short-name>`, e.g. `OPDEC-A-001-cluster-d-v0-1-defer`.

## GitHub Push Waiver Procedure

A failed or unavailable `git push` is not a waiver. When a push cannot be completed:

1. The agent stops the closure action.
2. The agent writes a decision request in `19_operator_decision_register.md` with id `OPDEC-<wave>-<sequence>-no-push-waiver`.
3. The request states the exact reason, affected task or wave, local commit SHA if available, remote/branch attempted, and proposed expiration.
4. The operator either approves or denies the waiver in `ledger/operator_decisions.md`.
5. If approved, the changelog row records `commit_local_only_via_waiver: <opdec-id>`.
6. If denied, the wave remains open until push succeeds.

## Failure Mode: Agent Acts Without Operator

If the agent acts on an operator-required decision without operator approval, this is a governance failure. The recovery procedure:

1. Stop the action immediately if not yet completed.
2. If completed and reversible: revert via append-only correction.
3. If completed and irreversible: write a row to `ledger/derailment_log.md` with pattern P5 (operator correction ignored), describe the action and its effect, request operator review.
4. The agent must not proceed with new actions until the operator reviews the failure.

## Empowerment Statement

Asking the operator at the declared categories is correct behavior. The desired autonomy is not silence; it is execution of the plan with escalation only at decision points. An agent that proceeds at a decision point without asking has failed governance. An agent that asks at every decision has failed productivity. The matrix above defines the line.
