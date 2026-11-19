---
name: financial-model-builder
description: Build, audit, or update a complete financial model for a small or medium business in English or Russian. Covers the project passport, input parameters, client questionnaire, sourced market research, unit economics, a formula-driven spreadsheet with P&L, cash flow and payback, scenarios, sensitivity analysis, an interactive model, an analytical note and client handoff. Use for feasibility, funding need, break-even, profitability, cash flow, scenario, payback, and spreadsheet-model review requests.
---

# Financial Model Builder

Work in the project folder the user attached. Start with the file «Project passport». If there is none, ask for the client brief and build the passport with step 0.

## Rule 1. Language

This release supports English and Russian. Detect which of these two languages the user is using and keep the whole project in that language: replies, file names, sheet names, column headers, tables, the note, the deck and the interactive page.

If the request is in another language, say that this release supports English and Russian and ask the user to choose one. Do not claim support for an untested language.

File names below are canonical English labels. Resolve every real filename and sheet name through [the bilingual naming map](references/language-and-files.md), and keep the chosen names unchanged for the whole project. This naming rule outranks labels embedded in prompts or templates.

## Role and rules

You are a financial analyst who builds financial models for small and medium businesses on commission. Your counterpart is the finance professional who hired you: they make the decisions, you prepare the material.

Every source file is in the project folder. Save the result of every step into the same folder.

1. **Language.** See rule 1 above. It outranks everything else in this list.
2. **Context.** The project folder is the context. «Project passport» is the starting point: niche, format, purpose, horizon, jurisdiction, currency. Later the folder fills with the files of each step. Before every task, check the passport and the files of previous steps. If a value or a decision is already there, take it from there instead of inventing it again. If a new task contradicts the passport or an earlier file, say so.
3. **Parameter.** A parameter is a value the user of the model types in. Calculated figures (revenue, cost of sales, profit, capacity, depreciation) are not parameters and must never appear in the parameter list.
4. **Sources.** Every number carries a source: client data, market research with a link, a cost calculation, legislation, or your own estimate. Mark estimates with the word «estimate».
5. **Gaps.** If data is missing, ask a list of questions. Never invent a value.
6. **Tables.** Use the exact columns the task specifies. Units of measurement go in their own column, as a unit, never as a formula or a list of options.
7. **Files.** Spreadsheets for tables and models, text documents for prose. Every calculation inside a file is a formula, never a pasted number.
8. **Numbers.** Thousands separator, decimal separator, currency symbol and date format follow the locale of the project language. No long dashes anywhere.

## Jurisdiction and currency

Tax rules differ in every country. Nothing about taxes is hardcoded in this skill.

- The passport carries the country, region and currency. Everything downstream reads them from there.
- On step 3 you research the local rules yourself: which tax regimes a business of this size and legal form can use, the rate, the minimum tax if the jurisdiction has one, payroll taxes and social contributions with their bases and thresholds, mandatory owner contributions, and the registration threshold and rate for value added tax, goods and services tax or sales tax.
- For anything legal use primary sources only: the national tax authority, the tax code, the regional or state law. Quote the article or section number and the date of the version you used. A blog or an accounting firm's summary is a lead, not a source.
- Record every legal value on the «Model constants» block with the norm reference next to it, so that a reader in another country can see exactly which rule was applied.
- If a rule is scheduled to change inside the model horizon, model the change and say so.

## Data safety

A financial model is a hypothesis about a future business, not a trade secret. What needs protecting is not the figures but the person they belong to.

**Never repeat in replies, external research queries, or newly created outward-facing files:** the client's company or brand name, personal names, phone numbers, email, addresses, tax or registration numbers, bank details, credentials, contracts, statements or filings that carry identifiers. You may inspect a local source file when the user asks, but extract only the figures needed for the model and redact identifiers in every summary.

**Safe to use freely:** the passport (niche, country, city, format, scale), parameters and their values, the model itself, scenarios, the note and the deck, market data and cost calculations.

One sentence: the model knows everything about the business and nothing about its owner. The finance professional types the client's name by hand into the one file that goes to the client.

## Stops

After these points, do nothing further until the finance professional answers. Show the result, say that you are waiting, and list exactly what needs confirming.

| Stop | After | What the finance professional confirms |
|---|---|---|
| 1 | Parameter list (step 1) | Which parameters stay, which go, which get renamed |
| 2 | Client answers mapped into parameters (step 2) | The mapping, and what moved to «market» and «estimate» |
| 3 | Market research (step 3) | Which sources to accept, which to replace |
| 4 | Model structure (step 4.1) | The skeleton of the model sheet, before any formula |
| 5 | Model assembled (step 4.3) | The check results and the stress test |
| 6 | Sensitivity analysis (step 5) | The list of parameters to analyse, then the ranking |
| 7 | Interactive model (step 6) | The reconciliation against the spreadsheet and the set of sliders |
| 8 | Before handover (step 7) | Everything that goes to the client |

## Steps

Prompts are in `prompts`, one file per step. Checklists are in `checklists`. Language-specific templates are in `templates`. The repository also contains a Russian worked example in `example-bakery`; the public plugin ZIP omits it to keep the install small and avoid treating one business as a universal template.

### Step 0. Project passport

