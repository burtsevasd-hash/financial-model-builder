# Step 2. Client meeting and quote

Write the output in the language of the user's request.

## Prompt 2.1. Client answers into the parameters

```
A file with the client's answers has appeared in the project folder: the export from the questionnaire plus my notes from the first meeting. Map them into «Parameters».

Do this:
1. Add two columns: «Value» and «Client comment». For every parameter the client answered, write the value in the right unit and their own words, briefly, in the comment. Source becomes «client».
2. Where the client said «I do not know», set the source to «market» if it can be found in open data or by analogy, or «estimate» if it is specific to their location. Leave the value empty.
3. If the file has a Scenarios sheet, fill it from the client's answers. Leave it empty if they gave no figures and note that in the summary. Do not touch the model constants except rows marked «to clarify» that the client answered.
4. If the client asked to drop or add something, do it and mark the comment «at the client's request».
5. If the meeting clarified any passport field, update «Project passport» and say what changed.

Save the same file. Then report: how many parameters now carry a client value, how many are marked «market», how many «estimate», and list the «market» ones for the next step.
```

**STOP 2.** Show the summary and wait.

## Prompt 2.2. Scope and price

```
Size the work and price the financial model for this project. The passport and «Parameters» are in the folder.

Build two packages:
1. Base: the model over the horizon from the passport, with a P&L, a cash flow statement, the investment need and the payback period, and a scenario switch driven by the Scenarios sheet.
2. Extended: everything in the base plus sensitivity analysis, an analytical note, a decision deck and an interactive version of the model.

For each package list the stages with hours: closing the «market» parameters, building the model, checks and tests, scenarios and analysis, preparing the materials, the results meeting. There are [number from the summary of prompt 2.1] «market» parameters.

Propose a price for each package for a small business in this country and region, in the currency from the passport. My own benchmark: [hourly rate or the price of comparable past work, if any]. Explain what drives the price and where it can go up or down.

Output a table: Stage | Base, hours | Extended, hours. Under it the price of each package and the delivery time in working days.
```

## Prompt 2.3. Quote

```
Write the quote from the calculation above: [if you changed the prices, give the final ones].

One page:
1. Two sentences on the client's task, taken from the passport, with no company name and no personal names.
2. A table: What is included | Base | Extended. Rows: scope of work, what the client receives, delivery time, price.
3. Three sentences on why the extended package fits this particular task.
4. What you need from the client to start, and by when.
5. Payment terms and how long the offer stands.

Plain language, no terms that need explaining. Address the reader neutrally, I will type the name myself.
Save it to the project folder as «Quote».
```
