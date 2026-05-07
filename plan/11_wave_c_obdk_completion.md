# Wave C — OBDK Completion
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Complete OBDK as the executable analysis kernel: paper ingestion, method extraction, script routing/generation, recipe library expansion, evidence packaging, VRE export adapter, absorbability pre-gate.

This is the largest wave (effort class XL, 10-15 sessions). It can run in parallel with Wave D (VRE Phase 10) provided write sets do not collide.

## Pre-conditions

Wave B closed (`ledger/active_wave.md` shows `active_wave: C and D (parallel)`).

## Allowed Write Set

Wave C may write to:

- `vibe-science/blueprints/private/onco-bio-discovery-kernel/contracts/*.md` (new contracts; bumps to existing only with explicit operator decision)
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/obdk/*.py` (new modules; modifications only via explicit task)
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/recipes/*.yaml` (new recipes)
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/registry/*.yaml` (script registry entries)
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/tests/*.py` (new tests)
- `vibe-science/blueprints/private/onco-bio-discovery-kernel/charter-v0.5.md` (§16 catalog updates only via formal HAT pattern)
- `Agentic_architect/ledger/` and `Agentic_architect/reports/`
- `Agentic_architect/plan/` mirror after any plan amendment

Wave C does NOT:

- delete contracts;
- modify VRE, Phase 10, Phase 9 files;
- modify Vibe Science core;
- modify sibling Codex plan.

## Workstreams

| Workstream | Purpose |
|---|---|
| C1 | Pending contract scope reconciliation |
| C2 | Paper source bundle contract and ingestion |
| C3 | Method extraction record and CLI |
| C4 | SPARK-derived script registry |
| C5 | Sandbox script generation runtime |
| C6 | Recipe library expansion |
| C7 | OBDK to VRE export adapter |
| C8 | OBDK absorbability pre-gate |

## Atomic Tasks

### Task C1 — Pending contract scope reconciliation

- [ ] Read OBDK `analisi_claude/project_plan/wiki/contract_registry.md` and `15_milestone_roadmap_v0.1.md`.
- [ ] For each of the 15 pending contracts (Cluster C governance, Cluster E LLM, Cluster F predictive), classify:
  - `must-have` for autonomous paper-to-analysis v1
  - `must-have only when LLM generation is enabled`
  - `must-have only when predictive modeling is used`
  - `safely deferred with concrete trigger`
- [ ] Write `reports/obdk_contract_completion_scope.md` with the classification.
- [ ] If any contract changes completion scope (must-have moves to deferred or vice versa), record an operator decision request in `19_operator_decision_register.md`.

### Task C2 — Paper source bundle contract and ingestion CLI

- [ ] Create `contracts/paper-source-record-v0.1.md` (Pydantic v2; JSON Schema export). Required fields: `source_id`, `source_kind` (paper, supplement, dataset_accession, operator_note), `title`, `authors`, `year`, `doi_or_pmid`, `local_raw_path`, `provenance_status`, `ingested_at`, `operator_notes`. Plus 1 valid + 5 invalid fixtures.
- [ ] Create `obdk/paper_ingest.py` with `ingest_paper(pdf_path, out_dir) -> RunResult` function.
- [ ] Add CLI entry point: `python -m obdk.cli ingest-paper --pdf <path> --out runs/paper_ingest/<source_id>`.
- [ ] Required behavior: copy or register PDF path, compute SHA256, extract text if possible (via `pypdf` or fallback to text-only file), write `paper_source_record.yaml`, write `paper_text.txt`, write ingestion manifest.
- [ ] Tests: valid PDF/text fixture ingests; missing file fails; checksum stable; manifest validates against contract.
- [ ] Update charter §16 to add the new contract.

### Task C3 — Method extraction record and CLI

- [ ] Create `contracts/method-extraction-record-v0.1.md` (Pydantic v2). Required fields: `method_id`, `source_ref` (FK to paper-source-record), `section_locator`, `procedure_name`, `procedure_type` (DE, GSEA, Cox, batch correction, etc.), `input_data_type`, `output_artifact_type`, `software_or_package`, `parameters`, `assumptions`, `extraction_confidence`, `requires_operator_review`. Plus 1 valid + 5 invalid fixtures.
- [ ] Create `obdk/method_extraction.py` with extraction logic (rule-based + heuristic; LLM-driven path deferred to Cluster E).
- [ ] CLI: `python -m obdk.cli extract-methods --source runs/paper_ingest/<source_id> --out runs/method_extract/<source_id>`.
- [ ] Required behavior: locate methods section or require manual locator, extract procedure candidates, write `method_extraction_records.yaml`, flag low-confidence candidates for operator review, never fabricate software/version when absent.
- [ ] Tests: fixture methods text yields expected procedures; no methods section yields review-required record; unsupported procedure creates script-generation candidate.

### Task C4 — SPARK-derived script registry

- [ ] Create `obdk/script_registry.py` with `ScriptRegistry` class supporting list, lookup by procedure type and input data type, return command template and required parameters, classify `take`, `improve`, `skip`, or `generate`.
- [ ] Create `registry/scripts/` with at least 5 YAML registry entries (5 SPARK-derived methods chosen from `analisi_claude/05_extraction_register.md`).
- [ ] Tests: registry loads, lookup works, missing procedure returns `generate` classification.

### Task C5 — Sandbox script generation path

- [ ] Create `obdk/sandbox_runtime.py` (or use existing `generated-code-sandbox-contract` if implemented).
- [ ] CLI: `python -m obdk.cli generate-script --method-record path/to/method.yaml --out sandbox/generated_scripts/<method_id>`.
- [ ] Required behavior: generate script only inside sandbox directory, create test fixture first, run test before registration, write generation metadata, mark `generated_pending_review` until adversarial review.
- [ ] Tests: missing script template generates a stub, test runs, registration record written.
- [ ] Note: actual LLM-driven generation is deferred to Cluster E LLM contracts; for Wave C, generation can be scaffolded only with an operator-provided concrete template or deterministic static scaffold that has tests.

### Task C6 — Recipe library expansion

Create three must-have recipes; two nice-to-have recipes deferred per operator decision:

Must-have:

- [ ] `recipes/bulk_signature_scoring.yaml` — extension of existing `d0_eaoc_syndecan_upr.yaml` pattern for any signature.
- [ ] `recipes/pseudobulk_de.yaml` — DESeq2 pseudobulk differential expression.
- [ ] `recipes/pathway_enrichment.yaml` — GSEA / fgsea pathway enrichment from ranked genes.

Nice-to-have (operator decision required to add):

- [ ] `recipes/cross_platform_validation.yaml`
- [ ] `recipes/scrna_compartment_scoring.yaml`

Each recipe must include: input contract refs, output artifact declarations, expected validation ladder behavior, VRE export policy, minimal fixture or smoke data.

### Task C7 — OBDK to VRE export adapter

- [ ] Create `obdk/export_vre.py`.
- [ ] CLI: `python -m obdk.cli export-vre --evidence-package path/to/evidence.yaml --vre-root vibe-science/blueprints/private/WIKI_VRE`.
- [ ] Required behavior: create computed artifact page in VRE, create source/procedure/run backlinks, preserve evidence package path, never mark as claimed without review verdict.
- [ ] Tests: valid evidence package produces VRE page; missing provenance fails; claimed status without R2 verdict fails.
- [ ] Note: VRE Phase 10 must be implemented (Wave D) for full end-to-end export; for Wave C, the adapter can write to a staging directory if Phase 10 is not yet ready, with explicit "pending Phase 10" note.

### Task C8 — OBDK absorbability pre-gate report

- [ ] Run all OBDK validations:
  - `python -m pytest --tb=short -q`
  - `python -m ruff check .`
  - `python -m obdk.cli contracts validate --charter charter-v0.5.md`
- [ ] Verify Wave C deliverables:
  - new contracts (paper-source-record, method-extraction-record) implemented and validated
  - 3 must-have recipes runnable
  - script registry has at least 5 entries
  - sandbox generation path tested
  - VRE export adapter tested (staging if Phase 10 not ready)
- [ ] Write `reports/obdk_absorbability_pregate.md` with: contract validation evidence, recipe coverage, script registry coverage, paper ingestion pass/fail, method extraction pass/fail, VRE export pass/fail (or staging note), remaining deferred contracts with triggers.

### Task C9 — Append change_log row and update active wave

- [ ] Append closure row to `ledger/change_log.md`.
- [ ] Update `ledger/active_wave.md` to point at `E` if D is also closed (or remain at `C and D parallel` until both close).

## Adversarial Review Required

Wave C introduces new contracts, code, recipes, and CLI commands. Reviewer verifies:

- new contracts validate via OBDK contract validate command;
- new code passes ruff and pytest;
- new recipes run end-to-end on smoke fixtures;
- script registry lookups are deterministic and complete;
- sandbox generation does not exfiltrate to filesystem outside sandbox dir;
- VRE export adapter does not violate LAW 13 (no claimed status without R2);
- absorbability pre-gate report is honest about what works and what is deferred.

## Closure Criteria

Wave C closes when:

- C1 through C9 checked;
- 3 must-have recipes run successfully end-to-end on smoke fixtures;
- script registry has at least 5 entries; at least 1 lookup test passes for each recipe;
- paper ingestion + method extraction pipeline runs on at least one real paper bundle (operator-provided);
- VRE export adapter is implemented (with Phase 10 staging note if D not yet ready);
- absorbability pre-gate report is complete;
- adversarial review ACCEPT or ACCEPT_WITH_MINOR.

## Stop Conditions

Wave C stops and operator is asked if:

- a contract change requires modifying an existing fixture (operator decision required for fixture changes);
- a script registry classification needs operator input (e.g. SKIP a SPARK function);
- the paper ingestion pipeline needs an external library (`pypdf`, `pdfplumber`) that is not in `pyproject.toml` dependencies;
- the VRE export adapter cannot be implemented because Phase 10 is not yet available (decide: stage to local OR pause Wave C until D ready);
- a recipe requires data not in the OBDK fixtures directory (operator decides whether to add fixture or use real cohort);
- LLM-driven generation is required for a critical method (route to Cluster E LLM contracts implementation).

## Outputs

After Wave C closure:

- 2 new contracts: `paper-source-record-v0.1`, `method-extraction-record-v0.1` (charter §16 +2 catalog entries)
- 4-5 new OBDK modules: `paper_ingest`, `method_extraction`, `script_registry`, `sandbox_runtime`, `export_vre`
- 3 new recipes (must-have); 2 deferred (nice-to-have)
- script registry with 5+ entries
- 4 new CLI commands: `ingest-paper`, `extract-methods`, `generate-script`, `export-vre`
- new tests covering all of the above
- `reports/obdk_absorbability_pregate.md`
- updated charter §16 catalog
- ledger row INTPLAN-C-001 (closed) plus per-task rows
