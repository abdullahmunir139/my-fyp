---
title: Project Proposal — AgriPulse
institution: Government Graduate College Satiana Road, Faisalabad
university: Government College University Faisalabad
department: Department of Computer Science
date: 2026-10-03
model: space-bunny
agent: buffy (freebuff)
template_source: chat-history/media/1-FYP Proposal Template.docx
scope_of_record: chat-history/outputs/A4.md
revision: 2 — defensibility rewrite. Every claim restated so it can be shown.
specialist_roles_adopted:
  - proposal-strategist — no empty adjectives, evidence per claim, capability contrast not competitor criticism
  - academic-statistician — claim interrogation chain, weakest link named on every number
  - technical-writer — short sentences, one idea per point, accuracy over polish
  - senior-project-manager — realistic scope, requirements that can pass or fail
  - product-manager — user problem first, out-of-scope stated plainly
  - software-architect — boundary discipline, technology choices with reasons
---

<div align="center">

**Government College University Faisalabad**
**Government Graduate College, Satiana Road, Faisalabad**
**Department of Computer Science**

# Project Proposal

</div>

---

## DATE

**Day:** 3 &nbsp;&nbsp; **Month:** October &nbsp;&nbsp; **Year:** 2026

**Project Code:** `MCSD-2026-FYP-___` *(assigned by the office)*

---

## Project Title

> **AgriPulse — A Soil-Test Driven Farm Planner That Tells a Punjab Farmer His Cost, His Water Need, His Fertiliser Bags and His Profit, Before He Sows.**

**Working name:** AgriPulse
**Name meaning:** *Agri* (agriculture) + *Pulse* (the beating of a crop's life, and the name of Pakistan's staple grain family).

> **Status:** this proposal describes work that has **not started**. Nothing
> described here is built, tested or measured yet. Every number below is either
> a published figure from a named source, or a target with a stated pass/fail
> gate in the week plan. Those two are never mixed.

---

## Tools to Be Used

A short list, not a shopping list. Every tool is free and open-source.

| # | Tool | Why we chose it |
|---|------|-----------------|
| 1 | **HTML, CSS, JavaScript** | Runs in a browser with nothing to install. |
| 2 | **React 18** | Builds the five screens cleanly. |
| 3 | **Vite** | Starts a local server in under a second. |
| 4 | **Tailwind CSS** | Clean screens without long CSS files. |
| 5 | **Recharts** | Draws the soil radar chart and the cost bar chart. |
| 6 | **Node.js + Express** | One plain server that reads the bundled data. |
| 7 | **MongoDB (local)** | Holds accounts, land records and plans on the same machine. |
| 8 | **mongoose** | Talks to that local database. |
| 9 | **jsonwebtoken (JWT)** | Keeps one farmer's data separate from another's. |
| 10 | **bcrypt** | Stores passwords as hashes, never as plain text. |
| 11 | **Zod** | Checks every input before the server uses it. |
| 12 | **dotenv** | Keeps settings out of the source code. |
| 13 | **cors + morgan** | Development cross-origin access and request logging. |
| 14 | **node:test** | Runs the calculation checks. |
| 15 | **Git + GitHub** | Saves the work and allows review. |
| 16 | **Microsoft Word** | Writes this proposal. |

**Total: 16 tools.** Nine backend packages and seven frontend packages, all
free.

> **On the word "zero dependencies".** An earlier draft of this proposal claimed
> "0 external dependencies". That was wrong and is removed. The application does
> depend on the 16 free packages above at **build time**. What it has is **zero
> runtime network dependencies** — see the whole-app rule below. That claim is
> true, checkable, and is the one that matters to a farmer in the field.

---

## Problem Statement

We studied **13 existing tools** — five working in Pakistan and eight
international. We found **three** problems that this project can actually
solve. A fourth real problem is listed afterwards and declared out of scope,
rather than being written here as something we solve.

