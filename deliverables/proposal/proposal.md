---
title: Project Proposal — AgriPulse
institution: Government Graduate College Satiana Road, Faisalabad
university: Government College University Faisalabad
department: Department of Computer Science
date: 2026-10-01
model: opencode/big-pickle
agent: opencode
template_source: chat-history/media/1-FYP Proposal Template.docx
specialist_roles_adopted:
  - sales-proposal-strategist — win themes, three-act narrative, evidence per claim
  - engineering-technical-writer — plain language, one idea per section, lead with outcome
  - project-manager-senior — exact requirements, realistic scope, testable acceptance
  - engineering-software-architect — technology choices with stated reasons
---

<div align="center">

**Government College University Faisalabad**
**Government Graduate College, Satiana Road, Faisalabad**
**Department of Computer Science**

# (PROJECT PROPOSAL)

</div>

---

## DATE

**Day:** 1 &nbsp;&nbsp; **Month:** October &nbsp;&nbsp; **Year:** 2026

**Project Code:** `MCSD-2026-FYP-___` *(assigned by the office)*

---

## Project Title

> **AgriPulse — A Soil-Test Driven Farm Planner that Tells a Punjab Farmer His
> Cost, His Water Need, His Fertiliser Bags and His Profit, Before He Sows.**

**Working name:** AgriPulse
**Name meaning:** *Agri* (agriculture) + *Pulse* (the beating of a crop's life, and
the name of Pakistan's staple grain family).

---

## Tools to be Used

### Frontend

| # | Tool | Why we chose it |
|---|------|-----------------|
| 1 | **React 18** | Most widely used UI library. Fast to build a single-page app. |
| 2 | **Vite** | Starts instantly in development. Small learning curve. |
| 3 | **Tailwind CSS** | Clean design without writing CSS by hand. |
| 4 | **Recharts** | Draws the radar chart and the cost bar chart from plain data. |
| 5 | **React Router** | Moves between the 5 pages of the app. |
| 6 | **Fetch API client** | Sends requests from the browser to the server. |
| 7 | **PWA (Service Worker + Manifest)** | Makes the app installable and loadable with no internet. |

### Backend

| # | Tool | Why we chose it |
|---|------|-----------------|
| 8 | **Node.js** | One language for the whole project — JavaScript on both sides. |
| 9 | **Express.js** | Makes the REST API in very few lines of code. |
| 10 | **MongoDB + Mongoose** | Stores users, land records and plans as documents. Runs locally, free. |
| 11 | **jsonwebtoken (JWT)** | Login token. Keeps one farmer's data separate from another's. |
| 12 | **bcrypt** | Hashes the password so the real password is never stored. |
| 13 | **Zod** | Checks every incoming request before the server accepts it. |
| 14 | **cors** | Lets the browser app talk to the server during development. |
| 15 | **dotenv** | Keeps secrets and settings out of the code. |
| 16 | **morgan** | Logs every request, so we can find bugs quickly. |

### Data files bundled inside the app

| # | File | Content | Rows |
|---|------|---------|------|
| 17 | `climate.json` | Monthly average temperature, rain, humidity and ETo for 30 districts | 360 |
| 18 | `cost.json` | Per-acre cost of every step, for 5 crops | 30 |
| 19 | `sfri.json` | The target N-P-K range for 5 soil types | 20 |
| 20 | `soil.json` | The 5 soil types of Punjab and their properties | 5 |

### Tools used to build and test

| # | Tool | Purpose |
|---|------|---------|
| 21 | **MongoDB Compass** | Looks inside the database like a spreadsheet. |
| 22 | **Postman** | Tests every API endpoint by hand. |
| 23 | **Node Test Runner (`node:test`)** | Runs the unit tests of the four calculation services. |
| 24 | **Visual Studio Code** | The code editor. |
| 25 | **Git + GitHub** | Version control and backup of the source code. |
| 26 | **Mermaid / draw.io** | Draws the system, data-flow and ER diagrams. |
| 27 | **Microsoft Word** | Writes this proposal and the final report. |

**Total: 27 tools. All are free. None need a paid licence.**

---

## Problem Statement

### The short version

A farmer in Punjab must decide **what to sow, how much to spend, and how much
fertiliser to buy — before the season starts.** Almost every tool that exists
today asks him for answers he does not have, or needs a signal his village does
not get.

### The long version

Pakistani farming decisions are made under three conditions at once: the farmer
has very little money, the decision is made once and cannot be undone until
harvest, and the information needed to make the decision is locked inside
government offices and paid services.

We studied **13 existing tools** — 5 working in Pakistan (Bakhabar Kissan,
Kissan, Agrixia, MandiOye, PAR) and 8 international ones (PlantVillage/Nuru,
Leafwise, LeafAid AI, Kisan Sarathi, Kisan Suvidha, Miraitu, KisanPe,
CropKhata/Farm Manager). We found **four** separate problems.

---

### Problem 1 — Farming decisions are made without real information

| What goes wrong today | Why it happens |
|---|---|
| The crop is chosen without knowing what the soil holds | Soil test data exists, but nobody turns it into a decision |
| Fertiliser is applied by habit, not by need | The exact quantity is never calculated for the farmer's own field |
| The farmer cannot *see* what his soil is short of | The result stays as a number on a printed slip |
| Money and water are wasted on the wrong dose | Nobody links the soil result to the cost sheet |

The soil test already exists. The Government of the Punjab runs the labs and
prints a card with the numbers on it. **The card stops there.**

---

### Problem 2 — There is no planning before the harvest

| What goes wrong today | Why it happens |
|---|---|
| The total expense is unknown on the day of sowing | Costs are only known after the season ends |
| The water requirement is unknown | Nobody tells him how many irrigations and how many litres |
| The expected yield and profit are unknown | No one can tell him if the crop will even pay for itself |
| Two crops cannot be compared side by side | Each calculation is done on paper, one at a time |
| Inputs cannot be changed and re-checked | The plan is written once and never revisited |

Farmers do plan. They do it in their heads, from memory, using last year's
prices. When urea goes up by twenty percent, nobody notices until the bill comes.

---

### Problem 3 — Disease names and cures are in a foreign language

| What goes wrong today | Why it happens |
|---|---|
| Advisory books are written in English | The farmer reads Urdu |
| The farmer cannot tell two diseases apart from a description | No photo available |
| The cure is not given in a local language | No remedy in Urdu |

**We state this honestly: this problem is NOT solved in this project.** It is
listed as future work in the Scope section below, and the reason given there is
a good reason.

---

### Problem 4 — Existing tools depend on hardware and paid services

| What it costs today | Detail |
|---|---|
| **Physical weather stations** | Bakhabar Kissan runs **300+ ground stations**. That cost cannot be removed from their model. |
| **A working internet connection** | Field signal is patchy. Every online-only tool fails in the field. |
| **A monthly data subscription** | B2B agri-data products (e.g. PAR) sell data, not decisions. |
| **A trained model on a server** | PlantVillage and Leafwise are free and offline, but both cover **38 US and temperate-horticulture classes** — not Punjab's field crops. |

So the farmer either pays, or goes blind.

---

### Why the existing tools do not solve this

| Tool | What it does well | What it cannot do |
|---|---|---|
| Bakhabar Kissan | Weather and advisory, 15.8M users | No cost, water or ROI figure. Needs a network. Runs 300 physical stations. |
| MandiOye | **18 free calculators** — closest to us | Asks you to **already know** the nutrient requirement. No soil-test logic. Online only. |
| Agrixia | GPS land, mandi prices, Urdu | Still pre-launch (waitlist). Marketplace first. No calculator, no soil test. |
| PlantVillage / Nuru | Free, offline, disease ID from a photo | **38 classes of US horticulture crops.** Cotton leaf blight of Punjab is not in that list. |
| Kisan Sarathi (India) | Advisory at national scale, 2.95 crore farmers | State-funded at national scale. Not an entry point for an FYP. |

**The gap, in one line:**

> Every existing tool asks the farmer for what he **already knows**. AgriPulse
> starts from the one thing he **actually has** — a soil test card and his land
> size — and works out the rest.

MandiOye's fertiliser calculator needs the nutrient requirement as an *input*.
The SFRI formula needs only the **soil reading**. That is the whole difference,
and it is a real difference.

---

## Aim and Objective

### Aim

To build **AgriPulse**, an offline web application that turns a soil test card
and a land size into the four decisions a farmer must make before sowing:
**cost, water, fertiliser bags and profit** — in Pakistani Rupees and litres,
with every number showing the government or FAO publication it came from.

### Objectives

Each objective below is written so that it can be **marked pass or fail**.

| # | Objective | How we will prove it was achieved |
|---|-----------|-----------------------------------|
| **O1** | Read a soil test card and show the farmer what his soil is short of, using a radar chart. | The radar shows the farmer's value against the target range for his soil type. |
| **O2** | Calculate the **exact** number of Urea, DAP and MOP bags using the **Government of the Punjab SFRI Guide-V formula** — not an invented formula. | Run it for cotton and land the result at **2.35 bags Urea + 1.04 bags DAP per acre**, the figure published in the PCPA Cotton Book. |
| **O3** | Calculate the total cost of sowing, broken down line by line (land preparation, seed, fertiliser, labour, water, transport). | Every line matches the PCPA Cotton Book / PAU Package of Practices figure for that crop. |
| **O4** | Calculate the total water need in litres and the number of irrigations, using the **FAO-56** method. | Same formula and same inputs; crop coefficients cited from FAO-56 Table 12. |
| **O5** | Show expected yield, net profit, ROI and the break-even price. | Yield band comes from PAU district averages; price from NFDC. |
| **O6** | Let the farmer move sliders and see cost, profit and ROI change **immediately**, so he can compare crops before committing. | The simulator recomputes **in the browser** — zero network calls. |
| **O7** | Make the app work **fully offline**, so field signal is never a problem. | Turn the router off. Every screen still opens and every calculation still runs. |
| **O8** | Show the **source** of every number on the screen, so the farmer and the supervisor can both trust it. | Citations sit next to the figures, not hidden behind a help icon. |
| **O9** | Keep the farmer's data private — one farmer can never see another's. | JWT login. Every protected query is filtered by the logged-in user's ID. |

### What the farmer learns, in one sentence

The system should teach one idea that no calculator can: **more land with the
same budget raises total profit but *lowers* the return on each rupee.** That
single observation is the intellectual content of the project.

---

## Scope of the Project

### 1. In scope — what we WILL build

| # | Module | What it does | Page |
|---|--------|--------------|------|
| **M0** | **Login and Register** | Email and password, JWT, one account per farmer | 1 |
| **M1** | **Land and Climate Profiler** | District, area in acres, soil type, and the climate card for that district and month | 2, 3 |
| **M2** | **Resource and Financial Planner** | Full cost breakdown, water in litres, yield, net profit, ROI, break-even | 4A |
| **M3** | **NPK Soil Fertiliser Advisor** | Deficiency ranking, exact Urea/DAP/MOP bags, cost, radar chart | 5 |
| **M4** | **What-If Simulator** | Sliders for area, budget and crop; live recompute; reset to baseline | 4B |

**Five pages. Four modules. Six API route files. Nine backend packages.**

### 2. Out of scope — what we will NOT build, and why

We are writing this list down **on purpose**. A project that says no to things is
a project that gets finished.

| # | Not building | Why |
|---|---|---|
| 1 | **Leaf disease identification from a photo** | Needs a trained model. We have no GPU, no labelled dataset and no server. The existing free models cover 38 US horticulture classes, not Punjab's crops. **Deferred to future work.** |
| 2 | **Mandi (market) price feed** | Needs a paid live feed and a server. It would change the project into a market app. |
| 3 | **Live weather API** | Needs the internet. The offline promise is the project's core. |
| 4 | **IoT sensors, weather stations, satellite** | Hardware is the cost we are removing, not adding. |
| 5 | **Saved plans, history, PDF reports** | Would double the work. Plans last for the current session only, and the app says so on screen instead of hiding it. |
| 6 | **Urdu voice audio, chat, notifications** | Text only. Not enough time, and not what the problem statement needs first. |
| 7 | **A native mobile app** | The web app installs on a phone as a Progressive Web App. A second codebase is not needed. |
| 8 | **Marketplace, job board, livestock records** | Belongs to a different product. |
| 9 | **Multi-farmer or organisation accounts, roles, admin panel** | One farmer, one account. |
| 10 | **Cotton, sugarcane and 7 other crops** | Five crops only: **wheat, rice, maize, potato, tomato** — the five with both agronomy data and disease data available for Punjab. |

### 3. Crops, soil types, districts, data volume

| Item | Count | Detail |
|------|-------|--------|
| Crops | **5** | Wheat, Rice, Maize, Potato, Tomato |
| Soil types | **5** | Sandy, Sandy Loam, Loam, Clay Loam, Clay |
| Districts | **30** | Punjab and Sindh, from the provincial Agriculture Departments |
| Climate records | **360** | 30 districts × 12 months |
| Total reference rows | **420** | 30 districts + 360 climate + 5 soil types + 20 SFRI bands + 5 crops + 15 yield bands + 30 cost rows |
| User collections | **3** | user, land, plan |
| Model files in the repo | **0** | No machine learning model anywhere in the project |

### 4. Coverage of the four problems — the honest scorecard

We audited all **16** factors inside the four problems. This is the result.

| Problem | Factors in it | Fully solved | Partly solved | Not solved |
|---------|---------------|--------------|---------------|------------|
| P1 — Uninformed decisions | 4 | 3 | 1 | 0 |
| P2 — No financial planning | 5 | 4 | 1 | 0 |
| P3 — Disease diagnosis | 3 | **0** | **0** | **3 → future work** |
| P4 — Hardware dependency | 4 | 4 | 0 | 0 |
| **Total** | **16** | **11** | **2** | **3** |

**Two problems solved, one three-quarters solved, one declared as future work.**
All three unsolved factors belong to the module we removed, so nothing else is
affected. We would rather say this than claim coverage we cannot show.

### 5. Seven-week plan

| Week | Work | Gate — we prove it works when… |
|------|------|--------------------------------|
| 1 | Build the 4 data files and the seed script | **420 rows** are in MongoDB |
| 2 | Express server, JWT login, 6 routes, Zod checks | `POST /api/auth/login` returns a token |
| 3 | Screens 1–3 and the climate service | District and N-P-K save; the climate card shows |
| 4 | Screen 4 Tab A and the planner service | Cost, water, yield and ROI appear **with citations** |
| 5 | **Screen 5, the SFRI service, the radar chart** | **Bags match the PCPA published cotton figures** |
| 6 | Screen 4 Tab B, simulator, responsive layout, dark theme | Sliders recompute live; the mobile layout holds |
| 7 | Unit tests on 4 services, offline PWA, final report | `npm test` is green; the app works with the router off |

**Week 5 is the project. Every other week is ordinary engineering.**

### 6. Risks, and what we do about them

| # | Risk | Chance | Effect | What we do |
|---|------|--------|--------|------------|
| 1 | Scope grows during the build | High | High | The out-of-scope list above is signed off. Nothing is added without removing something. |
| 2 | The formula does not match published figures | Medium | **Very high** | Week 5 is reserved for exactly this test. If it fails, the formula is wrong and we fix it before anything else. |
| 3 | Reference data cannot be found | Medium | High | Every figure has a named public source that is downloadable. Fallback is NFDC plus provincial department rates. |
| 4 | Supervisor asks for the removed disease module | High | Medium | It is already written down as future work, with the reason. We do not pretend. |
| 5 | Offline mode breaks on refresh | Medium | Medium | The service worker is tested in week 7 with the router physically switched off. |

### 7. Deliverables

| # | Deliverable | When |
|---|-------------|------|
| 1 | This proposal | Now |
| 2 | Proposal presentation (PPT) | +1 week |
| 3 | Four guidance documents — SRS, SDD, Test Plan, API and Data | +2 weeks |
| 4 | The working codebase | +5 weeks |
| 5 | Final documentation and final presentation | +7 weeks |

---

## Functional Requirements

Every requirement below has a number, an owner module, and a test that can
fail. If a test cannot fail, the requirement is not finished.

### FR group A — Accounts (Module M0)

| ID | Requirement | Acceptance test |
|----|-------------|------------------|
| **FR-A1** | A visitor can register with full name, email and password. | `POST /api/auth/register` returns `201` and one `user` document exists. |
| **FR-A2** | A registered farmer can log in with email and password. | `POST /api/auth/login` returns a JWT that expires after 24 hours. |
| **FR-A3** | Passwords are never stored in plain text. | The `user` document contains a bcrypt hash, not the password. |
| **FR-A4** | A duplicate email is rejected. | `POST /api/auth/register` returns `409` for an email that already exists. |
| **FR-A5** | A protected page cannot be opened without a valid token. | Any protected request without `Authorization: Bearer` returns `401`. |
| **FR-A6** | A farmer cannot read another farmer's land or plan. | A query for another user's `landId` returns `404`, never the record. |

### FR group B — Land and Climate (Module M1)

| ID | Requirement | Acceptance test |
|----|-------------|------------------|
| **FR-B1** | The farmer selects a district from a list of 30. | `GET /api/ref/districts` returns 30 rows. |
| **FR-B2** | The farmer enters land area in acres, from 0.1 to 100. | Zod rejects `0`, `100.1` and `"six"`. |
| **FR-B3** | The farmer selects a soil type from 5 options. | `GET /api/ref/soil-types` returns 5 rows. |
| **FR-B4** | The system shows the climate card for the selected district and the current month. | `GET /api/climate?district=Faisalabad&month=3` returns temperature, rainfall, rain probability and humidity. |
| **FR-B5** | The climate card shows irrigation need and frost risk. | Both fields are present in the response and change with the district. |
| **FR-B6** | Land details are saved against the logged-in farmer. | `POST /api/soil/recommend` writes one `land` document with the farmer's ID. |

### FR group C — NPK Fertiliser Advisor (Module M3)

| ID | Requirement | Acceptance test |
|----|-------------|------------------|
| **FR-C1** | The farmer enters nitrogen, phosphorus and potassium in kg/ha from his soil test card. | The form accepts decimals; the server rejects negatives and non-numbers. |
| **FR-C2** | The system converts ppm to kg/ha for the farmer's area. | 1 ppm is treated as 1 kg/ha at one-acre depth; the unit is shown on screen. |
| **FR-C3** | The system ranks each nutrient as **Poor**, **Medium** or **Adequate** using the SFRI band table for that soil type. | Each nutrient returns a rank and the target range that produced it. |
| **FR-C4** | The system subtracts the soil value from the crop requirement to get the nutrient needed. | `needed = cropRequirement − soilTest`, in kg/ha. |
| **FR-C5** | The system converts the nutrient needed into **whole bags** of Urea, DAP and MOP, rounding **up**. | Urea 46% N gives 23 kg N per 50 kg bag; DAP 46% P₂O₅ gives 23 kg; MOP 60% K₂O gives 30 kg. `Math.ceil` is used. |
| **FR-C6** | The system multiplies per-acre bags by acres to get total bags. | 2.35 bags/acre over 6.2 acres returns 15 bags, not 14.5. |
| **FR-C7** | The system shows a radar chart of soil health against the target ring for that soil type. | The radar draws 4 axes: N, P, K and pH. |
| **FR-C8** | The system shows **0 bags** when the nutrient is already above target. | Potassium above the loam range returns `mopBags: 0` and the warning "above target range". |
| **FR-C9** | The system shows a "How this was calculated" panel on screen. | The panel lists all 4 steps and names SFRI Punjab Guide-V as the source. |
| **FR-C10** | The system shows the fertiliser cost in PKR. | Cost equals bags × the NFDC retail price for that grade. |
| **FR-C11** | **The validation test.** The calculator must match the published figure. | For cotton it returns **2.35 bags Urea and 1.04 bags DAP per acre**, matching the PCPA Cotton Book. |

### FR group D — Planner (Module M2)

| ID | Requirement | Acceptance test |
|----|-------------|------------------|
| **FR-D1** | The farmer selects one of 5 crops. | `GET /api/ref/crops` returns 5 rows. |
| **FR-D2** | The farmer selects the sowing month, from 1 to 12. | Zod rejects `0` and `13`. |
| **FR-D3** | The farmer enters a budget in PKR. | The budget is optional; when present it produces a headroom warning. |
| **FR-D4** | The system returns a cost breakdown with 6 named lines. | Lines are land preparation, seed, urea, DAP, labour, water, transport — each with its PKR amount and its source. |
| **FR-D5** | Each cost line shows its source on screen. | The citation string from `cost_table` appears next to the amount. |
| **FR-D6** | The system calculates total water in litres and the number of irrigations using FAO-56. | `ETc = Σ(ETo × Kc × days)`; net irrigation = ETc − effective rainfall; litres = depth_mm × 10 × acres × 4047 ÷ canal efficiency. |
| **FR-D7** | The system calculates expected yield in maund, using the district yield band. | Yield = band × acres, rounded to 1 decimal. |
| **FR-D8** | The system calculates net profit and ROI. | `profit = revenue − cost`; `roi% = profit ÷ cost × 100`. |
| **FR-D9** | The system calculates the break-even price per maund. | `breakEven = cost ÷ expectedYieldMaund`. |
| **FR-D10** | The system warns when cost exceeds budget. | Budget PKR 100,000 and cost PKR 184,300 turns the warning red. |
| **FR-D11** | The system shows a cost bar chart and three stat cards. | Water, yield and profit cards appear above the chart. |

### FR group E — What-If Simulator (Module M4)

| ID | Requirement | Acceptance test |
|----|-------------|------------------|
| **FR-E1** | The farmer can move a slider for area, budget and crop. | Each slider is keyboard accessible with 44px touch targets. |
| **FR-E2** | Numbers update **as the slider moves**, with no button press. | A change event triggers a recompute in under 50 ms. |
| **FR-E3** | The simulator makes **no network calls**. | The browser network tab stays empty while sliders move. |
| **FR-E4** | The simulator writes **nothing** to the database. | The `plan` collection row count is unchanged after 100 slider moves. |
| **FR-E5** | The screen shows baseline and scenario side by side, with the change as a percentage. | Cost, revenue and profit each show `Δ +x%`. |
| **FR-E6** | A "Reset to baseline" button restores the original plan. | One click restores the original area, budget and crop. |
| **FR-E7** | The screen states plainly that results are session-only. | The text "Session only. There is no save button." is visible. |

### FR group F — Reference data and seeding

| ID | Requirement | Acceptance test |
|----|-------------|------------------|
| **FR-F1** | One seed script loads all reference data into MongoDB. | `npm run seed` reports 420 reference rows inserted. |
| **FR-F2** | The script is safe to run twice. | Running it again reports duplicates skipped, no crash. |
| **FR-F3** | The API serves reference lists without a login. | `GET /api/ref/crops` works with no token. |

---

## Non-Functional Requirements

| ID | Category | Requirement | How we measure it |
|----|----------|-------------|-------------------|
| **NFR-1** | **Offline** | The app must work with the network **completely off**, including after a page refresh. | Turn the router off, reload every page, run every calculation. All succeed. |
| **NFR-2** | **Offline** | No runtime call to any external API, CDN, font host or analytics service. | Grep the source for `http://` and `https://` outside comments — result is empty. |
| **NFR-3** | **Performance** | A page must appear in under 2 seconds on a mid-range laptop. | Lighthouse performance ≥ 90. |
| **NFR-4** | **Performance** | Any single calculation must finish in under 300 ms. | Stopwatch on all 6 endpoints; slowest is logged. |
| **NFR-5** | **Performance** | Slider recompute must finish in under 50 ms. | Frame timing while dragging; no visible lag. |
| **NFR-6** | **Security** | Passwords are stored only as bcrypt hashes, never in plain text. | Read the `user` collection in Compass; only a hash exists. |
| **NFR-7** | **Security** | Every protected endpoint requires a valid JWT. | 6 protected routes tested with no token — all return `401`. |
| **NFR-8** | **Security** | No user can read or modify another user's data. | Cross-user access attempt returns `404`, and is covered by a unit test. |
| **NFR-9** | **Security** | All secrets come from environment variables, never from source code. | `.env` is in `.gitignore`; no key appears in any committed file. |
| **NFR-10** | **Data integrity** | Every calculated number must be traceable to a named public source. | Each API response carries a `source` field; spot-check 10 numbers against the publication. |
| **NFR-11** | **Correctness** | The four calculation services must be covered by unit tests. | `npm test` is green; at least 25 test cases, including the PCPA cotton check. |
| **NFR-12** | **Reliability** | Invalid input must be rejected with a clear message, never a server crash. | 15 malformed requests; all return `400` with a readable message, no `500`. |
| **NFR-13** | **Usability** | A farmer must finish "set up land → see fertiliser bags" in under 3 minutes without help. | Timed walkthrough with 3 people who have never seen the app. |
| **NFR-14** | **Usability** | No screen may require horizontal scrolling on a 360px phone. | Checked at 360px, 768px and 1280px. |
| **NFR-15** | **Accessibility** | Interactive controls must be keyboard reachable with a visible focus ring. | Tab through every page; focus always visible. |
| **NFR-16** | **Accessibility** | Colour must never be the only signal. Deficiency also shows the word LOW; excess shows HIGH. | Toggle to greyscale; every state is still readable. |
| **NFR-17** | **Maintainability** | No backend file may exceed 250 lines; business logic lives in services, never in routes. | A line-count script in the test run. |
| **NFR-18** | **Portability** | The app must run on Windows, Linux and macOS with one command. | Fresh clone, `npm install`, `npm run dev`. |
| **NFR-19** | **Privacy** | No farmer data leaves the machine. There is no telemetry of any kind. | Network tab is empty after a full walkthrough. |
| **NFR-20** | **Documentation** | Every number on screen must show its source, and every module must be documented. | Sources visible on screen; the 4 guidance documents complete. |

---

## Particulars of the Students

| Sr. # | Registration No. | Name in Full | Email | Contact # | CGPA | Signature |
|-------|------------------|--------------|-------|-----------|------|-----------|
| 1 | 2017-CS-___ | Abdullah | ______________________ | _______________ | ______ | __________ |
| 2 | ________________ | ______________________ | ______________________ | _______________ | ______ | __________ |

> **Note for the student:** the Registration No., Email, Contact # and CGPA cells
> are left blank on purpose. Those are personal facts and must be typed in by the
> student before submission. This agent will not invent them.

---

## Remarks

**Why a supervisor should approve this project**

1. **It solves a real problem for a real person.** Not a demo problem. A smallholder
   in Faisalabad makes a PKR 250,000 decision with no cost figure, no water
   figure and no exact fertiliser quantity.

2. **It does not copy anyone.** We audited 13 tools. Nobody, anywhere, combines
   total cost in local currency + water in litres + soil-test-derived fertiliser
   bags + offline operation + a what-if slider.

3. **The central algorithm is not ours, and that is the strength.** We implement
   the Government of the Punjab **SFRI Guide-V** formula and the **FAO-56**
   method, then prove the result lands on the figure published in the **PCPA
   Cotton Book**. The project can be checked against an official source.

4. **Every number on screen carries its citation.** This is unusual, and it is the
   single reason a supervisor can believe the output.

5. **The scope is honest.** We wrote down ten things we are *not* building, with
   reasons. We say plainly that Problem 3 is future work. A project that admits
   its limit is easier to supervise than one that hides it.

6. **It is buildable in seven weeks by one student.** Nine boring backend
   packages, no model file, no image dataset, no GPU, no paid API. The heaviest
   week is week 5, and it is reserved for the one calculation that matters.

7. **It works offline.** Field signal is a fact of life in the study area. We
   treat that as a requirement, not a limitation.

---

**Signatures and Date**

| Role | Name | Signature | Date |
|------|------|-----------|------|
| **Student(s)** | Abdullah | ____________________ | ____ / ____ / 2026 |
| **Project Supervisor** | ____________________ | ____________________ | ____ / ____ / 2026 |
| **Coordinator** | ____________________ | ____________________ | ____ / ____ / 2026 |
| **Head of Department** | ____________________ | ____________________ | ____ / ____ / 2026 |

**Approved:** ☐ YES &nbsp;&nbsp;&nbsp; ☐ NO

---

## Annexure A — Sources of Data

These are the public publications the system is built on. Each one is named on
screen wherever its figures are used.

| # | Source | What we take from it | Why it is trustworthy |
|---|--------|----------------------|-----------------------|
| 1 | **SFRI Punjab — Guide-V** (Soil Fertility Research Institute, Government of Punjab) | The N-P-K target ranges for each soil type, and the recommendation method | A Government of the Punjab publication with a worked example |
| 2 | **PCPA Cotton Book** (Punjab Crop Protection Agency) | Real per-acre cost breakdown — Rs 63,970/acre with land rent, Rs 43,970 without; Urea 2.35 bags, DAP 1.04 bags, 7 irrigations, 19 maund yield | Government publication of actual field figures |
| 3 | **PAU Package of Practices Rabi 2025-26** (University of Agriculture Faisalabad) | Seed rates, varieties, sowing windows; Punjab average yield 20.92 quintals/acre | The university's own recommendation for its own region |
| 4 | **FAO Irrigation and Drainage Paper 56** | Crop coefficients (Kc), the ETc method, effective rainfall | An international standard used worldwide |
| 5 | **NFDC Pakistan Fertiliser Statistics** | Retail prices of urea, DAP and MOP | The official price series, not an estimate |
| 6 | **World Bank Climate Portal / NASA POWER** | Monthly temperature, rainfall and ETo normals, 1991–2020, for 30 districts | Internationally published climate dataset |
| 7 | **Punjab and Sindh Agriculture Departments** | District list, crop calendars, soil type distribution | Official provincial record |

---

## Annexure B — What Is NOT Claimed

Written down on purpose, so nobody has to guess what this project promises.

| We do **not** claim | Why |
|---|---|
| That AgriPulse identifies crop diseases from a photo | No trained model. The free models that exist cover 38 US horticulture classes. **Future work.** |
| That the numbers replace an agronomist's judgement | They apply published averages to one field. A local officer's advice still comes first. |
| That the app works in live weather | It uses **30-year climate normals**, not a live feed. It tells you what March in Faisalabad usually looks like. |
| That plans are stored for later | They are not. Plans live for the session and clear on reload. The app says so on screen. |
| That it works in every district of Pakistan | 30 districts are seeded. The data model supports more; we filled the ones we could source. |
| That it runs on a server or in the cloud | It runs on one laptop. That is deliberate — it is also the reason there is no subscription. |

---

*Proposal drafted from `chat-history/media/1-FYP Proposal Template.docx`, following
its section order exactly: Title → Tools → Problem Statement → Aim and Objective →
Scope → Functional Requirements → Non-Functional Requirements → Particulars of
the Students → Remarks. Source of truth for the project scope is
`chat-history/outputs/A4.md`.*

