# Step 4. The model

Write the output in the language of the user's request.

## Prompt 4.1. Model structure

```
The project folder is attached. Using «Parameters», propose the structure of the financial model for this business. Three sheets: «Parameters» (one input sheet holding both the parameters and the constants, merging the current sheets), «Model» by month, and «Scenarios» with a switch and a three by three scenario table at the top and the headline figures of the selected scenario by year below, linked to the model.

The «Model» sheet runs by month over the horizon from the constants. Blocks: inputs (start date, horizon, scenario values driven by the switch, everything else linked from the parameter sheet); P&L with gross and operating margin; working capital: inventory, receivables and payables, with a note on which of them this business actually has; cash flow split into operating, investing and financing, opening balance of the first month is zero; results: investment need, payback month, NPV, IRR. The «Scenarios» sheet: switch, scenario table, headline figures of the selected scenario by year.

Build the structure only from what can be calculated with the parameters and constants that exist. Leave out any row whose data is missing. Output the structure as a table: Block | Row | How it is calculated, in one plain sentence. Rows in the order they will appear in the file. Calculate nothing, this is the skeleton only. End by asking what I want to change.
```

**STOP 4.** Agree the skeleton before a single formula.

## Prompt 4.2. Calculation map

```
Using the agreed structure, build the calculation map: for every row of the model say which parameters, constants and other rows it comes from, and write the formula in words.

Output a table: Block | Row | Comes from (names of parameters and rows) | Formula in words. For example: «Retail revenue = transactions per day × average transaction × working days × retail share × seasonality factor × ramp-up factor».

After the table: the list of parameters and constants that appear in no formula. Such a parameter means the structure is missing a row, propose it. If a row cannot be calculated from the available data, drop it from the structure and say that you did. Calculate nothing.
```

## Prompt 4.3. Build the file

```
Build the «Financial model» file in the project folder from the agreed structure and calculation map.

Every calculation is a formula referencing the parameter sheet and the scenario table, not one number typed by hand. Every row carries a «How it is calculated» column. Built-in checks: channel shares add up to 100 per cent, closing cash equals opening cash plus the flow, payback not reached turns the cell red.

Formatting: thousands separators and no decimals on money, one decimal on percentages, block headings bold on a light grey fill, input cells light blue, wrapped text, column widths to fit.

Open the file and confirm that every formula calculates without errors at a horizon of 24 and of 36 months. In your reply list the assumptions you made yourself.
```

## Prompt 4.4. Fixes and self check

```
Fix «Financial model» in the project folder against my notes:
[what is wrong, from the checklist and the stress test]

After the fixes run the checks and report on each: every formula calculates without errors; no hand-typed numbers on the calculation sheets; every parameter is used; channel shares add up to 100 per cent; the cash flow statement reconciles in every month; doubling the main driver raises profit and brings payback forward; the model calculates at a horizon of 24 and of 36 months; switching the scenario changes the result.

Save the same file. In your reply: what you fixed, the check results, and what still worries you.
```

**STOP 5.** Report on the checks before moving to scenarios.
