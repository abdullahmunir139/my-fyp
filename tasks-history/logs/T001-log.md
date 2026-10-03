---
task: T001
opened: 2026-10-03
instance: 3
---

# T001 — Log

Append-only. One entry per step, in order.

## 2026-10-03

1. **Bootstrap.** Read `SYSTEM.md`, then `INDEX.md`, then
   `instructions/INDEX.md`. Confirmed the three modules this task touches:
   tasks-history (2nd/3rd instance), deliverables, contribution-history.

2. **Instance routing.** The user pointed at
   `tasks-history/definitions/T001.txt` → **2nd instance**, and T001.txt itself
   is stamped `Instance: 3 (agent's own prompt interface)`. The T file already
   exists and already contains the prompt word-for-word, so no new T file was
   created — the append-only rule forbids editing or recreating it.

3. **File existence check (hard gate).** Verified every file the task
   references:
   - `tasks-history/definitions/T001.txt` — present
   - `deliverables/proposal/AgriPulse_Soil-Test_Driven_Farm_Planner.pdf` —
     present
   - `deliverables/proposal/proposal.md` — present
   - `deliverables/proposal/AgriPulse_Soil-Test_Driven_Farm_Planner.odt` —
     present
   - `chat-history/outputs/A4.md` — present
   Gate passed; work started.

4. **Duplicate detection.** `tasks-history/INDEX.md` has a header row and zero
   data rows. `E001.md` does not exist in `executions/`. This is new,
   unindexed work. Proceeded.

5. **Graphify-first discovery.** Ran
   `graphify query "proposal rewrite claims"` from the repo root. Returned 16
   nodes centred on `deliverables/proposal/proposal.md` and its 14 section
   headings. Used it to locate the sections before any filesystem listing.

6. **Read the scope of record.** `chat-history/outputs/A4.md` is stamped
   **LOCKED** and is the authority on scope: 5 pages, 4 modules, 6 routes,
   9 backend packages, 420 reference rows, no ML, P3 as future work, 7-week
   plan. Nothing in the rewrite may contradict it.

7. **Recovered the required content-types from Q5-Q8.**
   - Q5/A5 — build the proposal inside the official template, easy words,
     specialist skills.
   - Q6/A6 — the four problems are compressed to **four short descriptive
     bullets**. This shape is already in the submitted PDF and must survive.
   - Q7 was rejected by the user; Q8/A8 is the surviving structure:
     one combined **Aim and Objective** heading, an aim block (5 numbered
     points, each followed by its description) and an objective block (6, same
     shape); **Scope** = one paragraph + 6 descriptive points, no sub-headings;
     **FR and NFR** = plain `1. 2. 3.` numbering, equal counts, 12 each;
     minimal depth, FYP level.

