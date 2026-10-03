---
task: T002
date: 2026-10-03
model: space-bunny
agent: buffy (freebuff)
instance: 2
target: deliverables/proposal/proposal.md
status: in-progress
---

# T002 — Tracker

## The complaint, restated

The proposal reads like a startup pitch rather than a student FYP proposal.
Specifically: outcome/margin language, "future work" framing, a dedicated
deployment section about how a farmer would reach the app, and the offline
design presented as a limitation to be excused rather than a feature.

The user is not asking for less rigour. They are asking for the *voice* to
change: prove the skills, not the business.

## Five reframes to apply

1. **Drop the pitch voice.** No "outcomes", "margins", "revenue", "we would
   rather be approved", "worth more than one that sounds larger". A proposal
   argues a problem is real and the work is doable. It does not sell.
2. **Stop apologising for offline.** "Zero runtime network dependencies" is a
   *property*, stated as a benefit. Cut "works with no internet is a promise /
   zero dependencies is a false claim" and the router-off ritual.
3. **Cut "future work" and "future plans" entirely.** The cuts are the cuts.
   No disease-diagnosis section, no out-of-scope-as-future-work framing, no
   "that is the next project, not this one".
4. **Cut the deployment section.** "How a farmer actually reaches this" is
   explicitly called meaningless — the viva requirement is only that the
   project *runs* so the examiner can see it was built.
5. **Keep the substance that earns marks.** Citations on screen, the SFRI
   method, the PCPA cotton validation figure, the crop-sourcing rule, honest
   labels on every number. These are the CS content.

## Hard constraints from the user

- **Edit `deliverables/proposal/proposal.md` and nothing else.** No PDF, no
  ODT, no binaries. The `.md` is the source of truth; the exports are stale
  and must be re-exported by the student, not by me.
- Teacher's template section order is fixed and must be preserved.
- No invented student data (registration no, email, contact, CGPA).

## Acceptance criteria

- [x] No pitch/margin/outcome language anywhere.
- [x] Offline presented as a positive property, zero apology.
- [x] Zero occurrences of "future work", "future plans", "next project".
- [x] No deployment/reach section.
- [x] Template section order intact.
- [x] Q8 content-types preserved: aim 5 + objectives 6; scope = 1 paragraph
      + 6 points, no sub-headings; FR 12 + NFR 12, plain numbering.
- [x] No claim contradicts `chat-history/outputs/A4.md` (locked scope).
- [x] No invented personal data.

## One conflict flagged to the user

A4 (locked scope of record) says: *"the proposal must state P3 [disease
diagnosis] as future work, not as a solved problem."* T002 says remove all
future-work framing. Both are satisfiable: the honest move is to **drop the
disease problem entirely** — not claim to solve it, and not list it as future
work. Silence satisfies A4's actual requirement (do not claim it as solved)
while honouring T002. Recorded in E002.
