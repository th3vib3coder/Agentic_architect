# Wave B Entrypoint Check

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Purpose

Wave B Task B4 selected the report-recipe path rather than an OBDK pytest file. This avoids modifying OBDK tests during an entrypoint-only wave while still making the validation commands durable and reviewable.

## Scope

Validated surfaces:

- OBDK `SKILL.md`
- OBDK `wiki/index.md`
- OBDK `wiki/contracts.md`
- OBDK `wiki/recipes.md`
- OBDK `wiki/scripts.md`
- OBDK `wiki/runs.md`
- Agentic plan `system_orchestration_map.md`
- Agentic plan `21_handoff_card.md`

## Command 1 — Required File Presence

```powershell
$paths = @(
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\SKILL.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\wiki\index.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\wiki\contracts.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\wiki\recipes.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\wiki\scripts.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\wiki\runs.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect\plan\system_orchestration_map.md',
'C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect\plan\21_handoff_card.md'
)
foreach ($path in $paths) { "$([System.IO.Path]::GetFileName($path)): $(Test-Path -LiteralPath $path)" }
```

Exit code: 0

```text
SKILL.md: True
index.md: True
contracts.md: True
recipes.md: True
scripts.md: True
runs.md: True
system_orchestration_map.md: True
21_handoff_card.md: True
```

## Command 2 — Required SKILL.md Sections

```powershell
$skill='C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel\SKILL.md'
$tokens=@('## Purpose','## When To Invoke OBDK','## When NOT To Invoke OBDK','## Available Commands','## Planned Wave C Commands','## Output Interpretation','## Escalation Rules','## Cross-System Links','## Anti-Derailment Hooks')
foreach ($token in $tokens) { "$token => $([bool](Select-String -LiteralPath $skill -Pattern ([regex]::Escape($token)) -Quiet))" }
```

Exit code: 0

```text
## Purpose => True
## When To Invoke OBDK => True
## When NOT To Invoke OBDK => True
## Available Commands => True
## Planned Wave C Commands => True
## Output Interpretation => True
## Escalation Rules => True
## Cross-System Links => True
## Anti-Derailment Hooks => True
```

## Command 3 — Current CLI Reality Check

```powershell
python -m obdk.cli --help
```

Working directory:

`C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel`

Exit code: 0

```text
usage: obdk [-h] {contracts,run,harvest-geo} ...

positional arguments:
  {contracts,run,harvest-geo}
    run                 execute a recipe and archive smoke-run evidence
    harvest-geo         download one real GEO supplementary file

options:
  -h, --help            show this help message and exit
```

## Command 4 — OBDK Plan Pack

```powershell
python -m pytest tests/test_project_plan_pack.py -q
```

Exit code: 0

```text
..........                                                               [100%]
10 passed in 0.32s
```

## Command 5 — Contract Baseline

```powershell
python -m obdk.cli contracts validate --charter charter-v0.5.md
```

Exit code: 0

```text
contracts=24 fixtures=202 unexpected=0
```

## Command 6 — Plan Mirror Integrity

```powershell
$source='C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\integrated-system-claude-plan'
$mirror='C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect\plan'
$files=@('00_INDEX.md','10_wave_b_agent_entrypoints.md','21_handoff_card.md','system_orchestration_map.md')
foreach($file in $files){
  $a=Get-FileHash -Algorithm SHA256 -LiteralPath (Join-Path $source $file)
  $b=Get-FileHash -Algorithm SHA256 -LiteralPath (Join-Path $mirror $file)
  "$file source_equals_mirror=$($a.Hash -eq $b.Hash)"
}
```

Exit code: 0

```text
00_INDEX.md source_equals_mirror=True
10_wave_b_agent_entrypoints.md source_equals_mirror=True
21_handoff_card.md source_equals_mirror=True
system_orchestration_map.md source_equals_mirror=True
```

## Command 7 — Mantra Coverage

```powershell
$root='C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect'
$files=Get-ChildItem -LiteralPath $root -Recurse -Filter *.md -File
$with=($files | Where-Object { Select-String -LiteralPath $_.FullName -Pattern 'Il piano e il vangelo' -Quiet }).Count
"total=$($files.Count) with_mantra=$with missing=$($files.Count-$with)"
```

Exit code: 0

```text
total=46 with_mantra=46 missing=0
```

## Verdict

Entrypoint check passes author-side. Claude Code must still review the Wave B artifact; Codex does not self-ACCEPT.
