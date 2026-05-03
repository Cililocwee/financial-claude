# Export Spreadsheet Skill

Triggered when the user says "export", "give me a spreadsheet", "download my data", "Excel file", "CSV".

## Scope options
Ask the user which period to export if not specified:
- Current month (default)
- Specific month
- Date range
- All time (all ledger files)

## Format detection

Before generating, check for openpyxl:
```bash
python3 -c "import openpyxl; print('ok')" 2>/dev/null
```
- If `ok`: offer xlsx (multi-sheet) or CSV
- If fails: proceed with CSV, tell the user xlsx isn't available and how to enable it (`pip3 install openpyxl`)

## CSV export

Write a single CSV to `finances/exports/transactions-YYYY-MM-DDThhmm.csv`:
```
Date,Description,Category,Amount,Notes
2026-04-01,Rent,housing,-1500.00,
2026-04-03,Whole Foods,food-groceries,-68.42,
```
Exclude `[CORRECTION]` entries from the export (show net amounts per transaction instead).

## XLSX export (multi-sheet)

Generate a Python script, run it, clean it up. Sheets:

**Sheet 1: Transactions**
All transactions for the period (net of corrections). Columns: Date, Description, Category, Amount, Notes. Auto-width columns.

**Sheet 2: Budget vs Actual**
Per-category comparison: Category | Budget | Actual | Difference | % Used. Conditional formatting: red fill if >100%, yellow if 80–100%.

**Sheet 3: Goals**
Goal name | Target | Saved | Remaining | % Complete | Deadline | On Track?

**Sheet 4: Monthly Summary**
One row per available month: Month | Total Income | Total Spending | Net | Top Category.

Save to `finances/exports/finance-YYYY-MM-DDThhmm.xlsx`.

## After export
Confirm the file path and size. Offer to open the containing folder if on desktop.

## Python script template
```python
import openpyxl
from openpyxl.styles import PatternFill, Font
from openpyxl.utils import get_column_letter

wb = openpyxl.Workbook()
# ... build sheets ...
wb.save('finances/exports/finance-[timestamp].xlsx')
```
Write to a temp file like `/tmp/finance_export.py`, run with `python3`, then `rm` it.
