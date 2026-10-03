---
title: Project Proposal — AgriPulse
institution: Government Graduate College Satiana Road, Faisalabad
university: Government College University Faisalabad
department: Department of Computer Science
date: 2026-10-01
model: Solar Mini 4
agent: Solar Mini 4 (freebuff)
template_source: chat-history/media/1-FYP Proposal Template.docx
specialist_roles_adopted:
  - proposal-strategist — defensible claims, no empty adjectives
  - technical-writer — plain English, one idea per section
  - senior-project-manager — realistic scope, testable acceptance
  - product-manager — one farmer, one clear decision, no invented features
---

<div align="center">

**Government College University Faisalabad**  
**Government Graduate College, Satiana Road, Faisalabad**  
**Department of Computer Science**

# Project Proposal

</div>

---

## DATE

**Day:** 1 &nbsp;&nbsp; **Month:** October &nbsp;&nbsp; **Year:** 2026

**Project Code:** `MCSD-2026-FYP-___` *(assigned by the office)*

---

## Project Title

> **AgriPulse — A Soil-Test Driven Farm Planner that Gives a Punjab Farmer His Cost, Water Need, Fertiliser Bags and Profit Before He Sows.**

**Working name:** AgriPulse  
**Name meaning:** *Agri* (agriculture) + *Pulse* (the beating of a crop's life, and the name of Pakistan's staple grain family).

---

## Tools to Be Used

This is a small list, not a shopping list. Every tool is free.

| # | Tool | Why we chose it |
|---|------|-----------------|
| 1 | **HTML, CSS, JavaScript** | The app works in a browser with no install. |
| 2 | **React 18** | Builds the five screens quickly and cleanly. |
| 3 | **Vite** | Starts a local server fast. |
| 4 | **Tailwind CSS** | Makes the screens look clean without writing long CSS. |
| 5 | **Recharts** | Draws the soil-health radar chart and the cost chart. |
| 6 | **Node.js + Express** | One plain-language server that reads the bundled data. |
| 7 | **mongoose** | Stores one user account, one land record and one plan. |
| 8 | **jsonwebtoken (JWT)** | Keeps one farmer's account separate from another's. |
| 9 | **bcrypt** | Stores the password as a hash, never as plain text. |
| 10 | **Zod** | Checks every answer before the server uses it. |
| 11 | **dotenv** | Keeps settings out of the code. |
| 12 | **morgan** | Logs requests while we build. |
| 13 | **node:test** | Runs the calculation checks. |
| 14 | **Git + GitHub** | Saves the work and lets us review it. |
| 15 | **mermaid** | Draws the diagrams. |
| 16 | **Microsoft Word** | Writes this proposal. |

**Total: 16 tools.** All free. None needs a paid licence.

---

## Problem Statement

### The short version

A Punjab farmer must decide **what to sow, how much to spend, how much fertiliser to buy and whether the crop pays** — before the season starts. Today he is asked for the answers he does not have, or the tools ask for a signal his village does not get.

### The long version

Farming decisions are made under three conditions at once: the farmer has little money, the decision is made once and cannot be undone until harvest, and the information needed is either locked inside government offices or hidden behind paid services.

We studied **13 existing tools** — five working in Pakistan and eight international ones. We found **four** separate problems.

---

### Problem 1 — Decisions are made without real information

| What goes wrong | Why it happens |
|-----------------|----------------|
| The crop is chosen without knowing what the soil holds | Soil test data exists, but nobody turns it into a decision |
| Fertiliser is applied by habit, not by need | The exact quantity is never calculated for the farmer's own field |
| The farmer cannot see what his soil is short of | The result stays as a number on a printed slip |
| Money and water are wasted on the wrong dose | Nobody links the soil result to the cost sheet |

The Government of the Punjab runs the soil labs and prints a card with the numbers on it. **The card stops there.** We take the numbers on that card and turn them into a decision.

