# Wave A Stale Prose Sweep

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Scope

Wave A Task A4 searched OBDK `analisi_claude/project_plan/plan/` and `analisi_claude/project_plan/wiki/` for stale tokens:

- `23 contracts`
- `190 fixtures`
- `Stage 1 BLOCKED`
- `Wave 1 drafts pending`
- `Pass 4 BLOCK`
- `218 passed`
- `kernel as it exists at 23 contracts`

## Findings

| Token | File | Line | Text | Disposition |
|---|---|---:|---|---|
| `23 contracts` | `analisi_claude/project_plan/plan/02_wave_queue.md` | 60 | `real D0 cycle on the kernel as it exists at 23 contracts, before further` | Forward-looking and stale, but outside Wave A allowed write set. Operator decision required before edit. |
| `kernel as it exists at 23 contracts` | `analisi_claude/project_plan/plan/02_wave_queue.md` | 60 | `real D0 cycle on the kernel as it exists at 23 contracts, before further` | Same hit as above; operator decision required before edit. |
| `Pass 4 BLOCK` | `analisi_claude/project_plan/plan/06_d0_first_cycle_roadmap.md` | 80 | `2026-05-07 after R2 Pass 4 BLOCK-1.` | Historical event reference, not stale active-state prose. Left unchanged. |

## Decision Needed

Wave A allowed stale prose edits in:

- `analisi_claude/project_plan/plan/00_current_state.md`
- `analisi_claude/project_plan/plan/06_d0_first_cycle_roadmap.md`

It did not include `analisi_claude/project_plan/plan/02_wave_queue.md`.

Codex appended `OPDEC-WAVE-A-STALE-PROSE-001` and did not edit `02_wave_queue.md`.