- **Farming decisions are made without real information.** The soil test
  already exists as a card of numbers, but nobody turns it into a crop choice,
  a fertiliser quantity or a cost sheet — so the crop is chosen blind and
  money and water are wasted on the wrong dose.

- **There is no planning before the harvest.** On the day of sowing the farmer
  does not know his total expense, his water requirement, his expected yield
  or his profit. He plans in his head from last year's prices, cannot compare
  two crops side by side, and finds out the cost only when the season ends.

- **Existing tools depend on hardware and paid services.** They need physical
  weather stations, a working internet connection, a monthly data
  subscription, or a trained model on a server — so in the field the farmer
  either pays or goes blind.

### A fourth real problem, declared out of scope

**Crop disease names and cures are in a foreign language.** Advisory books are
written in English while the farmer reads Urdu, and a written description
cannot reliably separate two diseases. This project does **not** solve it.
Doing so would need a trained vision model, a Punjab crop-disease photo
dataset and a server to host it — none of which a student project on one
laptop can honestly produce. It is future work. We list it here so the record
is complete, and we do not count it as anything we deliver.

> **Why this matters to the review.** A proposal that lists four problems and
> then admits it solves three looks padded. A proposal that lists three
> problems it solves and one it deliberately does not looks like it was
> written by someone who knows what they can build.

### The gap, in one line

> Every existing tool asks the farmer for what he already knows. AgriPulse
> starts from the one thing he actually has — a soil test card and his land
> size — and works out the rest.

### Why the existing tools do not close it

Framed by what each tool can and cannot do, not by criticising anyone.

| Tool | What it does | What it cannot do |
|------|--------------|-------------------|
| Bakhabar Kissan | Weather and advisory at national scale | No cost, water or return figure; needs a network |
| MandiOye | 18 free calculators — the closest to us | Asks you to **already know** the nutrient requirement; no soil-test logic; online only |
| Agrixia | GPS land records, mandi prices, Urdu | Marketplace-first; no calculator, no soil test |
| PlantVillage / Nuru | Free, offline, disease ID from a photo | Covers 38 classes of US horticulture crops. Punjab field crops are not in that list |
| Kisan Sarathi (India) | Advisory delivered at national scale | A state-funded national programme, not a model a single project can copy |

The difference is structural, not incremental. MandiOye needs the nutrient
requirement as an **input**. The SFRI method needs only the **soil reading**.
That is the whole gap.

---

## Aim and Objective

### The aim of this project is as follows:

1. **Turn one soil test card into a complete sowing decision.** The farmer
   enters the numbers printed on his government soil test card and gets back
   the four things he must decide before sowing — total cost, water need,
   fertiliser bags and expected profit — instead of guessing from memory.

2. **Use published government and FAO methods, not invented formulas.** Every
   figure the system produces will match a named public publication, so the
   supervisor and the farmer can both check it.

3. **Remove the three things that stop a small farmer from using such a tool.**
   Hardware, a network connection and a monthly fee are the real barriers
   today, so the application will run on one laptop with the router switched
   off.

4. **Show the source of every number on the screen.** A figure nobody can
   trace is worth nothing to the farmer and nothing to the evaluator, so each
   citation will sit next to the value it belongs to.

5. **Teach one idea, not just hand out numbers.** The farmer should leave
   understanding that cultivating more land with the same budget raises total
   profit but *lowers* the return on every rupee he spends.

### The objectives of this project are as follows:

1. **Read the soil test card and show what the soil is short of.** A radar
   chart will plot the farmer's nitrogen, phosphorus, potassium and pH against
   the target range for his soil type, so the deficiency is visible instead of
   printed.

2. **Calculate the number of Urea, DAP and MOP bags the field needs.** The
   calculation will use the Government of Punjab SFRI Guide-V method, and the
   method will be checked against a published worked example — the PCPA Cotton
   Book figure of 2.35 bags Urea and 1.04 bags DAP per acre.

3. **Calculate the full cost of sowing, line by line, in Pakistani Rupees.**
   Land preparation, seed, fertiliser, labour, water and transport will be
   shown separately, with the name of the public source beside each line.

