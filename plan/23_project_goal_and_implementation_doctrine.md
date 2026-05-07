# Project Goal And Implementation Doctrine
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Why this file exists

This file is the durable statement of what we are building. It must remain understandable to an operator or agent who arrives weeks later with no chat history.

If any future session becomes confused, the agent reads this file before proposing a new direction. This file does not replace the wave files; it explains why the wave files exist and what final system they are building.

## The Goal

Build a coordinated agentic research system where **Vibe Science**, **VRE**, and **OBDK** work as one operational stack:

- **Vibe Science** supplies rigor: review discipline, claim discipline, falsification pressure, provenance discipline, anti-derailment checks, and structured skepticism.
- **VRE** supplies long-term memory: sources, papers, extracted methods, scripts, runs, decisions, claims, reviews, operator choices, and recovery surfaces that survive across sessions.
- **OBDK** supplies executable analysis: paper ingestion, method extraction, SPARK-derived script routing, missing-script generation, sandbox execution, omics workflows, evidence-package production, and export back to VRE.

The system is complete when a fresh agent can enter the workspace, discover the active objective without chat hints, read the correct control surfaces, ingest a paper, extract its procedures, select or create the correct scripts, execute the analysis, save all artifacts, trigger Vibe Science review, persist results into VRE memory, and ask the operator only at declared decision boundaries.

## Current Starting State

At plan creation:

- Vibe Science is treated as functionally complete as a skill/protocol layer. It is not the master plan; it is the rigor layer.
- VRE exists with a wiki surface at `vibe-science/blueprints/private/WIKI_VRE`.
- VRE is missing Phase 10 implementation. Phase 10 is gated on Phase 9 Wave 5 closure plus operator approval.
- OBDK exists at `vibe-science/blueprints/private/onco-bio-discovery-kernel`.
- OBDK has contracts, a CLI, recipes, tests, and prior planning evidence, but it is not yet complete as an autonomous paper-to-evidence kernel.
- OBDK does not yet have its own wiki. Wave B creates the OBDK wiki seed so the orthodox update packet can work.
- Vibe Science does not yet have its own wiki or ledger. Until the operator decides otherwise, Vibe Science integration changes are recorded in the active subsystem ledger and in this plan's ledger.

## What The Final System Must Do

The final system must support this end-to-end flow:

1. **Recover objective:** agent reads this plan, active wave pointer, and subsystem entrypoints.
2. **Query memory:** agent checks VRE for existing sources, methods, runs, scripts, decisions, and claims.
3. **Ingest paper:** agent stores paper/source metadata with provenance and durable IDs.
4. **Extract methods:** agent identifies procedures used by the paper and maps each procedure to OBDK method records.
5. **Route scripts:** agent searches the SPARK-derived script registry for an existing script or recipe.
6. **Generate missing script:** if no script exists, agent generates a sandboxed script with tests, records it as generated-pending-review, and does not promote claims from it without review.
7. **Execute analysis:** agent runs OBDK recipes or scripts under the active autonomy policy.
8. **Package evidence:** agent emits evidence-package, validation-ladder, limitations, negative-result, and review-ready artifacts where applicable.
9. **Trigger review:** agent creates a Vibe Science review packet and waits for or records adversarial review.
10. **Persist memory:** agent exports source, method, script, run, evidence, review, and decision links into VRE.
11. **Recover later:** a future agent can trace the whole chain from VRE back to source, script, run, evidence, review, and operator decision.

## Implementation Doctrine

Implementation follows the written plan, not chat improvisation.

The sequence is:

1. **Wave 0 — Preflight:** create ledgers, verify subsystem state, confirm Phase 9/Phase 10 gate status.
2. **Wave A — Foundation Cleanup:** mark OBDK overshoot surfaces experimental, resolve Cluster D v0.1 closure, sweep stale prose.
3. **Wave B — Agent Entrypoints:** create OBDK `SKILL.md`, create OBDK wiki seed, create cross-system map, finalize fresh-agent entrypoint.
4. **Wave C — OBDK Completion:** add paper ingestion, method extraction, script registry, sandbox generation scaffold, recipes, VRE export, absorbability pre-gate.
5. **Wave D — VRE Phase 10 Completion:** implement Phase 10 only after Phase 9 Wave 5 closure and operator GO.
6. **Wave E — Orchestration And Memory:** wire OBDK output to VRE memory and Vibe Science review.
7. **Wave F — Autonomous Runtime:** prove paper-to-evidence and failure scenarios under autonomy limits.
8. **Wave G — Validation And Handoff:** run final validation, adversarial review, absorbability verdict, handoff to VRE.

Any change to this sequence requires a plan patch, adversarial review, and operator decision if it changes scope or objective.

## Orthodox Execution Rule

The plan is executed as a binding operating doctrine.

For every implementation step and for every variation, even minimal, the agent must:

1. update the appropriate project wiki;
2. append the implementation ledger row;
3. append the incremental changelog row naming every edited file and why;
4. update the relevant README or start-here surface;
5. commit and push the reviewed work to GitHub, or record an operator-approved no-push waiver.

No step is complete without durable evidence. Test success alone is not closure.

## Operator Decision Boundaries

The agent asks the operator only at declared decision boundaries:

- objective change;
- scope change;
- irreversible state change;
- public/private boundary change;
- claim status promotion;
- external cost or compute;
- gate relaxation;
- GitHub push waiver.

Everything else is executed according to the active wave.

## What The Agent Must Not Do

The agent must not:

- replace this plan with a faster-looking plan in chat;
- turn tool-completion work into publication-grade biological analysis;
- treat Vibe Science as the master plan;
- call fixture smoke-tests real data execution;
- use chat memory as authority over files;
- skip wiki, ledger, changelog, README, or GitHub evidence;
- silently waive GitHub push;
- self-accept its own authored patch.

## Completion Criteria

The integrated project is complete only when:

1. OBDK is complete as a paper-to-evidence kernel with agent-facing entrypoint and wiki.
2. VRE Phase 10 is implemented and validated after its upstream gate.
3. OBDK, VRE, and Vibe Science are wired through documented adapters and traceable IDs.
4. A fresh-agent drill succeeds without operator path hints.
5. Autonomous runtime scenarios pass, including failure scenarios that fail closed.
6. All wiki, ledger, changelog, README, and GitHub evidence requirements are satisfied.
7. Counter-agent adversarial review accepts final state.
8. Operator closes the project and declares the integrated system ready for use.

## Recovery Instruction

If a future agent is unsure what to do:

1. read this file;
2. read `00_INDEX.md`;
3. read `ledger/active_wave.md` if present;
4. read the active wave file;
5. execute the next unchecked task exactly as written;
6. ask the operator only if a declared decision boundary is reached.
