# Codex Adversarial Review — Orthodox Execution Patch
## Orthodox Mantra

**Il piano e il vangelo e noi siamo ortodossi che seguono il vangelo parola per parola.**

Every implementation step and every minimal variation must update the project wiki, implementation ledger, incremental changelog, relevant README, and GitHub remote, unless an operator-recorded waiver explicitly says otherwise.

## Scope

Codex reviewed the Claude-authored integrated system plan after the operator requested two explicit mantras:

1. the plan is the gospel and agents execute it word-for-word;
2. every implementation step and every minimal variation updates wiki, ledgers, changelog, README, and GitHub.

This file records the Codex-side review and the patch applied to the Claude plan. Codex authored this patch, so Codex must not issue final ACCEPT on it. Claude Code should review this file and the touched plan files before operator closure.

## Review Findings

### Finding 1 — [P1] Orthodox execution was implicit, not enforced

The plan already warned against derailment, but it did not carry the operator's exact "piano vangelo" rule into the surfaces a fresh agent reads first. This allowed future agents to treat the plan as advisory. Patch: `README.md`, `02_purpose_anchor.md`, and `21_handoff_card.md` now include the explicit mantra and its operational consequence.

### Finding 2 — [P1] Wiki / ledger / changelog / README / GitHub evidence was not a universal invariant

The plan mentioned ledgers and review, but it did not require the full durable-evidence packet for every step and every variation. Patch: `04_master_sequence.md`, `06_multi_agent_pairing.md`, `16_atomic_task_backlog.md`, `17_test_strategy.md`, `20_adversarial_review_packet.md`, and `21_handoff_card.md` now make the packet mandatory.

### Finding 3 — [P2] Plan file count and unfilled-stub discipline drifted

Adding this review file changes the plan from 23 to 24 files. Patch: `README.md`, `00_INDEX.md`, and `17_test_strategy.md` now use 24. The pending fields in `19_operator_decision_register.md` were replaced with explicit pending-operator text so exact-token scans are meaningful.

## Files Patched

| File | Reason |
|---|---|
| `README.md` | Add operator mantras and update file-count language. |
| `00_INDEX.md` | Index this review artifact and extend amendment rule with orthodox packet. |
| `02_purpose_anchor.md` | Make the orthodox execution contract part of the authority layer. |
| `04_master_sequence.md` | Add orthodox packet to wave closure and GitHub push discipline. |
| `06_multi_agent_pairing.md` | Add evidence-packet fields to implementer handoff and reviewer audit. |
| `16_atomic_task_backlog.md` | Add universal task epilogue inherited by every atomic task. |
| `17_test_strategy.md` | Add standing tests for mantra and evidence-packet enforcement. |
| `19_operator_decision_register.md` | Replace ambiguous pending text with explicit pending status. |
| `20_adversarial_review_packet.md` | Add review questions for orthodox execution and evidence packet. |
| `21_handoff_card.md` | Add post-completion operational mantra and stop-safe evidence checks. |
| `22_codex_adversarial_review.md` | Record this review and patch rationale. |

## Required Claude Review Questions

Claude Code should verify:

1. Does the patch implement the two operator-requested mantras without changing the plan's objective?
2. Does the evidence packet requirement appear in all surfaces a fresh agent will read before execution?
3. Does the GitHub push requirement include a safe waiver path for environments where push is impossible?
4. Does the added review artifact avoid becoming a zone morte by being indexed?
5. Do exact-token and line-count scans remain clean after this patch?

## Codex Verdict

Codex disposition: **AUTHOR_PATCH_READY_FOR_CLAUDE_REVIEW**.

Codex does not issue ACCEPT on this patch because Codex authored it. Per adversarial-pairing discipline, Claude Code is the counter-reviewer for this revision.
