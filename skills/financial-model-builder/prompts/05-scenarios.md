# Step 5. Scenarios and sensitivity analysis

Write the output in the language of the user's request.

Resolve every canonical artifact and sheet name through `references/language-and-files.md` from the skill root.

## Prompt 5.1. Comparison of three scenarios

```
In «Financial model», on the Scenarios sheet, under the project results, add a «Scenario comparison» block: a table with the measures as rows and pessimistic, base and optimistic as columns.

Measures: revenue of the second year, net profit of the second year, operating margin of the second year, investment need, payback month, closing cash at the end of the horizon, NPV. Under the table a row «Is the financing enough»: the investment need against the sum of own funds and borrowing, for each scenario.

The comparison must be built on formulas and recalculate whenever any parameter changes: use a data table driven by the scenario switch cell. If a data table is not possible, build a helper calculation of the three scenarios and say so. Do not paste numbers.

Do not change the currently selected scenario. Open the file and verify that the base column of the comparison matches the figures of the selected scenario above.
```

Watch out: data tables may be excluded from automatic recalculation. Check the calculation mode and warn the finance professional if the workbook is set to «automatic except data tables», because the block will then show a stale cache.

## Prompt 5.2. Sensitivity analysis and break points

```
On the Scenarios sheet, under the comparison, add a «Sensitivity analysis» block for the base scenario.

1. First propose the list of parameters to analyse: those that multiply revenue or carry a large share of costs, whose source is «market» or «estimate», and that the client can influence. Leave out statutory constants and technical settings. Output the list with one sentence per parameter explaining why it is there, and wait for my confirmation.
2. After confirmation: move each parameter by minus 20, minus 10, 0, plus 10 and plus 20 per cent with everything else unchanged. For each, three tables: how net profit of the second year, the investment need and the payback month respond. Use data tables, do not paste numbers.
3. A «Parameter ranking» block: for each parameter the difference in net profit between plus 10 and minus 10 per cent, sorted from strongest to weakest. This is the risk table: what moves the result most.
4. A «Break point» block: for the two strongest parameters find the value at which net profit of the second year is zero, and the value at which payback no longer happens inside the horizon. Use goal seek or a formula, record the result and how you got it.

Open the file, verify that every table calculates and that the zero row of each matches the base scenario. In your reply give the ranking and both break points in words.
```

**STOP 6.** Agree the list before calculating, show the ranking and the break points after.

## Prompt 5.3. Conclusions and verification

```
My notes on the comparison and the sensitivity analysis:
[anything that does not add up or needs changing]

Apply them. Then, at the bottom of the Scenarios sheet, add a «Conclusions» block: five to seven plain sentences built on the figures in the file. What the base scenario gives; whether the financing is enough and in which scenario; which three parameters matter most and how they move the result; where the break point of the main parameter lies; what would have to change in the base scenario for the project to pay back inside the horizon and for the money to be enough. Every sentence carries a figure from the file, no judgement words.

Verify and report: the comparison recalculates when a parameter changes; the zero row of each sensitivity table equals the base scenario; the ranking and the break points agree with the scenario comparison; the conclusions match the figures. Save the same file.
```