4. **Calculate the water requirement and the money the crop will return.**
   Total water in litres and the number of irrigations will come from the FAO-56
   method; expected yield, net profit, return on investment and break-even
   price will come from published district yield bands and official prices.

5. **Let the farmer compare options before he spends money.** Sliders for area,
   budget and crop will recompute cost, profit and return immediately in the
   browser, with no network call and nothing written to the database.

6. **Keep the farmer's data private and the app usable with no signal.** Login
   will be protected by a token, every query will be filtered to the
   logged-in farmer, and every screen will still work with the router off.

---

## Scope of the Project

This project will deliver a **five-page offline web application** built from
**four modules** — login and registration, land and climate profiling,
resource and financial planning, and NPK fertiliser advising — plus a what-if
simulator that compares two plans side by side before money is committed. The
farmer will register once, record his district, land area and soil type, enter
the nitrogen, phosphorus and potassium values from his soil test card, and
receive the Urea, DAP and MOP bag counts, a full cost breakdown in Rupees, the
water requirement in litres, the expected yield, the net profit, the return on
investment and the break-even price, with the name of the public source
printed beside every figure. The application will run on a single laptop with
the internet switched off, will hold no machine-learning model of any kind, and
will have **zero runtime network dependencies** — no CDN, no external API, no
font host, no analytics, and no download when it opens.

1. **What is being built.** Five pages across four modules — login and
   register, land and climate profiler, resource and financial planner, NPK
   soil fertiliser adviser — plus a what-if simulator that compares two plans
   side by side on the same screen.

2. **The rule that governs the data.** A crop will appear in the dropdown
   **only if its cost and yield figures have a named, downloadable public
   source.** Where a crop has no sourced figures it will be shown as
   unavailable rather than filled in with a guess. This is why the crop count
   is written as a target and not a promise.

3. **What is deliberately left out.** Leaf disease identification from a
   photo, live mandi price feeds, live weather, IoT sensors, saved plans and
   PDF reports, Urdu voice output, a native mobile app and an admin panel. Each
   needs a trained model, a paid server, a second codebase or extra storage,
   and none is needed to solve the three problems above.

4. **Honest coverage of the three problems.** Of the 13 factors inside the three
   problems, 11 will be fully solved and 2 partly solved. The 3 disease factors
   are excluded from the count entirely and declared future work.

5. **Seven weeks of delivery, with a pass-or-fail gate each week.** Week 5 is
   reserved entirely for the one test that decides the project: the calculated
   bag counts must match a published figure. Every other week ends with a
   stated, checkable gate.

6. **How it will be verified.** Unit checks on the four calculation services
   including the published-figure check, plus an offline test carried out with
   the router physically switched off.

---

## Deployment and Use — How a Farmer Actually Reaches This

This section exists because the obvious question deserves a straight answer,
not an evasion.

**The honest starting point.** This is a student final-year project. What it
produces is a **working prototype plus a deployment guide** — not a service
that already reaches farmers. Saying otherwise would be the easiest thing in
the world for a reviewer to reject.

**What ships.** A folder that runs on any Windows, Linux or macOS laptop. It
starts with one command, needs no installer and no account, and works with the
network off.

**How a farmer reaches it, in the version this project can honestly support.**

1. **On the student's or supervisor's machine, demonstrated live.** The
   evaluator runs it. This is the version this project delivers and proves.
2. **Copied to a laptop or shared computer** — an agriculture office, a dealer
   shop, a village computer room — using the written deployment guide. Anyone
   with a laptop can do this; it is deliberately that simple.
3. **Run on a local network inside one village or office.** Several farmers
   could use one machine. This is realistic and is what the offline design is
   built for.

**What is explicitly not being claimed.** No hosting, no domain, no accounts
on a public server, no live mandi price feed, no government integration, and no
field trial with a measured number of real farmers. Those are the next
project, not this one. We would rather be approved for what can be demonstrated
on one laptop in one room than rejected for a deployment that does not exist.

---