---

### Problem 2 — There is no planning before the harvest

| What goes wrong | Why it happens |
|-----------------|----------------|
| The total expense is unknown on the day of sowing | Costs are only known after the season ends |
| The water requirement is unknown | Nobody tells him how many irrigations and how many litres |
| The expected yield and profit are unknown | No one can tell him if the crop will pay for itself |
| Two crops cannot be compared side by side | Each calculation is done on paper, one at a time |

Farmers do plan. They plan in their heads, from memory and last year's prices. When urea goes up, nobody notices until the bill arrives.

---

### Problem 3 — Disease diagnosis was planned but is not delivered

We **planned** a disease module at the start. We then checked what we actually had to work with.

| What goes wrong | Why it was dropped |
|-----------------|--------------------|
| Disease books are written in English and the farmer reads Urdu | We have no photo dataset, no GPU and no server to train a model |
| The farmer cannot tell two diseases apart | There is no on-device vision model in this scope |
| The cure is not given in a local language | No remedy can be issued without a diagnosed disease |

**This project does NOT solve Problem 3.** We say so plainly. It is future work. Claiming to identify a disease from a photo would invite a rejection: we have no data, no model and no paid server.

---

### Problem 4 — Existing tools depend on hardware and paid services

| What it costs today | Detail |
|---------------------|--------|
| **Physical weather stations** | Bakhabar Kissan runs 300+ ground stations. That cost cannot be removed from their model. |
| **A working internet connection** | Field signal is patchy. Every online-only tool fails in the field. |
| **A monthly data subscription** | B2B agri-data products sell data, not decisions. |
| **A trained model on a server** | Free offline models exist, but they cover 38 US and temperate classes, not Punjab's field crops. |

The farmer either pays, or goes blind. **AgriPulse removes the cost and the need for a signal.**

---

### Why the existing tools do not solve this

| Tool | What it does well | What it cannot do |
|------|-------------------|-------------------|
| Bakhabar Kissan | Weather and advisory, 15.8M users | No cost, water or ROI figure. Needs a network. Runs 300 physical stations. |
| MandiOye | 18 free calculators — closest to us | Asks you to **already know** the nutrient requirement. No soil-test logic. Online only. |
| Agrixia | GPS land, mandi prices, Urdu | Still pre-launch. Marketplace first. No calculator, no soil test. |
| PlantVillage / Nuru | Free, offline, disease ID from a photo | **38 classes of US horticulture crops.** Punjab field crops are not in that list. |
| Kisan Sarathi (India) | Advisory at national scale, 2.95 crore farmers | State-funded at national scale. Not an entry point for an FYP. |

**The gap, in one line:**

> Every existing tool asks the farmer for what he already knows. AgriPulse starts from the one thing he actually has — a soil test card and his land size — and works out the rest.

The closest tool to us, MandiOye, needs the nutrient requirement as an **input**. The SFRI method needs only the **soil reading**. That is the real difference.

---

## Aim and Objective

### The aim of the project is as follows

1. **Turn one soil test card into a complete sowing decision.** A farmer enters the numbers printed on his government soil test card and gets back the four things he must decide before sowing — total cost, water need, fertiliser bags and expected profit — instead of guessing from memory.  
2. **Use published government and FAO methods, not invented formulas.** Every figure the system produces matches a named public publication, so the supervisor and the farmer can both check it.  
3. **Remove the three things that stop a small farmer from using such a tool.** Hardware, an internet signal and a monthly fee are the real barriers today, so the application runs on one laptop with the router switched off.  
4. **Show the source of every number on the screen.** A figure nobody can trace is worth nothing to the farmer and nothing to the evaluator, so each citation sits next to the value it belongs to.  
5. **Teach one idea, not just hand out numbers.** The farmer should leave understanding that cultivating more land with the same budget raises total profit but lowers the return on every rupee he spends.  

### The objectives of the project are as follows

