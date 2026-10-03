---
task: T002
date: 2026-10-03
model: space-bunny
agent: buffy (freebuff)
instance: 2
---

# T002 — Action Log

1. **Pre-work file check.** `tasks-history/definitions/T002.txt` present. It
   names no media file, so the media rule does not block. Proceeded.

2. **Tooling note.** `read_files` rejected plain string paths three times
   (serialised as `{"$text": ...}` instead of a string). Worked around with
   the `{path, offset, limit}` object form and `code_search`. No impact on
   the work.

3. **Read the rules.** `SYSTEM.md`, `INDEX.md`,
   `instructions/tasks_history_instructions.md`,
   `instructions/deliverables_instructions.md`,
   `instructions/contribution_history_instructions.md`.

4. **Read the prior work.** `tasks-history/executions/E001.md` and the current
   `deliverables/proposal/proposal.md` (revision 2). T002 is a *reversal* of
   several T001 decisions, so both had to be read before editing.

5. **Read the locked scope.** `chat-history/outputs/A4.md`. Confirmed: 5 pages,
   4 modules, no ML, 9 backend packages, P3 = disease = not covered. This is
   the constraint T002 must not violate.

6. **Extracted the teacher's template** (`1-FYP Proposal Template.docx`) to get
   the mandated section list, so no required heading gets deleted:
   header → DATE → Project Code → Project Title → Tools to be used →
   Problem Statement → Aim and Objective → Scope of the Project →
   Functional Requirements → Non-Functional Requirements → Particulars of the
   students → Signatures → Remarks → Signatures and Date.

7. **Extracted the locked PDF** text. Confirmed the teacher's Problem
   Statement carries exactly **three** bullets, and that the teacher's own
   version already frames offline as an aim ("run on one laptop with the
   router switched off") rather than a limitation. T002's complaint is
   therefore against the *revision-2 additions*, not the teacher's content.

8. **Audited the pitch voice.** Line-level pass over revision 2. The startup
   framing is concentrated in six places: the frontmatter `revision` note, the
   "Status" callout, the Tools "on the word zero dependencies" apology, the
   Problem Statement "why this matters to the review" meta-commentary, the
   entire **Deployment and Use** section, and **Appendix B — What Is NOT
   Claimed** plus the "we have not overclaimed" Remarks item.

9. **Decided the disease-problem resolution** (see tracker): remove it
   entirely rather than re-label it future work. Satisfies A4's real
   requirement without T002's banned framing.

10. **Rewrote `deliverables/proposal/proposal.md`.** Only that file. No PDF,
    no ODT, no binaries touched.

11. **Verified by grep** for banned tokens: "future work", "future plan",
    "next project", "margin", "revenue", "outcomes", "deployment".

12. **Appended index rows** to `tasks-history/INDEX.md` and wrote
    `executions/E002.md`.

13. **Contribution record.** T002 modifies the proposal deliverable, which is
    a real work item, so `contribution-history/c003.md` is required by the
    forced rule. Flagged to the user, since the user said "edit the proposal
    file only" — read that as *do not edit other deliverables*, not as
    *skip the engine's own bookkeeping*, which `SYSTEM.md` marks FORCED.
