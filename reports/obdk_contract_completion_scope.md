# OBDK Contract Completion Scope

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Scope

Wave C task C1 classifies the 15 pending OBDK contracts named in `plan\11_wave_c_obdk_completion.md`: Cluster C governance, Cluster E LLM/cost/reproducibility, and Cluster F predictive/cycle-health/governance-gap contracts.

This report is a classification artifact. It does not implement or defer any contract by itself.

## Pre-Output Failure Modes

- FM-1: The 15-contract list could drift from the actual OBDK registry and roadmap after Cluster A/B/D closures.
- FM-2: A contract could be marked deferred even though Wave C needs it for autonomous paper-to-analysis v1.
- FM-3: A contract could be marked must-have for v1 when the source text gates it on LLM generation, predictive modeling, or later validated feature families.

## Source Evidence

| Evidence ID | Source |
|---|---|
| E1 | `analisi_claude/project_plan/wiki/contract_registry.md:1-31` says the current implemented identities are 24 and lists all implemented families through Cluster D v0.2. |
| E2 | `analisi_claude/15_milestone_roadmap_v0.1.md:106-134` groups the remaining 15 contracts into Cluster C, Cluster E, and Cluster F. |
| E3 | `analisi_claude/15_milestone_roadmap_v0.1.md:111` maps Cluster C to Horizon 3.1 WIKI_VRE, negative-result, catalog, and privacy absorption conditions. |
| E4 | `analisi_claude/15_milestone_roadmap_v0.1.md:128` maps Cluster E to Horizon 3.1 provenance and reproducibility-envelope conditions. |
| E5 | `charter-v0.5.md:387-388` gates `predictive-model-record` on model usage and names `cycle-health-metrics-record`. |
| E6 | `charter-v0.5.md:402` says cycle health metrics must be computed for D-cycles. |
| E7 | `charter-v0.5.md:678` requires at least three negative results for absorption. |
| E8 | `charter-v0.5.md:684` requires the human-readable catalog/reference book after more than one validated feature family exists. |
| E9 | `charter-v0.5.md:686` requires a reproducibility envelope for the D-cycle. |
| E10 | `kernel-requirements-matrix-v0.3.md:80` requires `prompt-template-record` fields for prompt templates. |
| E11 | `kernel-requirements-matrix-v0.3.md:83` requires LLM outputs that influence records to be cached with prompt/model/timestamp/output hashes. |
| E12 | `kernel-requirements-matrix-v0.3.md:85` requires token/model cost to be split from compute/resource cost. |
| E13 | `kernel-requirements-matrix-v0.3.md:129-130` makes catalog/reference-book output mandatory after more than one validated feature family and specifies catalog content. |
| E14 | `kernel-requirements-matrix-v0.3.md:152` requires every D-cycle to produce `reproducibility-envelope-record`. |
| E15 | `d0-dataset-selection-memo-v0.1.md:346` says the kernel should generate an explicit `dataset-gap-record` or `negative-result-record` for groups without acceptable data. |
| E16 | `vibe-science-paper-integration-note-v0.1.md:193-194` says `r2-review-record` and external-review-summary should be promoted only if internal/external R2 or automated external-review routing need independent lifecycle. |
| E17 | `interop-mapping-v0.1.md:77-78` says review routing is partly represented by `evidence-package` and future `human-review-packet`, but external-review routing is not implemented. |
| E18 | `interop-mapping-v0.1.md:96-100` says catalog and reproducibility envelope remain future artifacts while evidence-package/provenance cover part of the shape. |

## Classification