1. **Read the soil test card and show what the soil is short of.** A radar chart plots the farmer's nitrogen, phosphorus, potassium and pH against the target range for his soil type, so the deficiency is visible instead of printed.  
2. **Calculate the exact number of Urea, DAP and MOP bags the field needs.** The calculation uses the Government of Punjab SFRI Guide-V formula and is validated against the published PCPA Cotton Book figure of 2.35 bags Urea and 1.04 bags DAP per acre, which is the check that proves the formula is correct.  
3. **Calculate the full cost of sowing, line by line, in Pakistani Rupees.** Land preparation, seed, fertiliser, labour, water and transport are shown separately, with the PCPA Cotton Book or PAU Package of Practices figure named beside each line.  
4. **Calculate the water requirement and the money the crop will return.** Total water in litres and the number of irrigations come from the FAO-56 method; expected yield, net profit, return on investment and break-even price come from PAU district yield bands and NFDC prices.  
5. **Let the farmer compare options before he spends money.** Sliders for area, budget and crop recompute cost, profit and return immediately inside the browser, with no network call and nothing written to the database.  
6. **Keep the farmer's data private and the app usable with no signal.** Login is protected by a JWT token and every query is filtered to the logged-in farmer, while every screen and every calculation still works with the router off.  

### What the farmer learns, in one sentence

The system should teach one idea that no calculator can: **more land with the same budget raises total profit but lowers the return on each rupee.** That single observation is the intellectual content of the project.

---

## Scope of the Project

### The scope, in one paragraph

This project delivers a **five-page offline web application** built from **four modules** — login and registration, land and climate profiling, resource and financial planning, and NPK fertiliser advising — plus a what-if simulator that compares two plans side by side before money is committed. The farmer registers once, records his district, land area and soil type, enters the nitrogen, phosphorus and potassium values from his soil test card, and receives the exact Urea, DAP and MOP bag counts, a full cost breakdown in Rupees, the water requirement in litres, the expected yield, the net profit, the return on investment and the break-even price, with the name of the public source printed beside every figure. The whole application runs on a single laptop with the internet switched off, is backed by **420 rows of bundled reference data** covering 5 crops, 5 soil types and 30 districts, and contains **no machine-learning model of any kind**. It also holds **0 external dependencies**: everything needed is bundled inside the app, so the farmer's machine needs no installation and no internet.

### What is being built

1. **Five pages and four modules** — login and register, land and climate profiler, resource and financial planner, NPK soil fertiliser adviser — plus a what-if simulator that compares two plans side by side on the same screen.
2. **The data behind it** — 420 reference rows loaded by one seed script: 30 districts, 360 monthly climate records, 5 soil types, 20 SFRI target bands, 5 crops, 15 yield bands and 30 cost rows, each taken from a named public source.
3. **What is deliberately left out** — leaf disease identification from a photo, live mandi price feeds, live weather, IoT sensors, saved plans and PDF reports, Urdu voice output, a native mobile app and an admin panel. Each of these needs a trained model, a paid server, a second codebase or extra storage, and none of them is needed to solve the four problem statements.
4. **The honest scorecard** — of the 16 factors inside the four problem statements, 11 are fully solved, 2 are partly solved, and 3 belong to the removed disease module and are declared as future work rather than claimed as delivered.
5. **Seven weeks of delivery**, with a pass-or-fail gate each week. Week 5 is reserved entirely for the one test that decides the project: the calculated bag counts must match the published PCPA Cotton Book figure. Every other week ends with a stated, checkable gate.
6. **How it is verified** — 16 free tools, unit checks on the four calculation services including the PCPA Cotton Book check, and an offline test carried out with the router physically switched off.

---

## Functional and Non-Functional Requirements

Both lists carry **12 points** so the two columns stay equal. They are simple numbered lists with no sub-headings, as requested for the proposal layout.

### Functional Requirements

