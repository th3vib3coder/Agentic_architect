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