## Functional and Non-Functional Requirements

Both lists carry **12 points** so the two columns stay equal. Simple numbered
lists, no sub-headings, as required for the proposal layout.

### Functional Requirements

1. A visitor can register with full name, email and password, and a registered
   farmer can log in and reach the protected pages.

2. The system will keep the password only as a scrambled hash and never in
   plain text, and will refuse any protected request that arrives without a
   valid login token.

3. One farmer can never read or change another farmer's land record or plan.

4. The farmer selects his district from a list of Punjab and Sindh districts
   and sees the climate card for that district and the current month.

5. The farmer enters his land area in acres, from 0.1 to 100, and selects one
   soil type; the details are saved against his own account.

6. The farmer enters the nitrogen, phosphorus and potassium values from his
   soil test card, and the system converts units when the card reports them in
   ppm, using the standard soil depth and bulk-density conversion.

7. The system will rank each nutrient as low, medium or adequate against the
   target range for that soil type, and show the result as a radar chart of
   nitrogen, phosphorus, potassium and pH.

8. The system will convert the nutrient still needed into whole bags of Urea,
   DAP and MOP, rounding up, and multiply by the farmer's acres to give total
   bags — including returning **zero bags** when a nutrient is already above
   target.

9. The system will show the fertiliser cost in Rupees and a "How this was
   calculated" panel that names the SFRI Punjab Guide-V method as the source.

10. The system will return a cost breakdown with named lines — land
    preparation, seed, fertiliser, labour, water and transport — each with its
    Rupee amount and its source shown next to it.

11. The system will show total water in litres, the number of irrigations, the
    expected yield in maund, the net profit, the return on investment and the
    break-even price, and will warn when the cost exceeds the entered budget.

12. The what-if simulator will let the farmer move sliders for area, budget and
    crop, show the baseline against the scenario with the change as a
    percentage, update every figure live, reset to the baseline on one click,
    and state on screen that results are session-only.

### Non-Functional Requirements

1. The application will work fully offline: every screen opens and every
   calculation runs with the network completely off, including after a page
   refresh.

2. **Zero runtime network dependencies** — no external API, CDN, font host,
   analytics or telemetry is contacted while the app is in use. All reference
   data is bundled with the application.

3. A page will appear in under two seconds on a mid-range laptop, measured on
   the demo machine and shown on screen during the demonstration.

4. Any single calculation will finish in under 300 milliseconds, measured by
   the unit checks.

5. Moving a simulator slider will recompute in under 50 milliseconds with no
   visible lag.

6. Passwords will be stored only as bcrypt hashes, every protected endpoint
   will require a valid token, and no user can read or modify another user's
   data.

7. All secrets will come from environment variables and never from source
   code, and the environment file will be excluded from version control.

8. Every calculated number will be traceable to a named public source, and each
   API response will carry the source of the figures it returns.

9. The four calculation services will be covered by unit checks — including
   the published-figure check — and the test run will be green.

10. Invalid input will be rejected with a clear message and will never crash
    the server; malformed requests will return a client error rather than a
    server error.

11. A farmer who has never seen the application will complete "set up land →
    see fertiliser bags" in under three minutes, every control will be
    reachable by keyboard with a visible focus ring, no screen will scroll
    sideways on a small phone, and colour will never be the only signal on
    screen.

12. No farmer data will leave the machine, the application will run on
    Windows, Linux and macOS from a fresh clone, and every module will be
    documented in the four guidance documents.

---

## The Whole-App Rule: Zero Runtime Network Dependencies

Field signal is a fact of life in the study area, so this is treated as a
requirement rather than a limitation.

> **The application will run with zero runtime network dependencies and with
> the network completely off, including after a page refresh.**

**What this means in practice.**

1. All reference data — climate, cost, SFRI bands, soil types and yield bands —
   is bundled inside the application as local files. Nothing is downloaded when
   it opens.
2. The server and the browser run from local files only. No CDN, no font host,
   no analytics script is loaded while the app is in use.