1. A visitor can register with full name, email and password, and a registered farmer can log in and reach the protected pages.
2. The system keeps the password only as a scrambled hash and never in plain text, and refuses any protected request that arrives without a valid login token.
3. One farmer can never read or change another farmer's land record or plan.
4. The farmer selects his district from a list of 30 Punjab and Sindh districts and sees the climate card for that district and the current month.
5. The farmer enters his land area in acres, from 0.1 to 100, and selects one of five soil types; the details are saved against his own account.
6. The farmer enters the nitrogen, phosphorus and potassium values from his soil test card, and the system converts the units when the card reports them in ppm.
7. The system ranks each nutrient as low, medium or adequate against the target range for that soil type, and shows the result as a radar chart of nitrogen, phosphorus, potassium and pH.
8. The system converts the nutrient still needed into whole bags of Urea, DAP and MOP, rounding up, and multiplies by the farmer's acres to give total bags.
9. The system shows the fertiliser cost in Rupees and a "How this was calculated" panel that names the SFRI Punjab Guide-V formula as the source.
10. The system returns a cost breakdown with named lines — land preparation, seed, fertiliser, labour, water and transport — each with its Rupee amount and its source shown next to it.
11. The system shows total water in litres, the number of irrigations, the expected yield in maund, the net profit, the return on investment and the break-even price, and warns in red when the cost exceeds the entered budget.
12. The what-if simulator lets the farmer move sliders for area, budget and crop and shows baseline against scenario with the change as a percentage, updates every figure live, resets to the baseline on one click, and states on screen that results are session-only.

### Non-Functional Requirements

1. The application works fully offline: every screen opens and every calculation runs with the network completely off, including after a page refresh.
2. No external API, CDN, font host or analytics service is called at runtime.
3. A page appears in under two seconds on a mid-range laptop.
4. Any single calculation finishes in under 300 milliseconds.
5. Moving a simulator slider recomputes in under 50 milliseconds with no visible lag.
6. Passwords are stored only as bcrypt hashes, every protected endpoint requires a valid JWT, and no user can read or modify another user's data.
7. All secrets come from environment variables and never from source code, and the environment file is excluded from version control.
8. Every calculated number is traceable to a named public source, and each API response carries the source of the figures it returns.
9. The four calculation services are covered by unit checks — at least 25 test cases including the PCPA Cotton Book check — and the test run is green.
10. Invalid input is rejected with a clear message and never crashes the server; malformed requests return a client error rather than a server error.
11. A farmer who has never seen the application completes "set up land → see fertiliser bags" in under three minutes, every control is reachable by keyboard with a visible focus ring, no screen scrolls sideways on a small phone, and colour is never the only signal on screen.
12. No farmer data leaves the machine and no telemetry of any kind exists, the application runs on Windows, Linux and macOS with one command from a fresh clone, and every module is documented in the four guidance documents.

---

## Coverage of the Four Problems — the Honest Scorecard

We audited all **16 factors** inside the four problem statements. This is the result.

| Problem | Factors in it | Fully solved | Partly solved | Not solved |
|---------|---------------|--------------|---------------|------------|
| P1 — Uninformed decisions | 4 | 3 | 1 | 0 |
| P2 — No financial planning | 5 | 4 | 1 | 0 |
| P3 — Disease diagnosis | 3 | **0** | **0** | **3 → future work** |
| P4 — Hardware dependency | 4 | 4 | 0 | 0 |
| **Total** | **16** | **11** | **2** | **3** |

**Two problems solved, one three-quarters solved, one declared as future work.** All three unsolved factors belong to the module we removed, so nothing else is affected. We would rather state this than claim coverage we cannot show.

---

## Whole-App Rule: Zero Dependencies and Offline

Every farmer uses the app on a simple Windows or Linux machine in a village with no signal. To keep that promise true and consistent, the application follows one whole-app rule:

> **The app must run with zero external resource dependencies and with the network completely off, including after a page refresh.**

