# Canonical State Audit
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

State exactly what exists in OBDK, VRE, and Vibe Science at plan creation. A fresh agent reads this before touching any subsystem so it can distinguish canonical from experimental from missing.

## Authority Stack (highest first)

1. Operator instruction in current session (must be crystallized to file before durable effect)
2. Append-only ledgers (`operator_decisions.md`, `gate_review_log.md`, `changelog.md`) in OBDK and in this plan folder
3. This plan folder + sibling Codex plan folder (coordination control plane)
4. Subsystem canonical control planes (OBDK `analisi_claude/project_plan`, WIKI_VRE `index.md` + `CLAUDE.md`, Phase 10 `02-formal-design-spec.md`)
5. Contracts and tests (executable truth)
6. Chat memory (non-authoritative; cite filesystem before relying on remembered state)

## OBDK State

### Canonical (in production)

- 24 contracts implemented after Cluster D v0.2 substrate close
- Charter `charter-v0.5.md` with §16 catalog
- Python package `obdk/` (loader, CLI, runner, scorer, facade, migrations)
- 1 working recipe `recipes/d0_eaoc_syndecan_upr.yaml` (smoke-test on real GEO data GSE230956, 748KB count matrix, 8 samples)
- 231 pytest passed, ruff clean, contracts=24 fixtures=202 unexpected=0
- Project plan pack `analisi_claude/project_plan/` with 24-row operator_decisions.md (append-only)
- Recovery protocol `analisi_claude/project_plan/01_RECOVERY_PROTOCOL.md`
- Folder map `analisi_claude/project_plan/source_maps/01_kernel_folder_map.md`
- Interop mapping `interop-mapping-v0.1.md`

### Experimental quarantine (must be marked, not deleted)

The following directory contains research-grade overshoot from prior derailment session and must not be treated as canonical:

`vibe-science/blueprints/private/onco-bio-discovery-kernel/.vibe-science/RQ-001-d0-first-cycle/`

Contents:

- `STATE.md`, `PROGRESS.md`, `CLAIM-LEDGER.md`, `ASSUMPTION-REGISTER.md`, `SERENDIPITY.md`
- `RQ.md`
- `00-brainstorm/` with 14 files (context, landscape, gaps, data-audit, hypotheses, triage, A2/A3/A4/A5/B4 memos, brainstorm-review pass1/2/3, B0_gate_verdict, D1/D5/D6 memos)
- `01-stage1/` with `cohort_pmi_audit.md`, `F3_gsva_pre_registration.md`, `TASK16_reference_quantification_preregistration.md`
- `05-reviewer2/pass4-pre-stage1-review.md`

These files contain research-grade scientific discipline that may be useful as reference material but must not be treated as the active implementation plan. Wave A marks them experimental at file level (header block) and at directory level (OVERSHOOT_STATUS.md).

### Missing (required for completion)

| # | Capability | Owner |
|---|---|---|
| 1 | Agent-facing `SKILL.md` wrapper for OBDK | Wave B Task B1 |
| 2 | Cross-system orchestration map | Wave B Task B2 |
| 3 | Paper source bundle ingestion (CLI + record contract) | Wave C Tasks C2, C4 |
| 4 | Method extraction (CLI + record contract) | Wave C Tasks C3, C5 |
| 5 | SPARK-derived script registry | Wave C Task C6 |
| 6 | Sandbox script generation runtime | Wave C Task C7 |
| 7 | Recipe library expansion (≥3 must-have recipes) | Wave C Task C8 |
| 8 | OBDK to VRE export adapter | Wave C Task C9 |
| 9 | OBDK absorbability pre-gate report | Wave C Task C10 |
| 10 | Cluster D v0.1 operator closure (`CLUSTER-D-HAT3-ACCEPT-002` still pending) | Wave A Task A3 |

## VRE State

### Canonical surfaces

- `vibe-science/blueprints/private/WIKI_VRE/`
  - `index.md` — wiki entry point
  - `CLAUDE.md` — agent instructions for wiki
  - `PROTOCOL-wiki-integrated-implementation.md` — integration protocol
  - `PLAN-atomic-completion.md` — completion plan
  - `PROMPT-adversarial-review.md`, `PROMPT-agent-session-preamble.md`, `PROMPT-implementation-step.md`
  - `tools/build-registries.mjs`, `tools/sync-mirror.mjs` — Node-based validators
  - `closures/`, `concepts/`, `coverage/`, `entities/`, etc.

