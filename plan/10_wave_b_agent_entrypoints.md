# Wave B — Agent Entrypoints
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Make the integrated system discoverable and usable by a fresh agent without chat history. Create the agent-facing surface (OBDK SKILL.md, cross-system orchestration map, fresh-agent simulation checklist) and the tests that ensure entrypoints remain present.

## Pre-conditions

Wave A closed (`ledger/active_wave.md` shows `active_wave: B`).

## Allowed Write Set

Wave B may create:

- `vibe-science/blueprints/private/onco-bio-discovery-kernel/SKILL.md`
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/wiki/index.md`
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/wiki/*.md`
- `Agentic_architect/plan/system_orchestration_map.md`
- `Agentic_architect/reports/wave_b_*.md`
- ledger rows under `Agentic_architect/ledger/`
- minor edits to `14_agent_start_here_card.md` if needed (Wave B finalizes the agent card; in this plan the card is built progressively)

Wave B does NOT:

- modify OBDK contracts, code, or tests (other than adding `SKILL.md`);
- modify VRE, Phase 10, Phase 9 files;
- modify Vibe Science core;
- modify sibling Codex plan.

## Atomic Tasks

### Task B1 — Create OBDK SKILL.md (agent-facing wrapper)

Create `vibe-science/blueprints/private/onco-bio-discovery-kernel/SKILL.md` with these sections:

- [ ] **Purpose**: OBDK is the analysis kernel for paper-to-evidence workflows. It ingests papers, extracts methods, routes or generates scripts, executes recipes, and emits evidence packages.
- [ ] **When to invoke OBDK**:
  - paper method extraction requiring executable analysis;
  - omics dataset/cohort processing;
  - SPARK-derived script routing;
  - evidence-package generation;
  - validation-ladder or claim-supporting analysis artifacts.
- [ ] **When NOT to invoke OBDK**:
  - general chat;
  - pure literature summary without analysis;
  - VRE wiki maintenance unrelated to analysis;
  - Vibe Science protocol work without computational artifact.
- [ ] **Commands**:
  ```
  python -m obdk.cli contracts validate --charter charter-v0.5.md
  python -m obdk.cli export-schemas --charter charter-v0.5.md --out schemas
  python -m obdk.cli run --recipe recipes/d0_eaoc_syndecan_upr.yaml --out runs/manual_smoke
  ```
  Plus future commands added in Wave C: `ingest-paper`, `extract-methods`, `generate-script`, `export-vre`.
- [ ] **Output interpretation**: where score tables, validation ladders, evidence packages, manifests appear; how to read them.
- [ ] **Escalation rules**: cite `vibe-science/blueprints/private/integrated-system-claude-plan/05_decision_boundaries.md` for the declared operator decision categories.
- [ ] **Cross-system links**: VRE memory at `vibe-science/blueprints/private/WIKI_VRE/`, Vibe Science at repository root, this plan at `vibe-science/blueprints/private/integrated-system-claude-plan/`.
- [ ] **Anti-derailment hooks**: cite `07_anti_derailment.md` patterns; remind agent that smoke-test on fixture is not real data.

### Task B2 — Create cross-system orchestration map

Create `system_orchestration_map.md` in this plan folder with:

- [ ] Diagram (Mermaid or ASCII) showing agent startup → VRE memory query → OBDK execution → Vibe review → VRE persistence.
- [ ] Decision table: when to use VRE, OBDK, Vibe Science, or operator.
- [ ] Failure fallback table: missing OBDK script, missing VRE page, Vibe gate failure, conflicting memories, Phase 10 not implemented yet (smoke fallback).
- [ ] ID and backlink rules: how `source_id`, `method_id`, `script_id`, `run_id`, `evidence_id`, `review_id`, `operator_decision_id` are formatted and where they live.

### Task B3 — Finalize agent start-here card

Refine `14_agent_start_here_card.md` to include:

- [ ] Exact first 10 files/commands the agent reads/runs.
- [ ] "Do not do" warnings learned from past derailments (the five patterns).
- [ ] Active objective statement: complete integrated system, not run biological research unless the active wave says so.
- [ ] Reference to `19_operator_decision_register.md` for decisions awaiting operator.

### Task B4 — Add entrypoint presence checks

Either as:

- (a) OBDK pytest test under `vibe-science/blueprints/private/onco-bio-discovery-kernel/tests/test_skill_md_present.py` that checks `SKILL.md` exists and contains required sections; OR
- (b) PowerShell/POSIX recipe in `reports/wave_b_entrypoint_check.md` that lists the validation commands.

