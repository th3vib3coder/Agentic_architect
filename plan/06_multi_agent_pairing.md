# Multi-Agent Pairing Protocol
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Define how Codex (implementer-favored), Claude (reviewer-favored), and operator (Carmine) cooperate per wave. The protocol prevents both same-agent self-certification and ad-hoc role swapping.

## Role Defaults

| Role | Default agent | Authority |
|---|---|---|
| Implementer | Codex | Writes code, contracts, tests, recipes; runs validations |
| Reviewer | Claude | Adversarial review of implementer output; byte-for-byte audit; mutation testing |
| Operator | Carmine | Records decisions, sets objective, closes waves |

Role swapping (Claude as implementer, Codex as reviewer) is allowed when:

- the operator explicitly authorizes the swap in `ledger/operator_decisions.md`;
- both agents are present in adjacent sessions;
- the swap is recorded in `ledger/multi_agent_pairing.md`.

## Per-Wave Role Assignment

| Wave | Implementer | Reviewer | Operator decisions required |
|---|---|---|---|
| 0 | either | either | none (preflight is verification-only) |
| A | Codex | Claude | Cluster D v0.1 closure or deferral |
| B | Codex | Claude | none unless SKILL.md content changes scope |
| C | Codex (heavy lift) | Claude (multi-task review) | TCGA-OV inclusion (if relevant); recipe priority |
| D | Codex (gated on Phase 9 Wave 5) | Claude | Phase 10 implementation track GO (HB-1) |
| E | Codex | Claude | none unless cross-system bridge changes scope |
| F | Codex | Claude | autonomy threshold (cost/compute/runtime) |
| G | Codex (test runs) | Claude (final adversarial) | absorbability verdict, handoff approval |

## Anti-Self-Certification Rule

The implementer of an artifact must not issue ACCEPT on their own work. ACCEPT verdicts require:

- a different agent than the implementer issuing the verdict;
- empirical re-verification commands run by the reviewer in the reviewer's own session;
- byte-for-byte audit when the artifact is a contract, schema, or hard-boundary specification;
- mutation testing when the artifact contains validators or invariants.

If only one agent is available, the operator can authorize a same-session pseudo-pairing where the implementer writes, then explicitly switches to reviewer disposition with verification-before-completion discipline. This is recorded as `pseudo_pairing` in `ledger/multi_agent_pairing.md` and the verdict is non-blocking until a real second-agent review is performed.

## Handoff Format

When implementer hands off to reviewer:

```markdown
## Implementer Handoff: <wave>:<task>

Status: VERIFIED BY AUTHOR
Implementer: <agent>
Verification commands run:
  - <command 1>: <result>
  - <command 2>: <result>
Files changed:
  - <path>:<description>
Orthodox update packet:
  - Wiki updated: <path or waiver ref>
  - Implementation ledger row: <path/row id>
  - Incremental changelog row: <path/row id>
  - README updated: <path/section>
  - GitHub pushed: <remote/branch/commit> OR waiver ref
Known limitations:
  - <limitation>
Pending operator decisions:
  - <decision id from 19_operator_decision_register.md>
Reviewer requested: yes
```

When reviewer responds:

```markdown
## Reviewer Verdict: <wave>:<task>

Reviewer: <agent>
Disposition: adversarial / R2 hard
Verdict: ACCEPT / ACCEPT_WITH_MINOR / REDIRECT / VETO
Findings: <list with file:line references>
Verification commands re-run by reviewer:
  - <command 1>: <result>
Mutation tests (if applicable):
  - <mutation>: <expected fail or expected pass> -> <observed>
Orthodox packet audit:
  - Wiki/ledger/changelog/README/GitHub evidence present: yes/no
Recommendation: <next step>
```

Handoffs are recorded in `ledger/multi_agent_pairing.md` with one row per handoff:

```
| <ISO date> | <wave>:<task> | <implementer> | <reviewer> | <verdict> | <evidence ref> |
```

## REDIRECT Rule

When reviewer issues REDIRECT, the implementer:

1. Reads the findings.
2. Patches the artifact to address P0/P1/P2 findings.
3. Re-runs the verification commands.
4. Hands off again with patches noted in the handoff format.
5. Reviewer re-reviews and either ACCEPTs (with or without minor findings) or VETOs (rare; only if architecture violates the objective).

A REDIRECT must not be ignored. Maximum three REDIRECT cycles per task; on the fourth REDIRECT, the operator is escalated.

## Orthodox Packet Review Rule

The reviewer treats missing wiki, ledger, changelog, README, or GitHub evidence as a review finding even when the code or document content is otherwise correct. Severity:

- P1 if the missing evidence hides a system behavior change, operator decision, public/private boundary, or autonomous-agent capability.
- P2 if the missing evidence affects documentation-only work.
- P3 only for formatting drift inside an otherwise complete evidence packet.

## Same-Wave Multi-Agent Coordination

When two agents work on the same wave concurrently:

- Each agent claims a sub-task by writing a row to `ledger/active_subtasks.md` with `start_timestamp` and `agent`.
- Agents must not write to the same file in the same commit.
- Conflict resolution: if two agents target the same file, the agent that claimed first proceeds; the other waits or picks a different sub-task.
- Synchronization point: every wave has a sequential gate task (e.g. A5, B5, C10, D8, E6, F6, G6) that must be executed by a single agent after all parallel sub-tasks close.

## Operator Steering

The operator can:

- pause the active wave (sets `ledger/active_wave.md` `paused: true`);
- swap roles (records in `ledger/multi_agent_pairing.md`);
- change implementer mid-wave (rare; operator decision row required);
- request adversarial review at any time (review packet built from current state);
- close a wave manually if validation evidence is acceptable.

Operator steering is recorded in `ledger/operator_decisions.md`.

## Multi-Agent Drift Protection

If two agents produce divergent artifacts in the same wave (e.g. both wrote a `SKILL.md`):

1. The conflict is logged in `ledger/multi_agent_pairing.md` with `conflict: true`.
2. Both versions are preserved (one renamed to `<artifact>.alternate.md`).
3. Operator decides which version becomes canonical.
4. The losing version is moved to `_archive_drift/<date>/<artifact>.md`.

Drift detection is automated by `17_test_strategy.md` Wave G tests that compare expected single-source-of-truth files against actual filesystem.

## Vibe Science As Reviewer Discipline Source

When Claude or Codex acts as reviewer, the disposition draws from Vibe Science discipline:

- R2 ensemble protocol: 4 reviewer modes (specificity, counter-evidence search, confounder analysis, falsification demand);
- LAW 9 confounder harness check on quantitative claims;
- Salvagente Rule on killed claims;
- Schema-validated gates on contracts;
- Skepticism Policy on imported papers and methods.

The reviewer cites the Vibe discipline used in the verdict (e.g. "applied Vibe R2 specificity + counter-evidence search").
