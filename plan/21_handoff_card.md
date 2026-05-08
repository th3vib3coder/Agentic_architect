# Handoff Card — Post-Completion Operational Guide
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

The compact operational card for an agent using the integrated system during implementation and after Wave G closes. A new agent reads this file and is ready to recover state, find the active wave, and avoid calling future commands before their wave closes.

## What This System Is

An integrated agentic research system composed of three subsystems:

- **OBDK** (Onco Bio Discovery Kernel) — analysis kernel; ingests papers, extracts methods, routes or generates scripts, runs analyses, emits evidence packages.
- **VRE** (Vibe Research Environment) — long-term memory; stores sources, methods, runs, decisions, claims, reviews; queryable across sessions.
- **Vibe Science** — rigor and governance; R2 review, LAW 9 confounder harness, LAW 13 provenance, Salvagente Rule, claim ledger, anti-derailment discipline.

The three subsystems are wired so an agent ingests a paper, executes analyses, persists evidence, triggers review, and recovers in future sessions — all without operator path hints, escalating only at the declared decision categories.

## What This System Is Not

- It is not a single biological analysis project.
- It is not a publication pipeline (until operator explicitly sets a publication objective).
- It is not a place to improvise around the written plan or this card.
- It is not allowed to treat chat memory as authority.

## Two Operating Mantras

1. **Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**
2. **For every implementation step and every minimal variation:** update the wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote. Missing durable evidence means the step is not complete.

## First Ten Moves For A Fresh Agent

1. Read `Agentic_architect/README.md`, then `Agentic_architect/wiki/index.md`.
2. Read `Agentic_architect/ledger/active_wave.md`.
3. Read `Agentic_architect/plan/23_project_goal_and_implementation_doctrine.md`.
4. Read `Agentic_architect/plan/00_INDEX.md`.
5. Read `Agentic_architect/plan/02_purpose_anchor.md`.
6. Read `Agentic_architect/plan/04_master_sequence.md`.
7. Read the active wave file named by `ledger/active_wave.md`.
8. Locate OBDK at `vibe-science/blueprints/private/onco-bio-discovery-kernel` and read `SKILL.md`.
9. Locate VRE at `vibe-science/blueprints/private/WIKI_VRE` and read `index.md`.
10. Read `Agentic_architect/plan/system_orchestration_map.md` and identify operator escalation points in `05_decision_boundaries.md`.

After these ten moves, the agent knows: what the system is, where each subsystem is, what the active wave is, and what to do next.

## How To Choose A Tool

| Need | Use |
|---|---|
| Recover past sources, methods, decisions, claims | VRE / WIKI_VRE |
| Ingest paper or store source with provenance | VRE Phase 10 source layer + OBDK paper-ingest CLI after Wave C/D closure |
| Extract methods and map to executable procedures | OBDK extract-methods CLI + script registry after Wave C closure |
| Run omics analysis, recipe, scorer | OBDK CLI (`obdk run`) |
| Generate missing script | OBDK `generate-script` + sandbox + Vibe review after Wave C closure |
| Review claim, assumption, negative result, uncertainty | Vibe Science R2 review packet |
| Persist evidence to long-term memory | OBDK `export-vre` + WIKI_VRE compile pipeline after Wave D/E closure |
| Ask operator | only for the declared decision categories in `05_decision_boundaries.md` |

## Common Workflows

### Workflow A: Ingest a paper and analyze its method (available after Wave C/D)

1. `python -m obdk.cli ingest-paper --pdf path/to/paper.pdf --out runs/paper_ingest/<source_id>`
2. `python -m obdk.cli extract-methods --source runs/paper_ingest/<source_id> --out runs/method_extract/<source_id>`
3. For each method record: look up script in registry. If found, instantiate recipe and run. If missing, `generate-script`.
4. `python -m obdk.cli run --recipe <recipe.yaml> --out runs/<run_id>`
5. `python -m obdk.cli export-vre --evidence-package runs/<run_id>/evidence.yaml`
6. Trigger R2 review via Vibe Science adapter.
7. Persist verdict to VRE.