If OBDK test path is chosen:

- [ ] Test file created.
- [ ] Test added to OBDK pytest collection without breaking existing 231 tests.
- [ ] Test passes.

If recipe path is chosen:

- [ ] Recipe file created with all checks.
- [ ] Each check has a documented expected output.

### Task B5 — Fresh-agent simulation

Run a simulated fresh agent flow without using chat memory:

- [ ] Start from the repository root.
- [ ] Open `vibe-science/blueprints/private/integrated-system-claude-plan/14_agent_start_here_card.md`.
- [ ] Follow the first 10 moves.
- [ ] Confirm agent can identify:
  - OBDK path
  - VRE path
  - Phase 10 path
  - Vibe Science path
  - validation commands
  - active wave
  - operator escalation points
- [ ] Record findings in `reports/wave_b_fresh_agent_simulation.md`.

If any step fails (file missing, instruction unclear, escalation rule not findable), patch the corresponding plan file and re-run the simulation.

### Task B6 — Create OBDK wiki seed

Create `vibe-science/blueprints/private/onco-bio-discovery-kernel/wiki/index.md` and seed the minimum pages required for future orthodox updates:

- [ ] `wiki/index.md`: purpose, reading order, relationship to `analisi_claude/project_plan/`, relationship to OBDK `SKILL.md`.
- [ ] `wiki/contracts.md`: contract catalog pointer and how contract changes are documented.
- [ ] `wiki/recipes.md`: recipe catalog pointer and how recipe changes are documented.
- [ ] `wiki/scripts.md`: SPARK-derived script registry pointer and how new scripts are recorded.
- [ ] `wiki/runs.md`: where run artifacts and evidence-package exports are documented.
- [ ] Cross-link each page back to this integrated plan and to OBDK `SKILL.md`.
- [ ] Mark OBDK wiki ready for orthodox packet updates in this plan's `ledger/change_log.md`.

If the operator chooses a different OBDK wiki location, record the decision before creating files.

### Task B7 — Append change_log row and update active wave

- [ ] Append row to `ledger/change_log.md`:
  ```
  | <ISO date> | INTPLAN-B-001 | OBDK SKILL.md + OBDK wiki seed + plan/system_orchestration_map.md + plan/14_agent_start_here_card.md + plan/reports/wave_b_*.md | wave B: agent entrypoints and OBDK wiki seed created and validated | closed |
  ```
- [ ] Update `ledger/active_wave.md`:
  ```
  active_wave: C and D (parallel)
  since: <ISO date>
  last_updated_by: <agent>
  last_updated_reason: wave B closed; opening waves C and D
  ```

## Adversarial Review Required

Wave B introduces new agent-facing surfaces (SKILL.md, orchestration map, agent card). Reviewer verifies:

- SKILL.md sections complete and non-misleading;
- orchestration map is accurate (no fabricated paths or capabilities);
- agent card first-10-moves actually work in a fresh-agent simulation;
- entrypoint presence check passes;
- no derailment patterns crept into the wrappers.

## Closure Criteria

Wave B closes when:

- B1, B2, B3, B4, B5, B6, B7 checked;
- adversarial review ACCEPT or ACCEPT_WITH_MINOR;
- fresh-agent simulation passes without operator path hints.

## Stop Conditions

Wave B stops and operator is asked if:

- the agent realizes SKILL.md content depends on Wave C deliverables not yet built (e.g. `ingest-paper` CLI). Resolution: SKILL.md lists planned commands but marks them "available after Wave C closure";
- the orchestration map needs to specify VRE Phase 10 capability that is not yet implemented. Resolution: map shows planned wiring with "pending Wave D" note;
- the fresh-agent simulation fails because the agent cannot find the active wave. Resolution: amend agent card.

## Outputs

After Wave B closure:

- `vibe-science/blueprints/private/onco-bio-discovery-kernel/SKILL.md` exists with all required sections
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/wiki/index.md` exists and links contracts, recipes, scripts, runs, and the integrated plan
- `Agentic_architect/plan/system_orchestration_map.md` exists with diagram, tables, IDs
- `14_agent_start_here_card.md` finalized
- `reports/wave_b_fresh_agent_simulation.md` documents the simulation
- entrypoint presence check exists (test or recipe)
- `ledger/active_wave.md` points at C and D parallel