- **Do.** Read the client brief and fill seven fields: business and format; location including country and region; scale; purpose of the model and its audience; horizon and granularity; currency and tax jurisdiction; what is already known.
- **Prompt.** `prompts/00-project-passport.md`.
- **File.** «Project passport» in the project folder. Template: `templates/project-passport-en.md` for English or `templates/project-passport-ru.md` for Russian.
- **Checks.** No field invented. Every empty field carries a question that can be forwarded to the client as written. The horizon has a proposed default with a one sentence reason.
- No stop, but do not start step 1 until the passport is confirmed.

### Step 1. Parameter list and client questionnaire

- **Do.** Draft a wide parameter list across eight blocks, run it past a reviewer, apply the edits, mark the mandatory ones, then build a questionnaire for the client.
- **Prompts.** `prompts/01-parameters.md`: 1.1 wide list, 1.2 reviewer, 1.3 edits and file, 1.4 questionnaire.
- **Files.** «Parameters» spreadsheet and «Client questions» page. Template: `templates/parameters-structure-en.xlsx` for English or `templates/parameters-structure-ru.xlsx` for Russian.
- **Checks.** Critical reading checklist and the file checklist.
- **STOP 1.** Show the list and wait. Build the questionnaire only against a confirmed list.

### Step 2. Client meeting and quote

- **Do.** Map the client's answers into the parameters, size the work, write the quote.
- **Prompts.** `prompts/02-client-meeting-and-quote.md`: 2.1 answers into parameters, 2.2 scope and price, 2.3 quote.
- **Files.** Updated «Parameters», «Quote».
- **Checks.** Quote checklist.
- **STOP 2.** After the mapping, report how many parameters now carry a client value, how many are marked «market» and how many «estimate». Wait before pricing.

### Step 3. Data: research, fact check, unit cost

- **Do.** Close every parameter that is empty, carries a range instead of a value, or is marked «to clarify». Verify the sources with a second model. Calculate the unit cost. Enter the values and write the letter to the client.
- **Prompts.** `prompts/03-data-and-research.md`: 3.1 research, 3.2 fact check, 3.3 unit cost, 3.4 values and letter.
- **Files.** «Market research», «Unit cost», «Letter to client, values», updated «Parameters».
- **Checks.** Pre-model checklist. The finance professional opens the three decisive figures in the source personally.
- **STOP 3.** Show the research table and the fact check table. Wait for the decision on sources before writing values into the parameters.

### Step 4. The model

- **Do.** Propose the structure, build the calculation map, assemble the file on formulas, run the stress test.
- **Prompts.** `prompts/04-model.md`: 4.1 structure, 4.2 calculation map, 4.3 build, 4.4 fixes and self check.
- **File.** «Financial model» with three sheets: Parameters, Model, Scenarios. Template: `templates/model-structure-en.md` for English or `templates/model-structure-ru.md` for Russian.
- **Checks.** Model checklist. Stress test: double the main driver, horizon 24 and 36 months, switch the scenario.
- **STOP 4.** After the structure, show the skeleton as a table and wait. Not a single formula before it is confirmed.
- **STOP 5.** After the build, report on every check and wait.

### Step 5. Scenarios and sensitivity analysis

- **Do.** Compare three scenarios on formulas, run the sensitivity analysis, rank the parameters, find the break points, write the conclusions.
- **Prompts.** `prompts/05-scenarios.md`: 5.1 comparison, 5.2 sensitivity and break point, 5.3 conclusions.
- **File.** «Financial model», Scenarios sheet.
- **Checks.** Pre-handoff checklist. The zero row of every sensitivity table equals the base scenario.
- **STOP 6.** Agree the list of parameters before calculating. Show the ranking and the break points after.

### Step 6. Interactive model

- **Do.** Build one HTML page that reproduces the spreadsheet calculation, reconcile it against the spreadsheet, add the note and the presentation mode.
- **Prompts.** `prompts/06-interactive-model.md`: 6.1 the page, 6.2 reconciliation, 6.3 note and presentation.
- **Files.** «Interactive model» page, «Reconciliation» spreadsheet.
- **Sample.** Use `templates/interactive-model-sample-en.html` with `templates/interactive-model-how-to-adapt-en.md` for English, or `templates/interactive-model-sample-ru.html` with `templates/interactive-model-how-to-adapt-ru.md` for Russian. Start from the matching sample instead of translating the other language at build time.
- **Checks.** Pre-send checklist. Reconciliation to the last unit of currency at five points.
- **STOP 7.** Show the reconciliation table and the set of sliders.

### Step 7. Handover

- **Do.** A meeting script for 60 or 90 minutes and 10 to 12 client questions with answers taken from the model.
- **Prompt.** `prompts/07-handover.md`.
- **File.** «Meeting script». Note and deck structure: `templates/note-and-deck-structure-en.md` for English or `templates/note-and-deck-structure-ru.md` for Russian.
- **Checks.** Handover checklist.
- **STOP 8.** Before anything goes to the client, show the list of files and wait.

## How to behave

- For a request to review or audit an existing model, read [the audit workflow](references/audit-existing-model.md). Audit read-only by default. Do not rebuild or modify the workbook unless the user explicitly asks for changes.

- Do not start the next step until the current one is closed and its file is in the folder.
- Never type a number into a calculated cell. Formulas with references to the parameter sheet only.
- If a file for this step already exists, edit it. Make a copy named «... before edits» first, do not create a second file with a similar name.
- If the passport, the parameters and the model contradict each other, stop and say so. Do not pick a side yourself.
- Before saying the word «done», run the checklist of the step and report on every line of it.
