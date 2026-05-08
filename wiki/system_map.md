# System Map

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Subsystems

| Subsystem | Local path | Current role |
|---|---|---|
| Agentic Architect | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect` | Operational repo and implementation orchestration surface |
| Canonical plan | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\integrated-system-claude-plan` | Binding plan and wave sequence |
| Versioned plan mirror | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\Agentic_architect\plan` | GitHub-tracked plan copy used by fresh cloned agents |
| OBDK | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\onco-bio-discovery-kernel` | Paper-to-evidence analysis kernel; stays in place locally |
| OBDK private remote | `https://github.com/th3vib3coder/onco-bio-discovery-kernel` | Private mirror of OBDK selected by `OPDEC-OBDK-REMOTING-001`; initial commit `44cccf5b520444050eb114b4fecc08f7bcc2250d`, Wave B entrypoint provider commit `5745de3159062a4d9cf3ffcde2be9fb6436cc602` |
| VRE | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\WIKI_VRE` | Durable research memory wiki |
| Phase 10 | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\phase10-knowledge-layer` | VRE missing layer, gated by Phase 9 Wave 5 closure |
| Phase 9 | `C:\Users\Test-User\Desktop\Tesi_Python_scRNA\nuove_skill\vibe-science\blueprints\private\phase9-implementation-plan` | Upstream gate for Phase 10 |

## External Architecture References

Reference architectures are listed in `wiki/architecture_references.md`. They are pattern sources only. They do not alter subsystem ownership or active wave scope.

## Navigation Rule

An agent starts here, then reads:

1. `README.md`
2. `wiki/index.md`
3. `ledger/active_wave.md`
4. plan `23_project_goal_and_implementation_doctrine.md`
5. the active wave file

In a fresh GitHub clone, the agent reads those plan files under `plan/`.

## Evidence Rule

Any new path created during implementation must appear in at least one of:

- this wiki;
- a subsystem wiki;
- `ledger/change_log.md`;
- `reports/`.

## Remoting Rule

Agentic Architect is public. OBDK is private. OBDK changes must be committed and pushed to the private OBDK remote, while orchestration decisions and cross-system status are mirrored here in `Agentic_architect`.

## Wave B Entrypoints

Wave B created OBDK `SKILL.md`, OBDK top-level `wiki/`, and `plan/system_orchestration_map.md`. Fresh agents should now recover OBDK by reading OBDK `SKILL.md` before attempting CLI usage.
