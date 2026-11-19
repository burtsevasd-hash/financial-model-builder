# Step 3. Data: research, fact check, unit cost

Write the output in the language of the user's request. Nothing about taxes is hardcoded: the country and the currency come from the passport.

Resolve every canonical artifact name through `references/language-and-files.md` from the skill root.

## Prompt 3.1. Market research

```
The project folder is attached. Read «Project passport», «Parameters» and the client's answers. Research everything still open in «Parameters», on every sheet: rows with no value, rows with a range instead of a figure, rows marked «to clarify», including the Scenarios sheet and the model constants. The source label does not matter: «market», «estimate» and «to clarify» all get closed here. Do not touch rows that already carry a client value.

Before searching, ask me the questions that change the answer: the exact format, the district, the period of the data, what counts as a comparable. Search after I reply.

Requirements:
1. For every parameter: a value for our format and city from the passport, the market range, the source with a link and a date, a confidence level (high, medium, low) and one sentence saying why.
2. For the main revenue driver [name of the driver from «Parameters»] find comparables: [format and type of location from the passport] in cities of a similar size, their revenue and the value of that driver. This is the main driver of the model, it needs more than one source.
3. Sources no older than two years, for the country and region in the passport. For taxes, contributions and statutory rates use primary sources only: the national tax authority, the tax code, the regional or state law. Give the article or section number and the date of the version.
4. Close the whole tax block for this jurisdiction: the tax regimes available to a business of this legal form and size, the rate of each, the minimum tax if one exists, payroll taxes and social contributions with their bases and thresholds, mandatory owner contributions, and the registration threshold and rate for value added tax, goods and services tax or sales tax. Say which regime you recommend and why.
5. If a parameter has no data, say so and propose how to estimate it indirectly. Never invent a value.
6. Use the units from «Parameters».

Output a table: Parameter | Value | Range | Source (link, date) | Confidence | Comment. Save it to the project folder as «Market research», with working links.
```

## Prompt 3.2. Fact check by a second model

```
The project folder is attached. «Market research» holds a table of market values with sources, produced by another model. Review it as an external reviewer with internet access. The business: [two lines from the passport: business and format, scale].

For every row:
1. Open the source. Does it support the value and the range? If the link is dead or the figures differ, flag it.
2. Find one independent source for the same parameter, no older than two years, for our region and format. Compare.
3. For taxes, contributions and statutory rates check against the primary source: the national tax authority, the tax code, the regional or state law. Quote the article or section.
4. Flag rows where the value does not fit our format or city, or where the source is weak: advertising, a franchise sales page, a classified listing.
5. For rows with low confidence, look for stronger classes of source: official statistics, point of sale data, industry research, academic publications.

Output a table: Parameter | Value from the research | Confirmed / Discrepancy / Cannot verify | Second source (link, date) | What to do. Do not rewrite the research file.
```

**STOP 3.** Show both tables. The finance professional opens the three decisive figures personally.

## Prompt 3.3. Unit cost and its share of revenue

```
The project folder is attached. Calculate the share of direct costs in revenue for this business and save the calculation to the folder as «Unit cost».

1. Range: 8 to 10 items from the client's answers and the passport. If the folder holds the client's own costings, use them. If not, build typical ones from industry references and mark the sheet «typical, replace with the client's data».
2. Sheet «Recipes» or «Bill of materials»: for every item the consumption of materials in natural units, the output unit, the packaging.
3. Sheet «Input prices»: the price of every input per base unit on the market of our city, with a link and a date. Watch the units: if consumption is in grams and prices are per kilogram, convert inside the formula. Check that the cheapest item comes out in units of currency, not thousands.
4. Sheet «Retail prices»: the price of every item at competitors of our format in our city, with a link.
5. Sheet «Calculation»: cost per item by formula, its share of the price, the sales mix in percent (an estimate from the format, label it as an estimate) and the weighted average share of direct costs in revenue.
6. Give three values of that share for the scenarios: pessimistic, base, optimistic, and explain what drives the difference. Compare the base value with the client's own guess from their answers and say whose figure is closer to reality and why.

Every calculation is a formula, every input sits in its own cell. Finish by saying which value to put into «Parameters» and into the Scenarios sheet.
```

## Prompt 3.4. Values into the parameters and the letter to the client

```
The project folder is attached. Enter the values into «Parameters» from «Market research», the fact check table and «Unit cost».

My notes on the sources:
[which figures to replace, which sources not to use]

Do this:
1. For every «market» row write the value and add the link and the date to the source column. Where sources disagree, take the one the fact check confirmed and note it in the comment.
2. Turn ranges into values: seasonal expenses by month, the ramp-up curve by month.
3. Fill the Scenarios sheet: the main driver and the share of direct costs across three scenarios, from the ranges in the research and the unit cost calculation.
4. On the model constants close every «to clarify» row and add the local tax rate with a reference to the law and the article.
5. For «estimate» rows propose a value with a reason: the main driver from comparables, the opening stock from the days of cover and the daily consumption, the month of borrowing from the month of the large payment.
6. Write the letter to the client with every value closed at this step: a table of Parameter | Proposed value | Where it comes from (source with a link, or our estimate and why). Two sentences before the table: these are our proposals, please confirm or correct them, we calculate the model after your reply. A separate paragraph after the table asking for the documents that would replace our typical assumptions. No names and no company name. Save it as «Letter to client, values».

Save «Parameters», and mark every row filled at this step «awaiting client confirmation» in the comment. Report: how many rows filled, how many awaiting confirmation, whether any parameter is still without a value.
```
