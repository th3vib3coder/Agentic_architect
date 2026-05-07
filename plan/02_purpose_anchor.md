# Purpose Anchor
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Why this file exists

Past sessions exhibited five derailment patterns (P1-P5) where the agent replaced the written plan with improvised research-grade workflows, framework-driven side quests, smoke-test theater, "minimum viable" shortcuts, and ignored operator corrections. This file is the immutable purpose statement that an agent must read before any non-trivial action and that overrides framework-derived improvisation.

## Immutable Objective

The integrated agentic research system being built is a **tool**, not a research project. Its purpose is to enable autonomous research workflows by:

1. preserving long-term memory in VRE (sources, methods, runs, decisions, claims, reviews);
2. enforcing rigor through Vibe Science (R2 review, LAW 9 confounder harness, Salvagente Rule, claim ledger discipline);
3. executing analyses through OBDK and SPARK-derived scripts (paper ingestion, method extraction, script routing or generation, evidence packaging);
4. recovering in future sessions without operator path hints;
5. asking the operator only on the declared decision categories listed in `05_decision_boundaries.md`.

The objective is complete when a fresh agent can ingest a paper, route or generate a script, execute the analysis, persist evidence to VRE, and trigger review without operator path hints — and recover identically on a future fresh session.

## Immutable Non-Objective

Until the operator explicitly says otherwise, the integrated system is NOT:

- a publication pipeline for biological research claims;
- a place to optimize confounder harnesses, GSVA parameters, cohort metadata, or other research-grade scientific discipline beyond what the active wave declares;
- a framework where Vibe Science replaces the written plan;
- a setting where smoke-test on fixture is called full data execution;
- a context where chat memory overrides filesystem state;
- a domain where shortcuts skip written tasks because they "feel faster".

If an agent feels tempted to do any of the above, the agent has hit a derailment pattern. Read `07_anti_derailment.md` and return to the active wave.

## Orthodox Execution Contract

The plan is the authoritative operating text:

> Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.

The sentence is intentionally blunt. It prevents the recurring failure mode where an agent treats the plan as inspiration and substitutes a faster, smarter-looking, or more research-grade path. The correct behavior is:

1. read the active wave;
2. execute the next atomic task exactly as written;
3. if a variation is needed, patch the plan first and send the patch through adversarial review;
4. record the result in durable project memory.

Every implementation step and every variation, including one-line documentation edits, carries the same mandatory evidence packet:

- project wiki update;
- implementation ledger row;
- incremental changelog row naming every edited file and why;
- relevant README update describing the implemented change;
- GitHub commit and push after review closure.

If a wave has not yet created the wiki, ledgers, README surface, or GitHub remote needed for this packet, the active task must create or locate those surfaces before implementation proceeds. Missing evidence surfaces are blockers, not excuses.

## Decision Authority Stack

When two surfaces disagree about what to do, the higher-rank surface wins:

| Rank | Surface | Authority Domain |
|---|---|---|
| 1 | Operator instruction in current session | Highest only for current turn; must be crystallized to file before durable effect |
| 2 | Append-only ledgers (`ledger/operator_decisions.md`, `ledger/adversarial_reviews.md` in this plan + same files in OBDK and VRE) | Past operator and reviewer decisions |
| 3 | This plan and sibling Codex plan (coordination control plane) | What waves to execute and in what order |
| 4 | Subsystem canonical control planes (OBDK `analisi_claude/project_plan`, WIKI_VRE `index.md`, Phase 10 spec) | Within-subsystem rules |
| 5 | Contracts and tests | Executable truth at runtime |
| 6 | Chat memory | Non-authoritative; suggest where to look but cannot decide |

## Pattern Recognition

The five derailment patterns from past sessions:

| ID | Pattern | Trigger | Correction |
|---|---|---|---|
| P1 | Framework capture | Vibe Science framework taken literally → applied to research-grade discipline outside the active wave scope | Read this file, return to active wave file |
| P2 | "Minimum viable" shortcut proposed bypassing the plan | Agent feels the plan is too long and proposes faster alternative | Execute the plan or patch the plan with review; do not bypass |
| P3 | Smoke-test artifact mistaken for real data-touching | Fixture run is called "we touched data" | State exact source path, command, and scope; smoke-test on fixture is not real data |
| P4 | Vibe Science taken as guide instead of supporto | Vibe Science becomes the master plan instead of rigor layer | Vibe Science is rigor; this plan is master |
| P5 | Ignore explicit operator correction → propose yet another way | Operator says "not this", agent proposes a third option | LAW 11: follow correction immediately, do not argue |

If any pattern is detected, stop the action, write a row to `ledger/derailment_log.md`, and either return to the active wave file or ask the operator.

## Pre-Action Check

Before any non-trivial action, the agent must answer:

1. Which active wave permits this action? (Cite file + section)
2. Which file will record the result? (Cite the path)
3. Which command or test will prove the action worked? (Cite the command)
4. Does this action change the system tooling scope or the biological research scope? (If biological research scope: STOP — needs operator)
5. Does this action require an operator decision per `05_decision_boundaries.md`? (If yes: STOP — escalate)
6. Which wiki page, ledger row, changelog row, README section, and GitHub commit/push will carry the durable evidence for this step?

If any answer is unclear, the agent reads the active wave file. If still unclear, the agent asks the operator.

## Stop Conditions (automatic)

The agent must stop and ask the operator if:

- the active wave's allowed write set is insufficient for the action;
- a required source system is missing or unreadable;
- a validation command cannot be run and no fallback evidence is possible;
- VRE Phase 10 hard boundaries (HB-1..HB-13 in `02-formal-design-spec.md`) conflict with the action;
- OBDK contract completion would require changing the scientific scope beyond what is declared in this plan;
- the agent is tempted to perform publication-grade research instead of completing the system;
- a task requires deleting or rewriting an append-only ledger;
- a proposed action changes the goal or non-goal stated in this file.

## Operator Questions Are Not Failure

Asking the operator at the declared decision categories is correct behavior. The desired autonomy is not silence; it is execution of the plan with escalation only at decision points. An agent that proceeds at a decision point without asking has failed governance.

## Test-Enforced Anchoring

`17_test_strategy.md` defines tests that verify this purpose anchor file exists, contains the immutable objective, contains the five derailment patterns, and is referenced from `00_INDEX.md` and `21_handoff_card.md`. Wave G validation runs these tests; the system is not absorbable until they pass.
