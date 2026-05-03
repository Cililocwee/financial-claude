# Personal Finance Companion — User Guide

## Quick-start phrases

| What you want | Say something like |
|---|---|
| Log an expense | "I spent $42 on groceries" |
| Log multiple at once | "coffee $12, gas $55, haircut $40" |
| Log income | "Got paid $3,200" / "freelance invoice, $800" |
| Check the month | "How am I doing this month?" |
| Category drill-down | "How much have I spent on restaurants?" |
| Fix a mistake | "That $42 was household supplies, not groceries" |
| Set budgets | "Set up my budgets" |
| Add a goal | "I want to save $5,000 for Japan by December" |
| Monthly review | "Monthly review" / "Summarize March" |
| Export data | "Export this month to a spreadsheet" |
| Import bank data | "I have a CSV from my bank" |
| Trends | "Show me spending trends" / "Year to date" |

## Your data files

```
finances/
  ledger-YYYY-MM.md     transaction history (never deleted)
  budgets.md            your monthly targets
  goals.md              savings goals
  exports/              CSV and Excel files you've generated
```

You own these files — edit them directly for bulk changes.

## First session checklist

1. Say **"Set up my budgets"** — the agent will walk you through it
2. Add any active savings goals: "I'm saving for X, goal is $Y by [date]"
3. Start logging transactions

## Spreadsheet export

The exported spreadsheet includes:
- **Transactions** tab: full ledger for the selected period
- **Budget vs Actual** tab: category comparison
- **Goals** tab: savings progress
- **Monthly Summary** tab: one row per month, YTD view

Requires Python + `openpyxl` for .xlsx. Falls back to CSV automatically.

## Importing from your bank

Most banks let you export transactions as CSV. The import skill will:
1. Read your file
2. Show you a preview and ask you to confirm column mapping
3. Auto-categorize what it can, ask about the rest
4. Append everything to the ledger

## Tips

- Approximate is better than nothing — log your best guess
- The agent won't lecture you about your spending choices
- Corrections are added as new rows, never edits — your history is safe
