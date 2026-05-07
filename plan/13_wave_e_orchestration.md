# Wave E — Orchestration And Memory
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Wire OBDK, VRE, and Vibe Science into a coherent cross-system workflow. After Wave E, an OBDK run produces evidence that lives in VRE memory, R2 review verdicts persist back to OBDK and VRE, and a single trace query can recover source-to-evidence chain.

## Pre-conditions

Both Wave C and Wave D closed (`ledger/active_wave.md` shows `active_wave: E`).

## Allowed Write Set

Wave E may write to:

- OBDK `obdk/orchestration_*.py` (new orchestration modules)
- OBDK `tests/test_orchestration_*.py`
- WIKI_VRE pages (computed artifact pages, review records, cross-system trace)
- `Agentic_architect/ledger/` and `Agentic_architect/reports/`
- `Agentic_architect/plan/` mirror after any plan amendment

Wave E does NOT:

- modify Phase 10 hard boundaries or Phase 9 contracts;
- delete any existing artifact;
- change OBDK contracts (other than minor field additions if absolutely necessary, with explicit operator decision);
- modify sibling Codex plan.

## Integration Contracts

| Producer | Consumer | Artifact |
|---|---|---|
| VRE | OBDK | source bundle path and source metadata |
| OBDK | VRE | paper source record, method records, run artifacts, evidence package |
| OBDK | Vibe Science | claim/review packet, assumptions, limitations |
| Vibe Science | VRE | R2 verdict, claim status, serendipity seed, operator decision |
| VRE | Agent | memory query results and active objective |

## Atomic Tasks

### Task E1 — Cross-system IDs

Define ID formats in `system_orchestration_map.md` (or extend existing map):

- [ ] `source_id`: matches `paper-source-record-v0.1.source_id` regex
- [ ] `method_id`: matches `method-extraction-record-v0.1.method_id` regex
- [ ] `script_id`: defined in script registry
- [ ] `run_id`: OBDK run directory name
- [ ] `evidence_id`: matches `evidence-package.evidence_id`
- [ ] `review_id`: Vibe Science R2 review record ID
- [ ] `operator_decision_id`: matches `OPDEC-<wave>-<sequence>-<short>` pattern

Add ID and backlink rules to `system_orchestration_map.md`.

### Task E2 — OBDK run to VRE page adapter

- [ ] Implement `obdk/orchestration_vre_export.py` (or extend `obdk/export_vre.py` from Wave C).
- [ ] Required behavior: every OBDK run exports a VRE computed artifact page; page links source bundle, method record, script record, run manifest, evidence package; page status remains `computed` until R2/claim review.
- [ ] Tests: run E2E on smoke recipe, verify VRE page created with correct backlinks.

### Task E3 — Vibe review packet adapter

- [ ] Implement `obdk/orchestration_vibe_review.py`.
- [ ] Required behavior: build review packet from OBDK run artifacts; include source citations, methods, assumptions, limitations, scripts, validation ladder; send or stage packet for R2/adversarial review.
- [ ] Tests: review packet contains all required fields; packet validates against Vibe Science review-packet schema.

### Task E4 — Review result persistence

- [ ] Implement persistence flow: R2 ACCEPT/REDIRECT/VETO writes to VRE page and OBDK ledger.
- [ ] Negative result creates preserved seed (Vibe Salvagente Rule) or negative-result record (if Cluster C governance contracts are implemented).
- [ ] Claim promotion requires explicit `claimed` status and operator decision (per `05_decision_boundaries.md`).
- [ ] Tests: ACCEPT updates page status to `validated`; REDIRECT stays at `computed` with findings recorded; VETO downgrades to `archived` with reason.

### Task E5 — Active objective resolver

- [ ] Implement `obdk/orchestration_objective.py`.
- [ ] Required behavior: agent asks VRE for current active objective; if none exists, operator prompt is required; if multiple active objectives exist, create escalation record.
- [ ] Tests: single objective returns it; no objective returns prompt-required; multiple objectives create escalation.

### Task E6 — End-to-end trace query

- [ ] Implement query: "For this evidence package, show the source paper, extracted method, script used or generated, run command, output files, R2 verdict, and operator decisions."
- [ ] Implementation: SQL-like join across VRE pages and OBDK records; or graph walk via backlinks.
- [ ] Tests: trace query returns all linked artifacts for a known evidence package; missing link fails the integration test.

### Task E7 — Cross-system orchestration report

- [ ] Write `reports/wave_e_orchestration_report.md` with: integration contracts implemented, ID rules used, trace query test result, identified failure modes and fallbacks.

### Task E8 — Append change_log row and update active wave

- [ ] Append closure row.
- [ ] Update `ledger/active_wave.md` to point at `F`.

## Adversarial Review Required

Wave E wires three subsystems. Reviewer verifies:

- ID rules consistent across OBDK contracts, VRE schemas, and Vibe Science records;
- VRE page creation does not violate LAW 13 (no claimed without R2);
- review packet contains all required fields;
- review result persistence updates both VRE and OBDK atomically (no torn states);
- end-to-end trace query returns complete chain;
- no integration leaks (e.g. OBDK does not write directly to VRE storage; routes through adapter).

## Closure Criteria

Wave E closes when:

- E1 through E8 checked;
- one cross-system run can be traced from source paper to evidence package to R2 review to VRE memory without chat context;
- adversarial review ACCEPT or ACCEPT_WITH_MINOR.

## Stop Conditions

Wave E stops and operator is asked if:

- Vibe Science R2 review API is not exposed (need operator decision on review interface);
- VRE Phase 10 query agent (Wave D) does not yet support cross-page joins (need fallback strategy);
- ID format conflicts emerge between OBDK contracts and VRE schemas (need operator decision on canonical format);
- claim promotion in test data needs operator approval (since claim promotion is in the declared decision categories).

## Outputs

After Wave E closure:

- 4 new OBDK modules: `orchestration_vre_export`, `orchestration_vibe_review`, `orchestration_objective`, plus integration with `export_vre`
- VRE pages for source/method/script/run/evidence/review/decision linkable
- Trace query implemented and tested
- `reports/wave_e_orchestration_report.md`
- ledger rows for all E tasks
- `ledger/active_wave.md` points at F