- `vibe-science/blueprints/private/phase9-implementation-plan/`
  - 22+ files implementing Phase 9 Waves 0..6 (capability handshake, objective lock, sanctioned execution, autonomy runtime, multi-agent orchestration, governance audit)
  - **Phase 9 Wave 5 status: in progress (split-series 06d-T5.2..T5.7)**

- `vibe-science/blueprints/private/phase9-vre-autonomous-research-loop/`
  - 9+ files defining Phase 9 spec (autonomous research loop, capability handshake, objective loop, sanctioned execution, kernel-VRE bridge, agent orchestration, acceptance evidence, wave boundaries)

### Phase 10 spec (approved, awaiting implementation gate)

- `vibe-science/blueprints/private/phase10-knowledge-layer/`
  - `01-brainstorming-and-decisions-log.md` — 10 foundational decisions across 17 adversarial review rounds
  - `02-formal-design-spec.md` — formal Phase 10 design
  - `03-vre-existing-state-audit.md` — VRE state audit at Phase 10 design time

### Phase 10 implementation gate (HB-1)

Phase 10 implementation cannot start until two conditions are met:

1. **Phase 9 Wave 5 closure** (Wave 5 split-series 06d-T5.2..T5.7 must all close)
2. **Operator approval gate** via explicit command `vre phase10 implementation-track-start --confirm` (or operator-recorded equivalent decision row)

Wave D of this plan starts with Task D1 to verify HB-1 gate. If gate is not satisfied, Wave D pauses pending Phase 9 Wave 5 closure.

### Missing (required for completion)

| # | Capability | Owner |
|---|---|---|
| 1 | Phase 10 implementation gate verification | Wave D Task D1 |
| 2 | Phase 10 source bundle store (LAW 13 fail-closed) | Wave D Task D2 |
| 3 | Phase 10 wiki compile pipeline | Wave D Task D3 |
| 4 | Phase 10 query agent (durable answers with citations) | Wave D Task D4 |
| 5 | Phase 10 R2 audit binding | Wave D Task D5 |
| 6 | Phase 10 operator steering and goal immutability | Wave D Task D6 |
| 7 | Phase 10 serendipity preservation | Wave D Task D7 |
| 8 | Phase 10 completion report | Wave D Task D8 |

## Vibe Science State

### Canonical

- Repository root files (Vibe Science skill, protocols, agents, schemas)
- Plugin runtime hooks
- LAW catalog (LAW 7 fresh context, LAW 9 confounder harness, LAW 10 crystallize, LAW 11 listen-to-user, LAW 13 provenance-or-declaration in Phase 10 spec)
- R2 ensemble protocol
- Salvagente Rule
- Schema-validated gates

Vibe Science is treated as complete enough for rigor layer use. This plan does not modify Vibe Science core. It only consumes Vibe Science discipline.

### Required integrations

| # | Integration | Owner |
|---|---|---|
| 1 | OBDK evidence-package consumes Vibe-plugin hooks (already in contract: r2_review_status, r2_review_packet_ref, salvagente_seed_ref, claim_ledger_entry_ref) | Wave E Task E3 |
| 2 | Vibe R2 review trigger from OBDK runs | Wave E Task E3 |
| 3 | Vibe Salvagente seed writer when claim killed | Wave E Task E4 |
| 4 | Vibe claim-ledger writer linked to VRE | Wave E Task E4 |

## Cross-System Dependencies

| Dependency | Direction | Blocking | Notes |
|---|---|---|---|
| Phase 10 implementation requires Phase 9 Wave 5 closure | Phase 9 → Phase 10 | YES | HB-1 enforced via task adapter |
| Phase 10 implementation requires operator approval | operator → Phase 10 | YES | HB-1 explicit confirm |
| OBDK to VRE export requires VRE Phase 10 source store | VRE → OBDK | partial | Wave C Task C9 can stage adapter shape; Wave E Task E2 wires runtime |
| OBDK absorbability requires Vibe Science review | Vibe → OBDK | YES | Wave G adversarial review |
| Multi-system trace query requires both VRE Phase 10 and OBDK export adapter | both → trace | YES | Wave E Task E6 |

## Decision Surfaces Awaiting Operator

A complete list lives in `19_operator_decision_register.md`. Summary at plan creation:

1. Cluster D v0.1 operator closure (`CLUSTER-D-HAT3-ACCEPT-002`) — closure or explicit deferral
2. Phase 10 implementation track GO (HB-1 confirm) — required before Wave D starts
3. Reconciliation between this Claude plan and sibling Codex plan — required before either becomes canonical
4. Acceptance of Wave A archive policy (mark experimental vs move to archive subdir vs delete)
5. Public/private boundary for VRE export when Wave C Task C9 is implemented