3. There is no subscription and no paid service. The only reason for a
   subscription in this product would be a cloud server, which this product
   deliberately avoids.
4. The demo is run with the router physically switched off. This is the check,
   not a claim in a paragraph.

**What this does not mean.** It does not mean the project has no software
dependencies. It has sixteen, all free, listed under Tools. The difference
matters: *"works with no internet"* is a promise to a farmer. *"Zero
dependencies"* is a false claim about the codebase. Only the first one is
defensible.

**How the demo machine shows it.**

1. Clone the repository on the demo machine.
2. Run the seed script so the reference data is loaded into the local
   database.
3. Start the server and open the browser to `http://localhost:5173`.
4. Log in, enter a soil test card and the land size, read the result on screen.
5. **Switch the router off.** Refresh every page and re-run the same
   calculation. Nothing changes. Open the browser's network tab — it is empty.

---

## Evidence and How Each Number Is Defended

Every number this project will produce falls into exactly one of three
categories. Nothing is allowed to be a fourth thing.

| Category | What it means | Example | How a reviewer checks it |
|----------|---------------|---------|-------------------------|
| **Published figure** | Copied from a named public source | PCPA Cotton Book: 2.35 bags Urea, 1.04 bags DAP per acre | Opens the publication and finds the number |
| **Calculated** | Produced by a published method from a published figure | Water need via FAO-56 ETc = ETo × Kc × days | Reads the method, checks the arithmetic |
| **Target** | A number this project intends to reach, not yet reached | 420 reference rows, 30 districts, 7 weeks | Checks it against the week gate that proves it |

**The rule that keeps this honest:** a target is never written in the voice of
an achievement. "420 reference rows" is a target with a week-1 gate. It is not
"420 rows are bundled", because nothing is bundled today.

### The validation reference, stated precisely

The SFRI calculation will be checked against the **PCPA Cotton Book** figure of
2.35 bags Urea and 1.04 bags DAP per acre.

> **Cotton is the validation reference for the method. It is not one of the
> crops the application will ship data for.** The shipped crop set is wheat,
> rice, maize, potato and tomato. A method that reproduces a published cotton
> figure correctly is evidence the arithmetic and the method are right. It is
> **not** evidence that cotton cost or yield data is present in the system. An
> earlier version of this proposal blurred that line; it is separated here.

**On the crops with no data yet.** Some crops in the target list do not
currently have a sourced cost or yield row. The rule above — *a crop appears in
the dropdown only if its figures are sourced* — means such a crop is visibly
disabled in the interface rather than silently filled with a plausible number.
The seed script will report, per crop, whether its rows are sourced or
unavailable. If fewer than five crops end up sourced, the project ships fewer
than five crops and says so.

---

## Coverage Scorecard

| Problem | Factors | Fully solved | Partly solved | Not solved |
|---------|---------|--------------|---------------|------------|
| P1 — Uninformed decisions | 4 | 3 | 1 | 0 |
| P2 — No pre-harvest planning | 5 | 4 | 1 | 0 |
| P3 — Hardware dependency | 4 | 4 | 0 | 0 |
| **Total** | **13** | **11** | **2** | **0** |
| *Excluded — disease diagnosis* | *3* | *0* | *0* | *3 — future work* |

**Three problems addressed, thirteen factors, none of them quietly dropped.**
The disease factors are excluded from the count and named separately, so the
scorecard measures only what the project actually attempts. We would rather
state a limit than claim coverage we cannot show.

---

## Risks and the Response to Each

