# Wave C C2 Author Handoff Report

## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Scope

Wave C C2 implemented the first OBDK paper/source intake surface:

- new contract: `contracts/paper-source-record-v0.1.md`;
- new module: `obdk/paper_ingest.py`;
- CLI command: `python -m obdk.cli ingest-paper --pdf <path> --out <dir>`;
- charter baseline: `contracts=25 fixtures=208 unexpected=0`;
- OBDK private provider commit after Claude F1 fix: `01e3d6c4a76519f8b294894fb0163fae79372d51`.

No Wave C C3 method-extraction task has started.

## Pre-Output Failure Modes

| ID | Failure mode | Result |
|---|---|---|
| FM-1 | Loader cannot discover the new contract from `charter-v0.5.md` | Falsified by `contracts=25 fixtures=208 unexpected=0` |
| FM-2 | `ingest-paper` fabricates missing bibliographic metadata | Falsified: generated record leaves `authors=[]`, `year=null`, `doi_or_pmid=null`, and marks metadata pending |
| FM-3 | Interop mapping silently drifts after charter insertion | Caught by full pytest, then fixed; `tests/test_interop_mapping.py` now passes |
| FM-4 | New files are dead recovery surfaces | Falsified by OBDK source-map/wiki/README/ledger updates and Agentic handoff rows |
| FM-5 | Binary PDF fallback path is untested or mislabels garbage text as reliable extraction | Falsified by persistent PDF-bytes fixture, RED title failure, explicit `binary_utf8_fallback`, filename-derived fallback title, and fallback operator note |

## TDD Evidence

| Step | Command | Exit | Output |
|---|---|---:|---|
| RED | `python -m pytest tests/test_paper_ingest.py -q` | 1 | `ModuleNotFoundError: No module named 'obdk.paper_ingest'` |
| GREEN | `python -m pytest tests/test_paper_ingest.py -q` | 0 | `3 passed in 1.85s` |
| Mutation | inline Python checksum mutation | 1 expected | `AssertionError: MUTATION_EXPECTED_FAIL: checksum mismatch was detected` |
| F1 RED | `python -m pytest tests/test_paper_ingest.py -q` after adding binary PDF fallback test | 1 | `1 failed, 3 passed`; title was `%PDF-1.4` instead of filename-derived `synthetic paper` |
| F1 GREEN | `python -m pytest tests/test_paper_ingest.py -q` after fallback fix | 0 | `4 passed in 2.67s` |
| F1 Mutation | inline Python fallback-status mutation | 1 expected | `AssertionError: MUTATION_EXPECTED_FAIL: binary PDF fallback must not be reported as text_passthrough` |

The first attempted bare `pytest` command failed because `pytest` was not on the PowerShell PATH. The meaningful RED was rerun with `python -m pytest`.

## Fresh Verification

| Command | Exit | Output |
|---|---:|---|
| `python -m pytest tests/test_paper_ingest.py -q` | 0 | `4 passed in 2.67s` |
| `python -m pytest tests/test_contract_loader.py -q` | 0 | `183 passed in 194.86s` |
| `python -m pytest tests/test_interop_mapping.py -q` | 0 | `8 passed in 0.44s` |
| `python -m pytest tests/test_project_plan_pack.py -q` | 0 | `10 passed in 0.31s` |
| `python -m obdk.cli contracts validate --charter charter-v0.5.md` | 0 | `contracts=25 fixtures=208 unexpected=0` |
| `python -m ruff check obdk/paper_ingest.py tests/test_paper_ingest.py` | 0 | `All checks passed!` |
| `python -m pytest --tb=short -q` | 0 | `245 passed in 203.25s` |

## Review Request

Codex authored this patch and does not issue ACCEPT. Required next gate is
Claude/Carmine adversarial re-review of Wave C C2 F1, focusing on:

1. whether the persistent PDF-bytes fixture closes Claude F1 P2 path (a);
2. whether `binary_utf8_fallback` plus filename-derived title and operator note is the right no-dependency behavior;
3. whether `--pdf` should remain as-is until a later operator decision on `pypdf` or source flag naming;
4. whether C3 should start only after re-review or can continue under Wave C execution discipline.
