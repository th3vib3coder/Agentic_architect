# Wave B Fresh-Agent Simulation

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Simulate a fresh agent recovering the integrated system without chat memory. This validates Wave B Task B5.

## Simulation Input

The simulation followed the first ten moves from `plan/21_handoff_card.md` after Wave B edits.

## Command

```powershell
$base='C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill'
$checks=[ordered]@{
'Agentic README' = Join-Path $base 'Agentic_architect\README.md'
'Agentic wiki index' = Join-Path $base 'Agentic_architect\wiki\index.md'
'Active wave ledger' = Join-Path $base 'Agentic_architect\ledger\active_wave.md'
'GOAL doctrine' = Join-Path $base 'Agentic_architect\plan\23_project_goal_and_implementation_doctrine.md'
'Plan index' = Join-Path $base 'Agentic_architect\plan\00_INDEX.md'
'Purpose anchor' = Join-Path $base 'Agentic_architect\plan\02_purpose_anchor.md'
'Master sequence' = Join-Path $base 'Agentic_architect\plan\04_master_sequence.md'
'Wave B file' = Join-Path $base 'Agentic_architect\plan\10_wave_b_agent_entrypoints.md'
'OBDK SKILL' = Join-Path $base 'vibe-science\blueprints\private\onco-bio-discovery-kernel\SKILL.md'
'VRE index' = Join-Path $base 'vibe-science\blueprints\private\WIKI_VRE\index.md'
'Orchestration map' = Join-Path $base 'Agentic_architect\plan\system_orchestration_map.md'
'Decision boundaries' = Join-Path $base 'Agentic_architect\plan\05_decision_boundaries.md'
}
foreach($kv in $checks.GetEnumerator()){ "$($kv.Key): $(Test-Path -LiteralPath $kv.Value)" }
$active=Get-Content -Raw (Join-Path $base 'Agentic_architect\ledger\active_wave.md')
($active -split "`n" | Where-Object { $_ -match 'active_wave|active_wave_file|blocked_by' })
```

Exit code: 0

```text
Agentic README: True
Agentic wiki index: True
Active wave ledger: True
GOAL doctrine: True
Plan index: True
Purpose anchor: True
Master sequence: True
Wave B file: True
OBDK SKILL: True
VRE index: True
Orchestration map: True
Decision boundaries: True
active_wave: B
blocked_by: none
active_wave_file: plan\10_wave_b_agent_entrypoints.md
```

## Fresh-Agent Recovery Result

| Required identification | Result |
|---|---|
| OBDK path | `vibe-science/blueprints/private/onco-bio-discovery-kernel` via README, SKILL, and system map |
| VRE path | `vibe-science/blueprints/private/WIKI_VRE` via handoff card and system map |
| Phase 10 path | `vibe-science/blueprints/private/phase10-knowledge-layer` via system map and canonical audit |
| Vibe Science path | `vibe-science` repository root and protocol surfaces via handoff card |
| Validation commands | OBDK `pytest`, `ruff`, `contracts validate`; VRE registry commands in handoff card |
| Active wave | `B` via `ledger/active_wave.md` |
| Operator escalation points | `plan/05_decision_boundaries.md` |

## Issues Found

One pre-existing naming drift was found and corrected during Wave B:

- Wave B referenced non-existent `14_agent_start_here_card.md`.
- The actual card is `21_handoff_card.md`.
- `10_wave_b_agent_entrypoints.md` was corrected in source and mirror to reference `21_handoff_card.md`.

## Verdict

The fresh-agent simulation passes author-side. The system is discoverable without chat-history path hints. Claude Code must still review before Wave B can close.
