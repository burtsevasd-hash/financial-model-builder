# Step 6. Interactive model

Write the output in the language of the user's request, including every label on the page.

Resolve every canonical artifact and sheet name through `references/language-and-files.md` from the skill root.

For an English project, start from `templates/interactive-model-sample-en.html` and `templates/interactive-model-how-to-adapt-en.md`. For a Russian project, start from `templates/interactive-model-sample-ru.html` and `templates/interactive-model-how-to-adapt-ru.md`. Do not translate the other language's sample at build time.

## Prompt 6.1. The interactive page

```
Using «Financial model» from the project folder, build an interactive model as one HTML page «Interactive model» in the project folder. Start from the language-matched sample named above. Every visible label stays in the language of this project.

1. The calculation on the page reproduces the formulas of the Model sheet one to one: the same rows, the same calculation map, the horizon and constants from the parameter sheet. Do not simplify and do not round on the way. Before building the interface, port the calculation row by row and reconcile it against the cached values of the spreadsheet across every month: a difference larger than one unit of currency means a porting error, not rounding.
2. The user moves only these parameters: [the list from the parameter ranking of step 5, usually six to eight]. Each gets a slider with a range of minus 30 to plus 30 per cent of the base value, a unit label and its influence rank. The scenario switch substitutes the values from the scenario table. A «Reset to base» button. A separate block of headcount steppers if shift cover depends on staffing. Every other parameter is hardwired as a constant.
3. Headline figures, large, recalculated on every move: investment need, payback month, net profit of the second year, closing cash at the end of the horizon, and a line saying whether the financing is enough against the sum of own funds and borrowing.
4. Charts: cumulative cash flow by month with the payback month and the trough marked, cash on hand by month with the funding gap shaded, revenue and net profit by year, cost structure of the second year.
5. A table by year, expandable to months on a button.
6. A «Margin of safety» block: for each slider the page finds the value at which payback inside the horizon disappears.
7. A «Model checks» block: the same checks as the spreadsheet, recalculated on every move.
8. One file, no external libraries, no internet. Works on a phone. Calm design, large type, numbers with thousands separators and the currency from the passport. No company name and no personal names, only the niche and the city.

Open the page and verify that at the base scenario the figures equal the Scenarios sheet of the spreadsheet. If they differ, fix the calculation, not the numbers.
```

## Prompt 6.2. Reconciliation against the spreadsheet

```
Reconcile «Interactive model» against «Financial model» and output a reconciliation table.

Points to reconcile: the three scenarios from the switch; the base scenario with the main driver at plus 20 per cent; the base with rent at minus 20 per cent; the base with the share of direct costs at plus 10 per cent; the base with investment at plus 20 per cent. For each point: investment need, payback month, net profit of the second year and closing cash at the end of the horizon, in the spreadsheet and on the page, and the difference.

Get the spreadsheet values by recalculating the file with the same parameters, not from a reconciliation sheet that may be stale. The only acceptable difference comes from rounding, up to one unit of currency. If the gap is larger, find the calculation row where it appears, fix the page and run the reconciliation again. Save the table to the project folder as «Reconciliation».
```

**STOP 7.** Show the reconciliation table and the set of sliders.

## Prompt 6.3. Analytical note and presentation mode

```
My notes on the page:
[what to change in the sliders, the figures, the charts, the design]

Apply them. Then add two blocks as separate tabs.

1. Tab «Note». An analytical note built on the Conclusions block of the Scenarios sheet and the files in the folder: the project and the purpose of the model from the passport; what the model shows at the current parameters, with investment, payback and second year profit, the figures substituted from the calculation so they move with the sliders; whether the money is enough against own funds and borrowing; the three scenarios and what separates them; the main parameters from the sensitivity analysis and how each moves the result; the conditions of entry, meaning the values of the main parameters below which the project does not pay back, calculated on the page; where the figures come from, with the key parameters, their values and their sources, estimates marked as awaiting the client's confirmation; what to verify before the start and what to monitor after opening. Plain language, short sentences, every one carrying a figure, no judgement words and no advice to go ahead or not. A button that downloads the note with the current figures as a document, and a button that opens print. Print styles are mandatory and separate: dark text on white, otherwise the note comes out pale and unreadable.

2. Tab «Presentation»: eight to ten screens, arrow keys and buttons, speaker notes under each screen, a button back to the sliders. Structure: the task; how much money is needed; the cash on hand chart with the gap shaded; when the money comes back; the cumulative cash flow chart with the payback point; what the profit will be; the margin of safety; the decisions that have to be made before the start, each with its price in money or in time; the risks; the bottom line. One idea per screen and no more than three figures, all from the page calculation.

At the foot of the page the date of the model and a line saying that the calculation follows the financial model in the spreadsheet and that the parameters were agreed with the client. Open the page, verify that the note and the screens change when the parameters move, check the printed note, and save the file.
```