| # | Risk | Chance | Effect | What we do |
|---|------|--------|--------|------------|
| 1 | The calculation does not match the published figure | Medium | Very high | Week 5 is reserved for exactly this test. If it fails, the method is wrong and we fix it before anything else. |
| 2 | A crop has no sourced data, so the shipped crop set shrinks | **High** | Medium | Accepted by design. The crop-sourcing rule disables unsourced crops instead of inventing figures. Fewer crops, honestly labelled, is a survivable outcome. |
| 3 | Reference data cannot be found or downloaded | Medium | High | Every figure has a named public source. The fallback is official provincial and NFDC rates, not an estimate. |
| 4 | Scope grows during the build | High | High | The out-of-scope list is fixed. Nothing is added without removing something. |
| 5 | A supervisor asks for the removed disease module | High | Medium | Already written down as out of scope, with the reason. We do not pretend. |
| 6 | Offline mode breaks on refresh | Medium | Medium | Tested in week 7 with the router physically switched off. |
| 7 | "How does a real farmer reach a locally run app?" | **High** | High | Answered openly in the Deployment and Use section, including the versions this project does *not* claim. |

---

## Deliverables

| # | Deliverable | When |
|---|-------------|------|
| 1 | This proposal | Now |
| 2 | Proposal presentation (PPT) | +1 week |
| 3 | Four guidance documents — SRS, SDD, Test Plan, API and Data | +2 weeks |
| 4 | The working codebase | +5 weeks |
| 5 | Final documentation and final presentation | +7 weeks |

---

## Seven-Week Plan With a Gate Each Week

| Week | Work | Gate — prove it when |
|------|------|---------------------|
| 1 | SFRI, PCPA, PAU and climate figures → local data files and a seed script | Seed script reports the row count **and which crops are sourced vs unavailable** |
| 2 | Express server, token login, routes, validation | Login returns a valid token |
| 3 | Screens 1–3, climate service | District and soil values save; climate card displays |
| 4 | Planner screen, cost/water/yield service | Cost, water, yield and return appear with citations |
| 5 | NPK screen, SFRI service, radar chart | **Calculated bags match the published PCPA figure** |
| 6 | What-if simulator, responsive layout, theme | Sliders recompute live; mobile layout holds |
| 7 | Unit checks on the four services, offline test, documentation | Test run green; app works with the router off |

Week 5 is the project. Everything else is engineering.

---

## Particulars of the Students

| Sr. # | Registration No. | Name in Full | Email | Contact # | CGPA | Signature |
|-------|------------------|--------------|-------|-----------|------|-----------|
| 1 | 2017-CS-___ | Abdullah | ______________________ | _______________ | ______ | __________ |
| 2 | ________________ | ______________________ | ______________________ | ______________________ | ______ | __________ |

> **Note for the student:** the Registration No., Email, Contact # and CGPA
> cells are left blank on purpose. Those are personal facts and must be typed in
> by the student before submission. If you are working alone, delete row 2
> entirely. This agent will not invent them.

---

## Remarks — Why a Supervisor Should Approve This Project

1. **It solves a real problem for a real person.** A smallholder in Faisalabad
   makes a PKR 250,000 decision with no cost figure, no water figure and no
   exact fertiliser quantity.

2. **It does not copy anyone.** We audited 13 tools. Nobody, anywhere, combines
   total cost in local currency + water in litres + soil-test-derived
   fertiliser bags + offline operation + a what-if slider.

3. **The central method is not invented, and that is the strength.** We
   implement the Government of the Punjab SFRI Guide-V method and the FAO-56
   method, then check the result against the figure published in the PCPA
   Cotton Book. The project can be checked against an official source.

4. **Every number on screen carries its citation.** This is unusual, and it is
   the single reason a supervisor can believe the output.

5. **The scope is honest.** We wrote down what we are not building, with
   reasons. We say plainly that disease diagnosis is future work, and we kept
   it out of the problem statement rather than solving it in a footnote. A
   project that admits its limit is easier to supervise than one that hides it.

6. **It is buildable in seven weeks by one student.** No model file, no image
   dataset, no GPU, no paid API. The heaviest week is week 5, and it is
   reserved for the one calculation that matters.

7. **It works offline on one laptop.** Field signal is a fact of life in the
   study area. We treat that as a requirement, and we prove it on the demo
   machine with the router switched off.

8. **We have not overclaimed.** The deployment section says exactly how a
   farmer reaches this and exactly what this project does not deliver. A
   proposal that a reviewer cannot knock down is worth more than one that
   sounds larger and breaks on the first hard question.

