# Wave D — VRE Phase 10 Completion
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Complete the VRE Phase 10 researcher knowledge layer so VRE can serve as long-term memory for sources, methods, analyses, claims, assumptions, and decisions. Wave D is gated externally by Phase 9 Wave 5 closure and operator approval (HB-1 from Phase 10 spec).

## Pre-conditions

Wave B closed AND one of:

- Phase 9 Wave 5 already closed at plan creation, OR
- Phase 9 Wave 5 closes during Wave C parallel execution, AND
- Operator confirms Phase 10 implementation track GO via `vre phase10 implementation-track-start --confirm` or equivalent recorded operator decision.

If Phase 9 Wave 5 is in progress and operator has not given GO, Wave D pauses until both conditions are met. Wave C can still proceed in parallel (parallel-safe with Wave D).

## Allowed Write Set

Wave D may write to:

- `vibe-science/blueprints/private/WIKI_VRE/**` — only Phase 10-scoped additions (new pages, schemas, tools)
- `vibe-science/blueprints/private/phase10-knowledge-layer/**` — implementation track artifacts (per HB-1 path discipline)
- `Agentic_architect/ledger/` and `Agentic_architect/reports/`
- `Agentic_architect/plan/` mirror after any plan amendment

Wave D does NOT:

- modify any Phase 9 file;
- modify OBDK contracts (other than evidence-package vre_export_destination value space if needed, and only via explicit task);
- modify Vibe Science core;
- modify sibling Codex plan.

## Authoritative Inputs

Wave D consumes these as authoritative:

- `vibe-science/blueprints/private/phase10-knowledge-layer/02-formal-design-spec.md` — Phase 10 design (HB-1..HB-13 hard boundaries)
- `vibe-science/blueprints/private/phase10-knowledge-layer/03-vre-existing-state-audit.md` — VRE state at Phase 10 design time
- `vibe-science/blueprints/private/WIKI_VRE/CLAUDE.md` — agent instructions
- `vibe-science/blueprints/private/WIKI_VRE/PROTOCOL-wiki-integrated-implementation.md` — integration protocol
- `vibe-science/blueprints/private/WIKI_VRE/index.md` — wiki entry point

## Atomic Tasks

### Task D1 — Phase 10 implementation readiness gate

- [ ] Verify Phase 9 Wave 5 closure status by reading `phase9-implementation-plan/00-index.md` and Wave 5 split-series files (06d-T5.2 through T5.7).
- [ ] If Wave 5 is closed: proceed.
- [ ] If Wave 5 is in progress: pause Wave D, document status in `reports/wave_d_phase9_dependency.md`, escalate operator only if Wave 5 is stalled.
- [ ] Verify operator approval for Phase 10 implementation track. If not yet given, request decision in `19_operator_decision_register.md`.
- [ ] Once both conditions met, record decision in this plan's `ledger/operator_decisions.md`.

### Task D2 — Phase 10 source bundle store

- [ ] Implement source bundle ingestion per Phase 10 spec §"Source Bundle Layer".
- [ ] Required behavior: accept papers, supplements, web clips, datasets, operator notes; enforce LAW 13 provenance or declaration; store raw material without changing content; expose source pages in VRE wiki.
- [ ] Validation: missing provenance fails; candidate/cache/query result cannot be cited as provenance; source bundle page includes `last-verified-at`.
- [ ] Tests: per Phase 10 spec test catalog.

### Task D3 — Wiki compile pipeline

- [ ] Implement wiki compile per Phase 10 spec §"Wiki Compile Pipeline".
- [ ] Required behavior: compile raw source bundles into wiki pages; maintain status (sourced, computed, claimed, supposition); fail closed on missing provenance; isolate supposition from authoritative pages.
- [ ] Validation: `wiki-lint --json` equivalent exits 0; deliberate page without provenance fails.

### Task D4 — Query agent and durable answers

- [ ] Implement query agent per Phase 10 spec §"Query Layer".
- [ ] Required behavior: answer questions using WIKI_VRE pages; include citation list; optionally file durable answer as computed/synthesis page; never cite query result as provenance.
- [ ] Validation: query over known page returns citation; query with no source returns insufficient-evidence answer.

### Task D5 — R2 audit binding

- [ ] Implement R2 audit binding per Phase 10 spec §"R2 Binding".
- [ ] Required behavior: authoritative synthesis requires R2 audit; decision-grade query requires R2 audit; review verdict is linked to page and source material.
- [ ] Validation: synthesis without R2 cannot become `claimed`; review record is discoverable from page.

### Task D6 — Operator steering and goal immutability

- [ ] Implement per Phase 10 spec §"Operator Steering".
- [ ] Required behavior: use existing VRE escalation/objective schemas where possible; record direction-change and operator-request events; prevent silent objective mutation; require explicit supersession for changed objective.
- [ ] Validation: attempted objective mutation creates escalation or supersession, not silent edit.

### Task D7 — Serendipity preservation

- [ ] Implement per Phase 10 spec §"Serendipity Preservation".
- [ ] Required behavior: preserve serendipity seeds with source context; link seeds to papers, methods, or analyses; allow retrieval by an agent in future sessions.
- [ ] Validation: seed has source/context/proposed follow-up; seed survives wiki sync.

### Task D8 — Phase 10 completion report

- [ ] Write `reports/vre_phase10_completion_report.md` containing: hard boundary compliance, implemented stores, lint results, R2 binding result, query result examples, remaining deferrals with triggers.

### Task D9 — Append change_log row and update active wave

- [ ] Append closure row.
- [ ] Update `ledger/active_wave.md` to point at `E` (if Wave C also closed).

## Adversarial Review Required

Wave D implements Phase 10 layer. Reviewer (Claude or Codex, depending on author) verifies:

- HB-1..HB-13 hard boundaries respected;
- LAW 13 fail-closed behavior in code;
- query agent never cites query result as provenance;
- R2 binding blocks unauthorized claimed synthesis;
- operator steering creates escalation/supersession events, not silent edits;
- serendipity seeds survive wiki sync.

## Closure Criteria

Wave D closes when:

- D1 through D9 checked;
- LAW 13 fail-closed in code or validated protocol;
- paper/source bundle ingestion is durable;
- query returns cited answers;
- R2 binding blocks unauthorized claimed synthesis;
- operator steering and objective immutability enforced;
- WIKI_VRE mirror/registries are consistent (`build-registries.mjs --check` passes);
- adversarial review ACCEPT or ACCEPT_WITH_MINOR;
- Phase 10 completion report exists.

## Stop Conditions

Wave D stops and operator is asked if:

- Phase 9 Wave 5 closure is delayed beyond expected window;
- HB-1 cannot be satisfied (operator has not given Phase 10 GO);
- a Phase 10 hard boundary conflicts with implementation (rare; design spec is canonical);
- Node tooling for WIKI_VRE registry build is not available;
- R2 audit infrastructure (Vibe Science) does not expose an API for Phase 10 binding;
- VRE storage layer needs a backend choice (filesystem vs SQLite vs other) — operator decision.

## Outputs

After Wave D closure:

- Phase 10 layer implemented in `WIKI_VRE/` per spec
- LAW 13 fail-closed enforced
- Query agent operational
- R2 binding operational
- Operator steering events logged
- Serendipity preservation operational
- `reports/vre_phase10_completion_report.md` exists
- ledger rows for all D tasks
- `ledger/active_wave.md` advances when both C and D close
