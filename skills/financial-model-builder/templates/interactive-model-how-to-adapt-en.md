# How to adapt the sample page to a new project

`interactive-model-sample.html` is a working page from a real project: a bakery in Kazan, Russia. Its visible text is Russian. Keep the structure and the engine, replace everything else.

The file has four parts. Three of them change on every project.

## 1. Project data: `const BASE` and `const SCEN`

At the top of the script. `BASE` is every parameter and constant from the parameter sheet as one object: horizon, first month, shares, rates, salaries, the investment budget, taxes, financing. `SCEN` is the three by three scenario table.

Produce it by reading the parameter sheet of the spreadsheet and building the object. Keep the key names from the sample where the meaning matches, add your own where the new business has different lines.

## 2. The calculation engine: function `runModel`

A row by row port of the model sheet. The row numbers in the code match the spreadsheet: `r[39]` is revenue net of sales tax, `r[69]` net profit, `r[117]` cash on hand, and so on.

How to work:

1. Export the formulas of the model sheet for one month column.
2. Port every row in the same order. Two passes: first the calendar, the indexation factors and sales, then everything else, because the sales tax flag has to look at the whole year.
3. Reconcile the engine against the cached values of the spreadsheet across every month and every row. A difference larger than one unit of currency is a porting error, not rounding.
4. Only then build the interface.

If the new business does not have a row, delete it and every reference to it rather than leaving it at zero.

## 3. Sliders: arrays `SLIDERS` and `STAFF`

`SLIDERS` is the list from the sensitivity ranking of step 5: key, rank, name, unit, bounds as a share of the base value, step, caption, output format. The flag `bad: 1` means that an increase makes the result worse, `abs: 1` means the slider sets an absolute shift rather than a multiplier.

`STAFF` holds headcount steppers. Include them when the model carries a shift cover check.

## 4. Text, which changes every time

- Header: niche, city, horizon, model date.
- The «Sources and assumptions» block at the bottom of the Model tab: four cards describing your own sources.
- The note: every paragraph rewritten for the new business. Figures are injected automatically through the `data-k` attributes.
- The presentation: function `buildDeck`, ten screens. The price of each decision is computed through `altMetrics`.
- Every label, button, heading and unit goes into the project language.

## Before handover

- The three scenarios on the page match the Scenarios sheet of the spreadsheet to the last unit of currency.
- The reset button restores the base values.
- The note prints dark on white.
- No external library, no network call. The page works offline.
- No company name and no personal names.
- Numbers, currency symbol and date format follow the locale of the project language.
