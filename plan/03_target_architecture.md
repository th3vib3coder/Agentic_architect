# Target Architecture
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Define the final state of the integrated system after wave G closes. A fresh agent reads this file to understand how OBDK, VRE, and Vibe Science cooperate and where each artifact goes.

## One-Sentence System Contract

Given a research problem and optional papers or datasets, the agent uses VRE to recover memory, Vibe Science to enforce rigor, and OBDK to ingest sources, extract methods, route or generate scripts, execute analyses, validate evidence, and persist everything for future sessions.

## Three-Layer Architecture

```
+----------------------------+
| Operator Surface           |  Operator decisions, escalations, objective steering
+----------------------------+
            |
            v
+----------------------------+
| Coordination Control Plane |  This plan + sibling Codex plan, ledgers, decision register
+----------------------------+
            |
   +--------+--------+
   v        v        v
+-----+ +------+ +-------+
| OBDK| | VRE  | | Vibe  |   Three subsystems with bounded responsibilities
+-----+ +------+ +-------+
   ^        ^        ^
   |        |        |
   +--------+--------+
            |
            v
+----------------------------+
| Agent Runtime (Claude/Codex/...) |  Reads coordination plane, invokes subsystems, persists outputs
+----------------------------+
```

## Subsystem Responsibility Boundaries

| Subsystem | Owns | Does Not Own |
|---|---|---|
| OBDK | analysis execution, paper ingestion, method extraction, script routing/generation, recipe library, evidence-package emission, contract enforcement at run time | long-term memory, R2 review verdict, claim promotion, wiki provenance |
| VRE | long-term memory, source bundle storage, wiki compile and query, provenance enforcement (LAW 13), claim ledger persistence, objective management, operator steering events | execution of analysis, contract validation, scientific rigor decisions |
| Vibe Science | rigor enforcement, R2 review, LAW 9 confounder harness, Salvagente seed creation, claim status decisions, anti-derailment governance | data ingestion, analysis execution, long-term storage |

## Knowledge Graph (cross-subsystem)

The integrated system is a single knowledge graph with edges typed by ownership:

```
[Source Bundle (VRE)]
      |
      | extract-methods
      v
[Method Record (OBDK)] ----+
      |                    |
      | route or generate  | route to existing
      v                    v
[Script Record (OBDK)]  [Registered Script (OBDK)]
      |                    |
      |   recipe binds     |
      v                    v
[Recipe (OBDK)] ---> [Run Manifest (OBDK)]
                            |
                            | produces
                            v
                     [Evidence Package (OBDK)]
                            |
                            | review packet
                            v
                     [R2 Review (Vibe)]
                            |
                            v
                     [Claim Status (Vibe + VRE)]
                            |
                            | persist
                            v
                     [VRE Wiki Page (VRE)]
                            |
                            | back-links
                            v
                     [Source Bundle, Method, Script, Run, Evidence] (queryable)
```

Every node carries an ID matching the format declared in `13_wave_e_orchestration.md` Task E1.

## Agent Startup Flow

A fresh agent starts at the repository root and follows this exact sequence:

1. Read `Agentic_architect/README.md`
2. Read `Agentic_architect/plan/23_project_goal_and_implementation_doctrine.md`
3. Read `Agentic_architect/plan/00_INDEX.md`
4. Read `Agentic_architect/plan/01_canonical_state_audit.md`
5. Read `Agentic_architect/plan/04_master_sequence.md`
6. Identify active wave from `Agentic_architect/ledger/active_wave.md` (if exists) else default Wave 0
7. Read the active wave file
8. Query VRE for current objective via `node WIKI_VRE/tools/build-registries.mjs --check` and reading `WIKI_VRE/index.md`
9. If active wave is execution wave (A-G), read the test strategy section in `17_test_strategy.md` for that wave
10. Execute one atomic task from `16_atomic_task_backlog.md` for the active wave

If at any step the file is missing, the agent stops and asks the operator.

## Data and Evidence Lifecycle

| Stage | Input | Output | Persistent Home |
|---|---|---|---|
| Source intake | PDF, supplement, dataset accession, operator note | source bundle + metadata | VRE raw/source store |
| Method extraction | source bundle | method/procedure records | VRE wiki + OBDK method registry |
| Procedure mapping | method records | script routing decision | OBDK script registry + VRE decision page |
| Execution | recipe + scripts + data | run artifacts | OBDK run directory + VRE computed artifact page |
| Review | run artifacts and claims | R2 verdict, limitations, kill/downgrade/promote | Vibe Science + VRE review records |
| Promotion | claim + R2 verdict | VRE claim/evidence entry, claim-ledger row | VRE memory + optional external export |

## Script Routing Decision Tree

When the agent maps a method record to executable code:

1. Does the procedure exactly match a registered OBDK or SPARK-derived script? Yes → use registered script and cite registry entry.
2. Does the procedure match a script template with parameter differences only? Yes → instantiate template, register parameters, run tests.
3. Is the procedure supported by existing OBDK primitives? Yes → compose new recipe, register recipe, smoke-test.
4. None of the above → generate new script in sandbox:
   - write test fixture first
   - generate script via LLM (governed by Cluster E LLM contracts when available; manual review otherwise)
   - run test on minimal fixture
   - register generated script with provenance, dependencies, limitations
   - mark `generated_pending_review` until R2 review

The decision tree itself is canonical and is exercised in Wave F autonomous runtime.

## Decision Escalation Matrix (full list in `05_decision_boundaries.md`)

| Decision | Agent autonomy | Operator required |
|---|---|---|
| Select existing registered script | autonomous | no |
| Instantiate script template within recipe bounds | autonomous | no |
| Generate new script for non-claim exploratory analysis | autonomous with sandbox + tests | no, unless external cost/compute is high |
| Generate new script whose output supports a claim | partial | yes before claim promotion |
| Change research objective | no | yes |
| Relax provenance/R2/confounder gate | no | yes |
| Public export | no | yes |
| Delete or rewrite append-only ledgers | no | yes (append-only correction preferred) |

## Recovery Properties

The system is fresh-context resilient: a new agent starting from zero can recover by reading at most these six files:

1. `README.md`
2. `23_project_goal_and_implementation_doctrine.md`
3. `00_INDEX.md`
4. `01_canonical_state_audit.md`
5. `04_master_sequence.md`
6. `18_recovery_protocol.md`

After the six recovery reads, including `23_project_goal_and_implementation_doctrine.md`, the agent knows what exists, what to do, and where to write outputs.

## Completion Definition

The architecture is complete when all of these are true (verified by `17_test_strategy.md` Wave G tests):

1. A fresh agent can find and follow `21_handoff_card.md` from the repository root.
2. OBDK exposes a `SKILL.md` wrapper at `vibe-science/blueprints/private/onco-bio-discovery-kernel/SKILL.md`.
3. VRE Phase 10 source/wiki/provenance/query/R2 layer is implemented and validated.
4. OBDK can ingest at least one paper, extract methods, and map methods to scripts.
5. OBDK runs at least three registered analysis recipes end-to-end.
6. At least one missing script is generated, sandbox-tested, registered, executed, and reviewed.
7. Vibe Science review events are persisted and queryable from VRE.
8. VRE answers "what did we do, why, with which source, which script, which run, and which verdict?"
9. All major surfaces have recovery docs and validation commands.
10. Both this plan and sibling Codex plan are reconciled or archived.
11. Adversarial review by the non-author agent (Codex for this plan, Claude for sibling) issues ACCEPT.
12. Operator closure is recorded in `ledger/operator_decisions.md`.