### What this means in practice

1. All reference data — climate, cost, SFRI bands, soil types and yield bands — is bundled inside the app as JSON files. Nothing is downloaded when the app opens.
2. The server and the browser run from local files only. No CDN, no font host and no analytics script is loaded at runtime.
3. The web app is installable on the farmer's desktop so it can be opened exactly the same way every time.
4. There is no subscription and no paid service. The only reason for a subscription in this product would be a cloud server, which this product deliberately avoids.
5. On the lab machine, the router is switched off to test the promise. On the farmer's machine, the same rule holds: the app stays self-contained.

### How a student demonstrates the app on the demo machine

1. Clone the repository on the demo machine.
2. Run the seed script so the 420 reference rows are imported into MongoDB on the local machine.
3. Start the Node.js server and open the browser to `http://localhost:5173`.
4. Log in with the demo account, enter a soil test card and the land size, and read the result on screen.
5. Switch the router off, refresh every page and re-run the same calculation. Nothing changes. The app still works.

This is the demonstration step. It shows the claim "works offline and with zero resource dependencies" rather than merely stating it.

---

## Risks and the Response to Each

| # | Risk | Chance | Effect | What we do |
|---|------|--------|--------|------------|
| 1 | Scope grows during the build | High | High | The out-of-scope list above is signed off. Nothing is added without removing something. |
| 2 | The formula does not match published figures | Medium | Very high | Week 5 is reserved for exactly this test. If it fails, the formula is wrong and we fix it before anything else. |
| 3 | Reference data cannot be found | Medium | High | Every figure has a named public source that is downloadable. The fallback is NFDC plus provincial department rates. |
| 4 | A supervisor asks for the removed disease module | High | Medium | It is already written down as future work, with the reason. We do not pretend. |
| 5 | Offline mode breaks on refresh | Medium | Medium | The offline promise is tested in week 7 with the router physically switched off. |

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

## Particulars of the Students

| Sr. # | Registration No. | Name in Full | Email | Contact # | CGPA | Signature |
|-------|------------------|--------------|-------|-----------|------|-----------|
| 1 | 2017-CS-___ | Abdullah | ______________________ | _______________ | ______ | __________ |
| 2 | ________________ | ______________________ | ______________________ | ______________________ | ______ | __________ |

> **Note for the student:** the Registration No., Email, Contact # and CGPA cells are left blank on purpose. Those are personal facts and must be typed in by the student before submission. This agent will not invent them.

---

## Remarks — Why a Supervisor Should Approve This Project

1. **It solves a real problem for a real person.** A smallholder in Faisalabad makes a PKR 250,000 decision with no cost figure, no water figure and no exact fertiliser quantity.
2. **It does not copy anyone.** We audited 13 tools. Nobody, anywhere, combines total cost in local currency + water in litres + soil-test-derived fertiliser bags + offline operation + a what-if slider.
3. **The central algorithm is not invented, and that is the strength.** We implement the Government of the Punjab SFRI Guide-V formula and the FAO-56 method, then prove the result lands on the figure published in the PCPA Cotton Book. The project can be checked against an official source.
4. **Every number on screen carries its citation.** This is unusual, and it is the single reason a supervisor can believe the output.
5. **The scope is honest.** We wrote down what we are not building, with reasons. We say plainly that Problem 3 is future work. A project that admits its limit is easier to supervise than one that hides it.
6. **It is buildable in seven weeks by one student.** No model file, no image dataset, no GPU, no paid API. The heaviest week is week 5, and it is reserved for the one calculation that matters.
7. **It works offline on the farmer's machine.** Field signal is a fact of life in the study area. We treat that as a requirement, not a limitation, and we prove it with a live demo.

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

These are the public publications the system is built on. Each one is named on screen wherever its figures are used.