8. **Extracted the submitted PDF** with `pdftotext` and diffed it against
   `proposal.md`. Found the exports carry a **different title** ("Tells a
   Punjab Farmer" vs "Gives a Punjab Farmer"), a **27-tool** list against the
   markdown's **16-tool** list, and the full 51-FR/20-NFR tables against the
   markdown's condensed 12+12. So `proposal.md` and its exports had already
   drifted. The `.md` is the source of truth per
   `deliverables_instructions.md`; the drift is reported, not silently patched
   into the binary exports.

9. **Loaded the specialist agents** read-only from the sibling repo
   `../specilized-agents-skills-from-agency-agents` (cross-repo protection:
   read only, never written):
   - `sales-proposal-strategist` — no empty adjectives, every claim carries
     evidence, contrast by capability rather than by criticising a competitor.
   - `academic-statistician` — the claim interrogation chain: question,
     measurement, sample, comparison, analysis, inference, decision. A claim
     is as strong as its weakest link. This is what exposed the data claims.
   - `engineering-technical-writer` — short sentences, one idea per point,
     accuracy over polish, every claim traceable.
   - `project-manager-senior` — realistic scope, exact requirements,
     acceptance criteria that can pass or fail.
   - `product-manager` — lead with the user problem, scope creep kills
     projects, say what is out of scope plainly.
   - `engineering-software-architect` — boundary discipline, technology
     choices with stated reasons.

10. **Built the claim audit** (13 claims, full table in `E001.md`). The ones
    that actually break the proposal under adversarial review:

    | # | Claim as written | Why it dies | Fix applied |
    |---|---|---|---|
    | A | "**0 external dependencies**" | The proposal itself lists 16 tools and A4 lists 9 backend + 7 frontend packages. Self-contradicting; an LLM rejects on the first line. | Restated as **0 runtime network dependencies** — no CDN, no external API, no font host, no telemetry, no runtime download. Build-time npm packages named honestly. |
    | B | "420 rows of reference data" as a fact | `app/` holds no code. Nothing is built. The number is a *plan*, presented as an *achievement*. | Every count restated as a week-1 target with a pass/fail gate, not a fact. |
    | C | Cotton figures used as the app's validation, cotton not in the crop list | The 5 crops are wheat, rice, maize, potato, tomato. A cotton check validates the **method**, not the shipped data. As written it implies cotton data ships. | Cotton named explicitly as a **method-validation reference only**, stated in the body, not buried in an appendix. |
    | D | Wheat "has no data right now" per the user, yet 5 crops claimed | Naming crops with no sourced rows is the single easiest rejection. | A hard rule: **a crop appears in the dropdown only if its cost and yield rows are sourced.** Unsourced crops are visibly disabled, not silently guessed. |
    | E | Disease diagnosis written as a solved Problem, then retracted | Reading the problem statement, a supervisor sees 4 problems; the scope then admits one is not solved. Reads as padding. | Removed from the Problem Statement. Declared out of scope in one line with the reason. |
    | F | "How does a farmer use it if it runs locally?" | The strongest attack on the whole project, and the proposal never answers it. | New **Deployment and Use** section: what ships, who installs it, how a farmer reaches it, and what is explicitly not being claimed. |
    | G | "We studied 13 tools" with user counts (15.8M, 2.95 crore, 300+ stations) | Unverifiable third-party numbers, some for a state-funded national system. Any wrong figure discredits the audit. | Competitor analysis **kept** (the user said it is sound), but framed as capability contrast. Unverified reach figures removed; what each tool can and cannot do is kept. |
    | H | "Lighthouse performance ≥ 90" | No Lighthouse run exists and none is planned. | Replaced with a check the student can actually perform and show. |
    | I | "ppm converted to kg/ha **for the farmer's area**" | Wrong on its face — ppm↔kg/ha is a soil depth and density conversion, nothing to do with area. A domain reader catches it instantly. | Corrected to the soil-depth and bulk-density conversion, stated. |
    | J | Present-tense product voice throughout ("the farmer registers once... receives") | The app does not exist. Product voice on unbuilt software reads as over-claiming. | Conditional, planned voice. One explicit line: the project has not started. |
    | K | Proposal says "16 tools"; PDF says 27; `c001.md` says 27 | Three different numbers for the same document. | `proposal.md` states 16 and names them. The export drift is reported to the user, not edited into the binaries. |
    | L | "no machine-learning model of any kind" | Correct and load-bearing, but it invites "so what is the CS content?" | Kept, and answered directly: the contribution is applying a published agronomic method reproducibly and offline, with every figure traceable. |
    | M | Title differs between `proposal.md` and the PDF/ODT | Two titles in one folder. | One title in `proposal.md`; exports flagged for re-export. |

11. **Rewrote `deliverables/proposal/proposal.md`.** Kept the official
    template's section order exactly. Restored the Q6 four-bullet problem
    shape and the Q8 aim/objective, scope and 12+12 requirements. Added the
    Deployment and Use section and the crop-sourcing rule. Cut the depth to
    overview level as the user asked. Left competitor analysis intact.

12. **Wrote `executions/E001.md`** with the full audit, the reasoning, and the
    questions the user still has to answer.

13. **Index rows appended** — 4 rows in `tasks-history/INDEX.md`
    (T001.txt repair row, tracker, log, execution), the `proposal.md` row
    updated in `deliverables/INDEX.md`.

14. **Contribution record `c002.md`** appended — a proposal rewrite is real
    work and the rules require it in the same turn.

15. **`graphify update .`** from the repo root.
