# Architecture References

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

This page records external architecture references. A reference is not a scope adoption. It is a pattern source that may inform a later wave only after explicit operator decision.

## ARCH-REF-001 — OpenClaw-Style Local Automation Patterns

| Field | Value |
|---|---|
| Status | reference-only |
| Source | OpenClaw-style local automation architecture, discussed by operator on 2026-05-07 |
| Applies later to | Optional local cross-agent bridge after core wiki/ledger/recovery base is stable |
| Does not change | Wave 0, Wave A, OBDK completion scope, VRE Phase 10 scope, Vibe Science role |

## Patterns Worth Studying Later

- persistent local job queue;
- filesystem-backed agent state;
- skills/config as readable files;
- sandbox and permission model;
- heartbeat and wake/resume;
- audit log;
- multi-channel transport as a concept.

## Explicit Non-Adoption Boundaries

The integrated system does not become:

- a general personal automation assistant;
- a broad desktop automation platform;
- an email/calendar/chat/CRM agent;
- a system with unrestricted filesystem authority;
- a replacement for Vibe Science, VRE, or OBDK.

## Future Trigger

Open a dedicated bridge design task only when manual Claude/Codex handoff becomes a bottleneck or when the operator explicitly requests the local cross-agent bridge wave.

## ARCH-REF-002 — Karpathy LLM Wiki Pattern Hardening For WIKI_VRE

| Field | Value |
|---|---|
| Status | reference-only |
| Source | Karpathy LLM Wiki pattern plus agentmemory-style retrieval/lifecycle inspiration, discussed by operator on 2026-05-09 |
| Applies later to | WIKI_VRE primarily; informs Wave D / Phase 10 design |
| Does not change | Wave C, Wave D execution scope, OBDK typed records, Vibe Science CLAIM-LEDGER discipline, operator decision authority, or any current toolchain |

### Binding Rule

Wiki pages are views, not stores. If a wiki page conflicts with a typed record, ledger row, source bundle, or operator decision, the store wins and the wiki must be corrected.

### Borrow

- three-layer raw / wiki / schema separation;
- frontmatter status lifecycle (`draft`, `reviewed`, `stale`, `superseded`);
- hybrid search using BM25 + vector + graph as read-only retrieval over markdown, if the pain becomes real;
- session replay and audit;
- provenance/citation trace using file, line, and commit references;
- `Contradictions / Tensions` section per page;
- append-only `log.md`, aligned with existing ledger discipline.

### Reject

- LLM-generated confidence scoring as authority, because it is incompatible with LAW 9;
- auto-forget / decay, because it is incompatible with append-only ledger discipline;
- knowledge graph extraction as primary structure, because automatic markdown graph extraction is fragile;
- wholesale adoption of NEXUS, OmegaWiki, SwarmVault, Synthadoc, Link, or similar projects without later operator review.

### Authority Boundaries

- Store layer: typed records, contracts, CLAIM-LEDGER, operator decisions, and Phase 10 source bundles are sources of truth.
- View layer: WIKI_VRE markdown pages are synthesis pages with backlinks to the store.
- Raw layer: Phase 10 source bundles follow HB-1..HB-13.

### Trigger To Revisit

- Wave D / Phase 10 implementation begins;
- the operator reports "where is decision/claim/method X?" pain;
- not before Wave G validation unless the operator explicitly opens a design decision.

### Future Candidate

Wave H may evaluate a local retrieval-only layer if retrieval pain materializes. This reference does not authorize building `wiki_lint`, `wiki_search`, backlink, graph, or MCP tooling now.