| # | Source | What we take from it | Why it is trustworthy |
|---|--------|----------------------|-----------------------|
| 1 | **SFRI Punjab — Guide-V** (Soil Fertility Research Institute, Government of Punjab) | The N-P-K target ranges for each soil type, and the recommendation method | A Government of the Punjab publication with a worked example |
| 2 | **PCPA Cotton Book** (Punjab Crop Protection Agency) | Real per-acre cost breakdown; Urea 2.35 bags, DAP 1.04 bags, 7 irrigations, 19 maund yield | Government publication of actual field figures |
| 3 | **PAU Package of Practices Rabi 2025-26** (University of Agriculture Faisalabad) | Seed rates, varieties, sowing windows; Punjab average yield 20.92 quintals/acre | The university's own recommendation for its own region |
| 5 | **FAO Irrigation and Drainage Paper 56** | Crop coefficients (Kc), the ETc method, effective rainfall | An international standard used worldwide |
| 5 | **NFDC Pakistan Fertiliser Statistics** | Retail prices of urea, DAP and MOP | The official price series, not an estimate |
| 6 | **World Bank Climate Portal / NASA POWER** | Monthly temperature, rainfall and ETo normals, 1991–2020, for 30 districts | Internationally published climate dataset |
| 8 | **Punjab and Sindh Agriculture Departments** | District list, crop calendars, soil type distribution | Official provincial record |

---

## Appendix B — What Is NOT Claimed

Written down on purpose, so nobody has to guess what this project promises.

| We do **not** claim | Why |
|---|---|
| That AgriPulse identifies crop diseases from a photo | We have no trained model and no Punjab photo dataset. **Future work.** |
| That the numbers replace an agronomist's judgement | They apply published averages to one field. A local officer's advice still comes first. |
| That the app works in live weather | It uses **30-year climate normals**, not a live feed. It tells you what March in Faisalabad usually looks like. |
| That plans are stored for later | They are not. Plans live for the session and clear on reload. The app says so on screen. |
| That it works in every district of Pakistan | 30 districts are seeded. The data model supports more; we filled the ones we could source. |
| That it needs a server, cloud or subscription | It runs on one laptop. That is deliberate — it is also the reason there is no subscription. |
| That it works as a mobile app, in Urdu or with audio | It is a browser app that installs on a laptop. The scope is English text and a clean, keyboard-friendly screen. |

---

These eight sources are the foundation of every number in this proposal. Each one is named on screen wherever its figures are used.

---

*Draft from `chat-history/media/1-FYP Proposal Template.docx`, following its section order exactly: Title → Tools → Problem Statement → Aim and Objective → Scope → Functional Requirements → Non-Functional Requirements → Particulars of the Students → Remarks. Source of truth for the project scope is `chat-history/outputs/A4.md`.*

---

## Appendix C — Demo rule: show, don't just say it

A supervisor cannot believe a claim that is not demonstrated. The demo machine
is one laptop, the router switched off, the network tab empty. The demo shows the
five screens — login, district and land setup, planner, what-if slider, and
fertiliser advice — and every number on screen carries its public source. The
messages you must hear during the demo are these:

1. No photo is used in the demo, because AgriPulse does not diagnose diseases.
2. No internet is used in the demo, because the app runs from local files.
3. No subscription or cloud is used in the demo, because the app runs on one
   laptop.
4. No main-crop claim needs a photo, because the demo shows the SFRI calculation
   on one soil test card, with the PCPA Cotton Book figure as the validation
   check.
5. The five crops are wheat, rice, maize, potato and tomato, with 5 soil types
   and 30 districts. Cotton is used only as a published calculation check.
6. The result clears when the farmer can read his own loss, water, bags, cost,
   yield and return on screen, with every number traced to its source.

The demo machine is a single laptop with the router switched off. The demo shows
the five screens: login, district and land setup, planner, what-if slider and
fertiliser advice. Every number on screen carries its public source. No photo,
no internet, no subscription and no cloud is used.

