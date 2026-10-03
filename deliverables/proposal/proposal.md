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
revision: 3 — student-voice rewrite. Pitch framing and forward-looking
  promises removed. Every retained number is either quoted from a named
  publication or computed by a published method.
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

> **AgriPulse — A Soil-Test Driven Farm Planner That Tells a Punjab Farmer His
> Cost, His Water Need, His Fertiliser Bags and His Profit, Before He Sows.**

**Working name:** AgriPulse
**Name meaning:** *Agri* (agriculture) + *Pulse* (the beating of a crop's life,
and the name of Pakistan's staple grain family).

---

## Tools to Be Used

Every tool below is free and open-source. The list is the stack the project is
actually built on, matched to the locked scope in `A4.md`.

| # | Tool | Why we chose it |
|---|------|-----------------|
| 1 | **React 18** | Builds the five screens as components. |
| 2 | **Vite** | Starts a local dev server in under a second. |
| 3 | **React Router** | Moves between the five pages. |
| 4 | **Tailwind CSS** | Clean screens without long CSS files. |
| 5 | **Recharts** | Draws the soil radar chart and the cost bar chart. |
| 6 | **Fetch API client** | The browser's own request method — no extra library. |
| 7 | **Node.js** | The runtime for the server. |
| 8 | **Express** | One plain server that reads the bundled data. |
| 9 | **Mongoose** | Talks to the local MongoDB. |
| 10 | **MongoDB (local)** | Holds accounts, land records and plans on the same machine. |
| 11 | **jsonwebtoken (JWT)** | Keeps one farmer's data separate from another's. |
| 12 | **bcrypt** | Stores passwords as hashes, never as plain text. |
| 13 | **Zod** | Checks every input before the server uses it. |
| 14 | **dotenv** | Keeps settings out of the source code. |
| 15 | **cors** | Development cross-origin access. |
| 16 | **morgan** | Request logging. |
| 17 | **nodemon** | Restarts the server on a file change. |
| 18 | **Git + GitHub** | Saves the work and allows review. |
| 19 | **Microsoft Word** | Writes and exports this proposal. |

**Total: 19 tools** — ten backend-side packages, seven frontend-side, and two
everyday tools (Git, Word). All free.

Two properties of this stack matter for the project and are stated once here
rather than repeated as caveats:

- **It is entirely local.** The database is a local `mongod`, the reference
  data ships as local JSON files, and the browser loads its assets from the
  local server.
- **It needs no account, no subscription and no hosted service.** There is
  nothing to sign up for and nothing to pay for at run time.

---

## Problem Statement

We studied **13 existing tools** — five working in Pakistan and eight
international. They gave us a clear picture of what a farmer is missing. Three
problems stood out, and all three are ones this project can genuinely address.

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

### The gap, in one line

> Every existing tool asks the farmer for what he already knows. AgriPulse
> starts from the one thing he actually has — a soil test card and his land
> size — and works out the rest.

### What the existing tools do and do not do

| Tool | What it does | What it cannot do |
|------|--------------|-------------------|
| Bakhabar Kissan | Weather and advisory at national scale | No cost, water or return figure; needs a network |
| MandiOye | 18 free calculators — the closest to us | Asks you to **already know** the nutrient requirement; no soil-test logic; online only |
| Agrixia | GPS land records, mandi prices, Urdu | Marketplace-first; no calculator, no soil test |
| PlantVillage / Nuru | Free, offline, disease ID from a photo | Covers 38 classes of US horticulture crops. Punjab field crops are not in that list |
| Kisan Sarathi (India) | Advisory delivered at national scale | A state-funded national programme, not something a single project copies |

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

3. **Run the whole thing on one laptop.** Hardware, a network connection and a
   monthly fee are the real barriers in the field, so the application is built
   to run on a single machine with nothing else attached.

4. **Show the source of every number on the screen.** A figure nobody can
   trace is worth nothing to the farmer and nothing to the evaluator, so each
   citation sits next to the value it belongs to.

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
   logged-in farmer, and every screen will work with the router off.

---

## Scope of the Project

This project will deliver a **five-page web application** built from **four
modules** — login and registration, land and climate profiling, resource and
financial planning, and NPK fertiliser advising — plus a what-if simulator that
compares two plans side by side before money is committed. The farmer will
register once, record his district, land area and soil type, enter the
nitrogen, phosphorus and potassium values from his soil test card, and receive
the Urea, DAP and MOP bag counts, a full cost breakdown in Rupees, the water
requirement in litres, the expected yield, the net profit, the return on
investment and the break-even price, with the name of the public source
printed beside every figure. The application will run on a single laptop, hold
no machine-learning model of any kind, and load every asset from the local
server rather than the internet.

1. **What is being built.** Five pages across four modules — login and
   register, land and climate profiler, resource and financial planner, NPK
   soil fertiliser adviser — plus a what-if simulator that compares two plans
   side by side on the same screen.

2. **The rule that governs the data.** A crop appears in the dropdown **only
   if its cost and yield figures have a named, downloadable public source.**
   Where a crop has no sourced figures it is shown as unavailable rather than
   filled in with a guess. This is why the crop count is written as a target
   and not a promise.

3. **What this project does not attempt.** Leaf disease identification from a
   photo, live mandi price feeds, live weather and IoT sensors are outside what
   a single-laptop project can do honestly. Each needs a trained model, a paid
   server or a second codebase, and none is needed to solve the three problems
   above. Saved plans, PDF reports, Urdu voice output, a native mobile app and
   an admin panel are left out for the same reason — they are not required by
   the three problems.

4. **Coverage of the three problems.** Of the 13 factors inside the three
   problems, 11 will be fully addressed and 2 partly addressed. The scorecard
   below shows the split.

5. **Seven weeks of delivery, with a checkable result each week.** Week 5 is
   reserved entirely for the one test that decides the project: the calculated
   bag counts must match a published figure. Every other week ends with a
   stated result that can be seen.

6. **How it will be verified.** Unit checks on the four calculation services
   including the published-figure check, plus a run with the router physically
   switched off.

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

1. The application will work with the network completely off: every screen
   opens and every calculation runs, including after a page refresh.

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

## Remarks

1. **It solves a real problem for a real person.** A smallholder in Faisalabad
   makes a PKR 250,000 decision with no cost figure, no water figure and no
   exact fertiliser quantity.

2. **It does not copy anyone.** We audited 13 tools. Nobody combines total cost
   in local currency + water in litres + soil-test-derived fertiliser bags +
   offline operation + a what-if slider.

3. **The central method is not invented, and that is the strength.** We
   implement the Government of the Punjab SFRI Guide-V method and the FAO-56
   method, then check the result against the figure published in the PCPA
   Cotton Book. The project can be checked against an official source.

4. **Every number on screen carries its citation.** This is unusual, and it is
   the single reason a supervisor can believe the output.

5. **The scope is honest.** We wrote down what we are not building, with
   reasons. A project that states its own limits is easier to supervise than
   one that hides them.

6. **It is buildable in seven weeks by one student.** No model file, no image
   dataset, no GPU, no paid API. The heaviest week is week 5, and it is
   reserved for the one calculation that matters.

7. **The computer-science content is real.** The agronomic formulas are
   published and fixed; the work is turning them into a correct, validated,
   fully local service — four calculation services, a token-authenticated API,
   input validation at every boundary, and a test suite that proves the
   arithmetic against an official figure.

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

## Where Every Number Comes From

Every figure the system produces falls into exactly one of two categories.

| Category | What it means | Example | How it is checked |
|----------|---------------|---------|-------------------|
| **Published figure** | Copied from a named public source | PCPA Cotton Book: 2.35 bags Urea, 1.04 bags DAP per acre | Open the publication and find the number |
| **Calculated** | Produced by a published method from a published figure | Water need via FAO-56 ETc = ETo × Kc × days | Read the method, check the arithmetic |

### The validation reference, stated precisely

The SFRI calculation will be checked against the **PCPA Cotton Book** figure of
2.35 bags Urea and 1.04 bags DAP per acre.

> **Cotton is the validation reference for the method. It is not one of the
> crops the application ships data for.** The shipped crop set is wheat, rice,
> maize, potato and tomato. A method that reproduces a published cotton figure
> correctly is evidence the arithmetic and the method are right. It is not
> evidence that cotton cost or yield data is present in the system.

**On crops with no data yet.** Some crops in the list do not currently have a
sourced cost or yield row. The rule above — *a crop appears in the dropdown only
if its figures are sourced* — means such a crop is visibly unavailable in the
interface rather than silently filled with a plausible number. The seed script
reports, per crop, whether its rows are sourced or unavailable. If fewer than
five crops end up sourced, the project ships fewer than five crops and says so.

---

## Coverage Scorecard

| Problem | Factors | Fully addressed | Partly addressed |
|---------|---------|-----------------|------------------|
| P1 — Uninformed decisions | 4 | 3 | 1 |
| P2 — No pre-harvest planning | 5 | 4 | 1 |
| P3 — Hardware dependency | 4 | 4 | 0 |
| **Total** | **13** | **11** | **2** |

**Three problems, thirteen factors, none of them quietly dropped.**

---

## Risks and the Response to Each

| # | Risk | Chance | Effect | What we do |
|---|------|--------|--------|------------|
| 1 | The calculation does not match the published figure | Medium | Very high | Week 5 is reserved for exactly this test. If it fails, the method is wrong and we fix it before anything else. |
| 2 | A crop has no sourced data, so the shipped crop set shrinks | **High** | Medium | Accepted by design. The crop-sourcing rule shows unsourced crops as unavailable instead of inventing figures. |
| 3 | Reference data cannot be found or downloaded | Medium | High | Every figure has a named public source. The fallback is official provincial and NFDC rates, not an estimate. |
| 4 | Scope grows during the build | High | High | The out-of-scope list is fixed. Nothing is added without removing something. |
| 5 | Offline mode breaks on refresh | Medium | Medium | Tested in week 7 with the router physically switched off. |

---

## Build Schedule

| Week | Work | Result that can be seen |
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

## Appendix A — Sources of Data

These are the public publications the system is built on. Each one is named on
screen wherever its figures are used.

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

*Rebuilt 2026-10-03 from `chat-history/media/1-FYP Proposal Template.docx`,
following its section order exactly. Scope of record is
`chat-history/outputs/A4.md`; the required content-types for Aim and Objective,
Scope and the two requirement lists are the ones specified in Q8. The exported
`.pdf` and `.odt` in this folder are exports of an earlier version and must be
re-exported from this file — the `.md` is the source of truth.*
