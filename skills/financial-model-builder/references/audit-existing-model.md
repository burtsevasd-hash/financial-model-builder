# Audit an existing financial model

Use this workflow when the user asks to review, check, diagnose, or audit an existing spreadsheet without asking for corrections.

## Default boundary

- Treat the request as read-only. Do not modify, overwrite, rename, recalculate-and-save, or create a corrected copy of the workbook unless the user explicitly asks for changes.
- Inspect the existing files before requesting a project brief or restarting the full model-building workflow.
- Preserve the user's language in the audit report. Translate labels only for explanation; quote workbook labels as they appear when needed to identify evidence.
- Do not infer missing business facts. Mark them as not verifiable and state what evidence is required.

## Audit checks

Check only what the available workbook supports:

1. **Formula integrity:** formula errors, broken or inconsistent references, hardcoded results in calculation areas, copied-formula drift, missing roll-forwards, circularity, and calculations with the wrong period or unit.
2. **Data types and units:** numbers stored as text, percentages represented inconsistently, dates or currencies with the wrong type or format, and incompatible units used in one calculation.
3. **Input provenance:** inputs without a source, date, unit, owner, or estimate label; assumptions presented as facts; and material values that cannot be traced to an input.
4. **Business logic:** revenue and cost drivers, taxes, investments, financing, working capital, cash balances, scenario controls, payback logic, and other relationships that are relevant to the model's stated purpose.
5. **Completeness and usability:** missing periods, unexplained rows, unavailable key outputs, inconsistent labels, and controls that do not affect the calculation as described.

## Evidence for every finding

Report each finding with these fields:

| Field | Required content |
|---|---|
| Location | Sheet and cell, range, named range, row, or formula area. |
| Current formula/value | The exact formula, value, type, or observed state. |
| Issue | What is wrong or cannot be verified. |
| Impact | Which outputs, decisions, or downstream formulas may be affected. |
| Priority | Critical, High, Medium, or Low, based on potential effect and propagation. |
| Recommended correction | A specific correction or the evidence needed to resolve the finding. |

Do not report a generic concern when a precise workbook location is available. Separate observed evidence from inference.

## Checklist statuses

For each applicable checklist item, use one of:

- **Pass** - verified from workbook evidence.
- **Fail** - contradicted by workbook evidence; cite the finding.
- **Not applicable** - the feature is outside this model's intended scope.
- **Not verifiable** - the workbook lacks the information needed; name the missing evidence.

Do not treat Not applicable or Not verifiable as a failure.

## Output

Provide:

1. a short scope statement confirming that the workbook was audited without modification;
2. findings ordered by priority;
3. a source and assumptions summary;
4. the applicable checklist with explicit statuses;
5. a concise conclusion stating whether the model is usable for its stated purpose and what must be corrected first.

If the user later asks to fix the workbook, confirm the authorized scope, create a backup, apply only the requested corrections, and rerun the affected checks.