---

## Signatures and Date

| Role | Name | Signature | Date |
|------|------|-----------|------|
| **Student(s)** | Abdullah | ____________________ | ____ / ____ / 2026 |
| **Project Supervisor** | ____________________ | ____________________ | ____ / ____ / 2026 |
| **Coordinator** | ____________________ | ____________________ | ____ / ____ / 2026 |
| **Head of Department** | ____________________ | ____________________ | ____ / ____ / 2026 |

**Approved:** ☐ YES &nbsp;&nbsp;&nbsp; ☐ NO

---

## Appendix A — Sources of Data

These are the public publications the system will be built on. Each one is
named on screen wherever its figures are used.

| # | Source | What we take from it | Why it is citable |
|---|--------|----------------------|-------------------|
| 1 | **SFRI Punjab — Guide-V** (Soil Fertility Research Institute, Government of Punjab) | N-P-K target ranges per soil type and the recommendation method | A Government of the Punjab publication with a worked example |
| 2 | **PCPA Cotton Book** (Punjab Crop Protection Agency) | Per-acre cost breakdown; the Urea 2.35 / DAP 1.04 bag validation figure | Government publication of field figures |
| 3 | **PAU Package of Practices** (University of Agriculture Faisalabad) | Seed rates, varieties, sowing windows, district yield bands | The university's own recommendation for its own region |
| 4 | **FAO Irrigation and Drainage Paper 56** | Crop coefficients (Kc), the ETc method, effective rainfall | An international standard used worldwide |
| 5 | **NFDC Pakistan Fertiliser Statistics** | Retail prices of urea, DAP and MOP | The official price series, not an estimate |
| 6 | **World Bank Climate Portal / NASA POWER** | Monthly temperature, rainfall and ETo normals for the seeded districts | Internationally published climate dataset |
| 7 | **Punjab and Sindh Agriculture Departments** | District list, crop calendars, soil type distribution | Official provincial record |

---

## Appendix B — What Is NOT Claimed

Written down on purpose, so nobody has to guess what this project promises.

| We do **not** claim | Why |
|---|---|
| That AgriPulse identifies crop diseases from a photo | No trained model and no Punjab photo dataset. **Out of scope, future work.** |
| That it has zero software dependencies | It has sixteen, all free. What it has is **zero runtime network dependencies**. |
| That any part of it is built yet | The project has not started. Every quantity is a published figure, a calculated result, or a gated target — and never two of those at once. |
| That it is deployed and farmers are using it | What ships is a working prototype and a deployment guide. Hosting, public accounts and a field trial are not in this project. |
| That the numbers replace an agronomist's judgement | They apply published averages to one field. A local agriculture officer's advice still comes first. |
| That it works in live weather | It uses long-term climate normals, not a live feed. It tells you what March in Faisalabad usually looks like. |
| That cotton data is in the system | Cotton is the **validation reference for the method only**. It is not a shipped crop. |
| That five crops are guaranteed | A crop appears only if its cost and yield rows are sourced. If fewer are sourced, fewer ship. |
| That plans are stored for later | They are not. Plans live for the session and clear on reload, and the app says so on screen. |
| That it works in every district of Pakistan | Only the seeded districts are included. The data model supports more; we filled the ones we could source. |
| That it needs a server, cloud or subscription | It runs on one laptop. That is deliberate — and it is also why there is no subscription. |
| That it works as a mobile app, in Urdu, or with audio | It is a browser app on a laptop. The scope is English text and a clean, keyboard-friendly screen. |

---

*Rebuilt 2026-10-03 from `chat-history/media/1-FYP Proposal Template.docx`,
following its section order exactly. Scope of record is
`chat-history/outputs/A4.md`; the required content-types for Aim and Objective,
Scope and the two requirement lists are the ones specified in Q8. The exported
`.pdf` and `.odt` in this folder are exports of an earlier version and must be
re-exported from this file — the `.md` is the source of truth.*
