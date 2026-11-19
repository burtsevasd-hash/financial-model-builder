# Step 1. Parameter list and client questionnaire

Write the output in the language of the user's request.

Resolve every canonical artifact name through `references/language-and-files.md` from the skill root.

The eight blocks: Revenue drivers; Cost of sales; Operating expenses; People; Start-up investment and equipment; Working capital; Taxes and financing; Technical model settings.

## Prompt 1.1. Wide parameter list

```
We are building a financial model in the project folder attached. The context is in the folder, start with «Project passport».

Task: produce the full list of input parameters for this business.

A parameter is a value the user of the model types in, not one calculated from others. Calculated figures (revenue, cost of sales, profit, production capacity, depreciation) do not belong in the list.

Split the parameters into 8 blocks: Revenue drivers; Cost of sales; Operating expenses; People; Start-up investment and equipment; Working capital; Taxes and financing; Technical model settings.

Output one table with these columns:
1. Block
2. Parameter
3. Unit of measurement (a unit only, no formulas, no lists of options)
4. Type: driver / norm / assumption
5. Source: client / market / cost calculation / legislation
6. Why it is needed (one sentence)

Respect the format and size from the passport: parameters that suit a chain or a factory do not belong in a single location model. If a block lacks data, list the questions for the client after the table.

Save the table to the project folder as «Parameters». This is a draft, we will edit it.
```

## Prompt 1.2. Reviewer

```
You are an external reviewer accepting a financial model from an analyst. The list of input parameters is in the «Parameters» file, attached or in the project folder. The business: [two lines from the passport: business and format, scale].

Review the list and find:
1. Calculated figures that ended up among the parameters.
2. Duplicates: the same thing under two names or in two blocks.
3. Parameters with no unit, or with a formula or a choice instead of a unit.
4. Blocks missing for a monthly P&L, a monthly cash flow statement, the investment need and the payback period.
5. Parameters that are excessive for a business of this size.

Output a table: Row | Finding | What to do. Do not rewrite the list itself.
```

Ask a different model for the review than the one that produced the list.

## Prompt 1.3. Edits, mandatory parameters, file

```
Edit the «Parameters» file in the project folder.

Reviewer findings:
[paste the table from prompt 1.2, striking out the ones you disagree with]

My own notes:
[what to remove, what to add, what to change]

After the edits add a column «Required for the base model» with yes or no. The base model is a monthly P&L and cash flow statement, the investment need and the payback month. Mark «yes» for anything those forms cannot be built without.

Save the same file: one table, headers in the first row, a filter on the headers, wrapped text, column widths to fit the content.
```

## Prompt 1.4. Client questionnaire

```
The project folder is attached. Context in «Project passport», parameters in «Parameters». Build a questionnaire for the first client meeting, covering the parameters whose source is «client».

Questions:
1. One question per parameter. Merge them where one question settles several.
2. Ask through the client's own situation, not in jargon. Not «what is your conversion rate», but «out of the people who walk in, how many usually leave having bought something».
3. Order: format and product first, then customers and sales, then expenses, people, equipment, and money and taxes last.
4. Under each question a hint «if you do not know»: how to estimate it, or write «I do not know» and we will take it from the market.

Deliver the questionnaire as one HTML page «Client questions» in the project folder:
- an introduction of three or four sentences: why the questions, how long it takes, that «I do not know» is a fine answer;
- questions grouped in blocks, each with an answer field, a hint and a label saying which unit the answer should be in;
- at the bottom a button that copies all answers as «Parameter: answer» text, and a button that saves the same text as a file;
- answers persist in the browser so the client can come back and finish;
- calm, clean design, large type, comfortable on a phone, no logos and no company names. One file, no external libraries.

Open the page and check that the buttons work.
```

**STOP 1.** Show the list to the finance professional before the questionnaire. Build the questionnaire only against a confirmed list.