| Contract | Class | Trigger / Timing | Evidence |
|---|---|---|---|
| `negative-result-record` | must-have for autonomous paper-to-analysis v1 | Required before Wave C can honestly close on real paper-to-analysis work that may fail, be underpowered, lack data, or produce no signal. | E3, E7, E15 |
| `limitations-record` | must-have for autonomous paper-to-analysis v1 | Required before v1 emits reviewable outputs from extracted methods, recipes, or evidence packages, because limitations must survive export instead of living only in prose. | E2, E3, E15 |
| `dataset-gap-record` | must-have for autonomous paper-to-analysis v1 | Required when source papers, datasets, cohorts, or recipe inputs are unavailable or unsuitable; prevents fake coverage. | E2, E15 |
| `cycle-health-metrics-record` | must-have for autonomous paper-to-analysis v1 | Required when Wave C reaches D-cycle-like execution or repeated paper-to-analysis runs; it measures confounder coverage, replication, pathway recovery, and related health signals. | E5, E6 |
| `compute-cost-record` | must-have for autonomous paper-to-analysis v1 | Required once Wave C runs nontrivial local compute, because cost/resource evidence is distinct from token/model cost. | E4, E12 |
| `reproducibility-envelope-record` | must-have for autonomous paper-to-analysis v1 | Required before a D-cycle can be called reproducible or absorbable; Wave C should either implement it or explicitly mark pre-gate limitation. | E4, E9, E14, E18 |
| `prompt-template-record` | must-have only when LLM generation is enabled | Not required for deterministic paper ingest, rule-based method extraction, static script registry, or deterministic sandbox scaffold. Required before LLM prompts influence records. | E2, E10 |
| `llm-config-record` | must-have only when LLM generation is enabled | Required before LLM provider/model/reasoning configuration influences extraction, generation, or acceptance. | E2, E10 |
| `llm-output-cache-record` | must-have only when LLM generation is enabled | Required before any LLM output influences records; otherwise reproducibility cannot rely on cached prompt/model/output hashes. | E2, E11 |
| `llm-cost-record` | must-have only when LLM generation is enabled | Required when token/model spend exists; separate from compute/resource cost. | E2, E12 |
| `agent-meta-validation-record` | must-have only when LLM generation is enabled | Required when agent judgments influence record acceptance or automated review; deterministic scaffolding does not require it. | E2, E10, E16 |
| `hypothesis-diversity-record` | must-have only when LLM generation is enabled | Required when the kernel generates or deduplicates hypothesis sets; not required for ingesting a paper and extracting its existing methods. | E2, E5 |
| `predictive-model-record` | must-have only when predictive modeling is used | Charter explicitly gates this contract on model usage. Wave C's must-have recipes do not include predictive modeling. | E2, E5 |
| `catalog-record` | safely deferred with concrete trigger | Trigger: after more than one validated feature family exists or when a human-readable reference book renderer is requested. | E3, E8, E13, E18 |
| `human-review-packet` | safely deferred with concrete trigger | Trigger: automated external-review routing or independent lifecycle for internal/external R2 outputs. Until then, `evidence-package` plus adversarial ledger covers review state. | E16, E17 |

## Decision Register Check

Wave C C1 says to record an operator decision request in `19_operator_decision_register.md` if classification changes completion scope. This report does not change completion scope; it classifies the existing roadmap/charter triggers.

Path note: `vibe-science/blueprints/private/onco-bio-discovery-kernel/analisi_claude/19_operator_decision_register.md` is absent. If a Wave C contract-scope decision becomes necessary later, use OBDK `analisi_claude/project_plan/ledger/operator_decisions.md` for the durable OBDK decision record and mirror cross-system state in Agentic Architect.

## C1 Outcome

- Pending contracts reviewed: 15/15.
- Must-have for autonomous paper-to-analysis v1: 6 contracts.
- Must-have only when LLM generation is enabled: 6 contracts.
- Must-have only when predictive modeling is used: 1 contract.
- Safely deferred with concrete trigger: 2 contracts.
- Operator decision request emitted: no.

## Next Wave C Task

Proceed to C2: `paper-source-record-v0.1` and `ingest-paper` CLI, unless the operator redirects the C1 classification.

## Post-C2 Review Request

After C2 closure, Claude's post-closure audit flagged that this C1 report was marked `closed_report_ready_for_review` without a formal adversarial review row.

Carmine issued `OPDEC-WAVE-C-C1-REVIEW-REQUEST` on 2026-05-09. C3 method extraction is blocked until Claude reviews this C1 classification or Carmine explicitly overrides the review gate.
