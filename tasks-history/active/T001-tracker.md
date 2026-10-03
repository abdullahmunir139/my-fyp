---
task: T001
title: Defensible FYP proposal rewrite for AgriPulse (Instance 3)
opened: 2026-10-03
status: in-progress
---

# T001 — Tracker

Instance: **3** (agent's own prompt interface, T file pre-written by the user).
Task definition: `../definitions/T001.txt`.

## Goal

Rewrite `deliverables/proposal/proposal.md` so the proposal is **honest,
internally consistent, and survives adversarial review** by a supervisor, an
LLM, or a domain expert — while keeping the section content-types the user
required in Q5, Q6, Q7 and Q8.

## Steps

- [x] 1. Read `SYSTEM.md`, `INDEX.md`, module instruction files
- [x] 2. Verify every referenced file exists (T001.txt, proposal.md, proposal PDF)
- [x] 3. Read the scope of record `chat-history/outputs/A4.md`
- [x] 4. Read Q5-Q8 + A5-A8 to recover the required section content-types
- [x] 5. Extract the submitted PDF text and diff it against `proposal.md`
- [x] 6. `graphify query` for related context
- [x] 7. Load specialist agent skillsets (proposal strategist, statistician,
      technical writer, senior PM, product manager, software architect)
- [x] 8. Build the claim audit — every claim that can be rejected, and its fix
- [x] 9. Rewrite `deliverables/proposal/proposal.md`
- [x] 10. Write `executions/E001.md` with the audit table + rationale
- [x] 11. Index rows: `tasks-history/INDEX.md` (4 files),
      `deliverables/INDEX.md` (proposal.md row updated)
- [x] 12. Contribution record `contribution-history/c002.md` + index row
- [x] 13. `graphify update .` from repo root

## Acceptance criteria

1. No claim in the proposal that the project cannot show on the demo machine.
2. No fabricated data volume. Data is stated as sourced-or-disabled, not guessed.
3. "Zero dependency" is restated precisely and defensibly.
4. The local-run / farmer-use perception gap is closed by an explicit, honest
   deployment-and-use section instead of being left implicit.
5. Cotton is never presented as seeded crop data; it is only a published
   validation reference, and that is stated in the body, not an appendix.
6. Disease diagnosis is removed from the Problem Statement and declared
   out of scope, so the problem statement and the scope cannot contradict.
7. Section content-types match Q5/Q6/Q7/Q8 exactly.
8. Depth stays FYP-appropriate — overview, not manual.
9. Every created file has a complete index row.
10. A contribution record exists for the real work.

## Open questions for the user

- Which crops actually have a citable cost + yield source today? The proposal
  ships a rule ("a crop appears in the dropdown only if its rows are sourced")
  so the answer does not block the rewrite, but the real list decides the
  seed script later.
- The exported PDF/ODT still carry an older title and a 27-tool list. They are
  exports, not the source of truth — flagged for re-export, not edited.
