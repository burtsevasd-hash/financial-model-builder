# Structure of the financial model file. Template

Three sheets. No calculated number is ever typed by hand: formulas with references only.

## Sheet «Parameters»

The single input sheet. Columns: Block | Parameter or constant | Unit | Value | Source or comment | How it is used.

Blocks in order: model control; revenue; variable costs; people; fixed costs; start-up investment; working capital; taxes; financing and valuation; technical constants; staffing check.

Input cells light blue. Technical constants (zero, one, months in a year, check tolerance) sit in their own block so that no formula contains a bare number.

## Sheet «Model»

Columns: Row | Unit | How it is calculated | Total | M1 … M36.

Blocks of rows in order:

1. **Inputs and drivers.** Model month number, calendar month and year, months since opening, an «open for business» flag, the selected scenario, the scenario values, indexation factors by expense group, working days, ramp-up, seasonality, channel shares.
2. **P&L.** Sales, sales tax if the jurisdiction has one, revenue net of it, direct costs, gross profit and margin, variable costs by line, people by role, payroll contributions, fixed costs by line, depreciation, operating profit and margin, interest, tax-deductible items, taxable base, tax, net profit.
3. **Working capital.** Inventory, receivables and payables at opening and closing, the movements, net working capital.
4. **Cash flow, operating.** Receipts, payments for materials, commissions, payroll, rent, utilities, marketing, other, tax and contribution payments, total.
5. **Cash flow, investing.** Every line of the budget in its own payment month, the contingency, total.
6. **Cash flow, financing.** Owner contribution, drawdown, debt balance, instalment, interest, repayment, fees, owner distributions, total.
7. **Cash.** Net flow, opening and closing balance, shortfall against the minimum balance.
8. **Project results.** Project flow before financing, cumulative flow, terminal recoveries, flow for NPV and IRR, investment need, payback month.
9. **Checks.** Channel shares, cash reconciliation, shift cover by staff, a status for each.

## Sheet «Scenarios»

1. The scenario switch, one cell with a list.
2. A three by three table: key parameters as rows, scenarios as columns.
3. Headline figures of the selected scenario by year, linked to the model.
4. Project results: investment need, payback month, NPV, IRR, peak shortfall, debt outstanding.
5. Model checks: the statuses from the model sheet.
6. Scenario comparison, through a data table.
7. Sensitivity analysis, parameter ranking, break points.
8. Conclusions: five to seven sentences, each carrying a figure.