Until Wave C closes, use only current OBDK commands listed in `OBDK/SKILL.md`: `contracts validate`, `contracts export-schemas`, `run`, and `harvest-geo`.

### Workflow B: Query VRE memory

1. Read `WIKI_VRE/index.md` to find existing pages.
2. Use Phase 10 query agent to ask "what did we do, why, with which source, which script, which run, and which verdict?"
3. The agent returns citation list.

### Workflow C: Recover from fresh context

1. Read the recovery path (README, wiki/index, active_wave, GOAL doctrine, INDEX, purpose anchor, master_sequence, active wave file).
2. Smoke-check subsystems via `pytest`, `obdk validate`, `node build-registries.mjs`.
3. Identify operator decisions awaiting (read `19_operator_decision_register.md`).
4. Resume active wave or escalate.

### Workflow D: Recognize and recover from derailment

1. If matching a pattern from `07_anti_derailment.md`: stop.
2. Read `02_purpose_anchor.md` and active wave file.
3. Mark any artifacts created during derailment as experimental.
4. Write derailment row in `ledger/derailment_log.md`.
5. Escalate operator if needed; otherwise resume active wave.

## How To Stop Safely

When ending a session:

1. Update `ledger/active_subtasks.md`: mark in-progress tasks as `paused` with timestamp.
2. Update `ledger/active_wave.md`: ensure pointer is correct.
3. Append session summary to `ledger/change_log.md`.
4. Verify wiki, ledger, changelog, README, and GitHub push evidence exists for each completed step.
5. Verify all writes are committed and pushed, or that an operator-approved no-push waiver is recorded.
6. Close the session.

## How To Review (Adversarial)

To run adversarial review on a wave:

1. Read `20_adversarial_review_packet.md`.
2. Identify the wave's required reading list.
3. Execute the review questions.
4. Issue verdict (ACCEPT, ACCEPT_WITH_MINOR, REDIRECT, VETO).
5. Record in `ledger/adversarial_reviews.md`.

## Operator Decisions (when to ask)

Ask the operator only for these declared categories:

1. Objective change.
2. Scope change.
3. Irreversible state change (file deletion, ledger rewrite).
4. Public/private boundary change.
5. Claim status promotion.
6. External cost or compute.
7. Gate relaxation.
8. GitHub push waiver.

For everything else, execute the plan or patch the plan via adversarial review.

## Anti-Derailment Reminders

- The plan is executed; it is not reinterpreted in chat.
- Vibe Science is rigor, not the master plan.
- Smoke-test on fixture is not real data.
- Operator correction is followed immediately, not argued.
- A shortcut that bypasses written tasks is a derailment, not productivity.

## Validation Commands (always available)

```
# OBDK
cd vibe-science/blueprints/private/onco-bio-discovery-kernel
python -m pytest --tb=short -q
python -m ruff check .
python -m obdk.cli contracts validate --charter charter-v0.5.md

# WIKI_VRE
node vibe-science/blueprints/private/WIKI_VRE/tools/build-registries.mjs --check
node vibe-science/blueprints/private/WIKI_VRE/tools/sync-mirror.mjs --check
```

## Where To Find Help

| Question | File |
|---|---|
| What is this system? | `README.md` |
| Where is everything? | `00_INDEX.md` + `01_canonical_state_audit.md` |
| What's the immutable objective? | `02_purpose_anchor.md` |
| What's the architecture? | `03_target_architecture.md` |
| What's the active wave? | `ledger/active_wave.md` + `04_master_sequence.md` |
| When do I ask the operator? | `05_decision_boundaries.md` |
| How does multi-agent pairing work? | `06_multi_agent_pairing.md` |
| What if I'm derailing? | `07_anti_derailment.md` + `18_recovery_protocol.md` |
| What's my next task? | `16_atomic_task_backlog.md` for active wave |
| How do I test? | `17_test_strategy.md` |
| What decisions await operator? | `19_operator_decision_register.md` |
| How do I review? | `20_adversarial_review_packet.md` |

## Closing Note

This card is the canonical operational reference. If anything in this card is contradicted by another file, the higher-rank surface in the authority stack (`02_purpose_anchor.md`) wins. If the contradiction cannot be resolved, escalate operator.
