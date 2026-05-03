# Import CSV Skill

Triggered when the user says "import", "I have a bank export", "load transactions from a file", or provides a file path ending in `.csv`.

## Purpose
Read a bank-exported CSV, map columns to the ledger format, auto-categorize what's possible, prompt for the rest, then append to the appropriate monthly ledger file(s).

## Steps

### 1. Get the file path
Ask for the full path to the CSV file if not provided. Read it with the Read tool.

### 2. Detect format
Read the first 2 rows to identify columns. Common bank CSV formats:
- **Single amount column:** Date, Description, Amount (negative = expense)
- **Debit/credit columns:** Date, Description, Debit, Credit
- **Amount with sign column:** Date, Description, Amount, Type ("DR"/"CR")

Show the user the detected column mapping and ask them to confirm or correct it.

### 3. Preview
Show the first 5 transactions in ledger format so the user can verify the mapping looks right before any data is written.

### 4. Auto-categorize
For each transaction description, attempt to match against known category keywords (see `.claude/rules/categories.md`). Build a list:
- Confidently categorized: show count
- Ambiguous (need user input): show list, one at a time, with suggested category

### 5. Confirm before writing
Show a final summary:
```
Ready to import:
  47 transactions across 2 months (March–April 2026)
  42 auto-categorized, 5 need your input
  Appending to: finances/ledger-2026-03.md, finances/ledger-2026-04.md

Proceed? (yes/no)
```

### 6. Append to ledger(s)
Group transactions by month. For each month:
- Check if `finances/ledger-YYYY-MM.md` exists; create with header if not
- Append all transactions for that month
- If the month already has entries, warn the user about potential duplicates

### 7. Confirm
Report: X transactions imported across Y months. Offer to run the monthly review for any affected month.

## Duplicate detection
Before appending, check if a transaction with the same date, description, and amount already exists in the ledger. Flag potential duplicates and ask before adding them.

## Notes
- Amount sign convention: expenses negative, income positive — normalize during import
- Strip bank-specific prefixes from descriptions (e.g., "POS PURCHASE", "ACH DEBIT") to make them readable
- Never modify the source CSV file
