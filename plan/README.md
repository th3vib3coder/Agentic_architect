# Integrated System Claude Plan — Completion Programme
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

> **REQUIRED SUB-SKILLS:** Use `superpowers:writing-plans` for any plan amendments. Use `superpowers:adversarial-pairing` (or kernel `adversarial-pairing` skill) for review gates. Use `superpowers:verification-before-completion` for closure claims.

## Purpose

This folder is the Claude-authored completion plan for the integrated agentic research system composed of three subsystems:

- **OBDK** (Onco Bio Discovery Kernel) — analysis tool, paper-to-evidence runtime, SPARK-derived script library
- **VRE** (Vibe Research Environment) — long-term memory, wiki provenance, objective management
- **Vibe Science** — rigor/governance framework, R2 review, claim ledger, anti-derailment discipline

The three subsystems already exist in partial state (Vibe Science complete, VRE missing Phase 10, OBDK missing completion). This plan brings all three to coordinated, agent-discoverable, autonomous-operation readiness.

## Operational Workspace Binding

The operator declared `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect` as the implementation workspace. This folder remains the local canonical plan source, and Wave 0 mirrors it into `Agentic_architect/plan/` so the public GitHub repository contains the plan, wiki, ledgers, reports, and README together.

Unless a wave explicitly names a subsystem path, relative plan references to `ledger/`, `reports/`, and `plan/` resolve inside `Agentic_architect/`.

## Orthodox Execution Mantras

These are implementation rules, not slogans:

1. **Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.** The active wave file and this plan are executed exactly as written unless a reviewed patch changes them.
2. **For each implementation step and for each variation, even minimal:** update the project wiki, write implementation ledgers and incremental changelogs with every edited file and why, update the relevant README describing what changed, and push the completed reviewed work to GitHub.

Any agent that cannot satisfy mantra 2 for a step must stop before starting that step, record the blocker, and ask the operator or the counter-reviewer. A chat explanation is not a substitute for wiki, ledger, changelog, README, and GitHub evidence.

## Relation to Sibling Plan

A sibling plan exists at `vibe-science/blueprints/private/integrated-agentic-research-system-plan/` authored by Codex. This Claude-authored plan covers the same scope with the following structural differences:

- More granular file count (26 vs 16) for tighter atomic deliverables
- Dedicated Wave 0 preflight (state verification before any other wave)
- Test strategy file separate from wave files (so test specs survive wave changes)
- Multi-agent pairing protocol file (explicit Codex/Claude/operator role boundaries per wave)
- Operator decision register file (single source of truth for decisions awaiting operator)
- Recovery protocol scoped to multi-system (OBDK + VRE + Vibe), not single-system OBDK only

The two plans reconciled via OPDEC-PLAN-001. This Claude-authored plan is canonical; the sibling Codex plan is reference-only and is not executed unless the operator records a new plan decision.

## Goal Statement (immutable until operator changes it)

A fresh agent (Claude Code, Codex, or any tool-calling LLM agent) opening this workspace with no chat history must be able to:

1. discover the integrated system entry point within six filesystem reads;
2. identify the active wave and the operator decision points blocking it;
3. execute non-blocking tasks of the active wave without operator path hints;
4. invoke OBDK, query VRE, and trigger Vibe Science review correctly;
5. ingest a new paper, extract methods, route or generate scripts, execute analyses, and persist evidence to VRE memory;
6. recover from a derailment by reading derailment patterns and following the recovery protocol;
7. escalate to operator only on the declared decision categories listed in `05_decision_boundaries.md`.

## Non-Goal Statement (immutable until operator changes it)

This plan does not:

- promote OBDK to a publication-grade scientific platform unless operator changes the goal;
- replace any existing canonical control plane (OBDK `analisi_claude/project_plan`, WIKI_VRE `index.md`, Phase 10 spec) — it coordinates them;
- delete or rewrite any existing append-only ledger;
- assume any chat-history context;
- introduce new biological research questions beyond what is already in OBDK `d0-*` documents.

## Read First (6-file fresh-agent path)

1. `README.md` — this file
2. `23_project_goal_and_implementation_doctrine.md` — complete durable goal and implementation doctrine
3. `00_INDEX.md` — reading order and file role table
4. `01_canonical_state_audit.md` — current state of OBDK, VRE, Vibe Science, and dependencies
5. `02_purpose_anchor.md` — immutable objective and decision authority stack
6. `04_master_sequence.md` — wave order, dependencies, active wave pointer

After these six, the agent has enough context to identify which wave file to read next.

## Distribution Note

This plan folder lives under `blueprints/private/` and is not for external distribution. It is the implementer-facing coordination control plane. Any public-facing artifact requires explicit operator decision and routing through VRE export.

## Plan Status

| Status | Detail |
|---|---|
| Created | 2026-05-07 |
| Author | Claude (cross-agent) |
| Pairing | Codex parallel author exists; reconciliation pending adversarial review |
| Active wave | Wave 0 — Preflight (until ledgers exist) |
| Adversarial review status | not yet reviewed by Codex |
| Operator closure status | not yet operator-closed |
