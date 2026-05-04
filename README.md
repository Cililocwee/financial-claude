# Financial Claude

A personal finance tracking companion built on Claude Code. Log transactions, manage budgets, track savings goals, and export spreadsheets — all through natural conversation, with data stored locally in plain markdown.

## How it works

Tell the agent what you spent or earned in plain language. It categorizes transactions, appends them to a local ledger, and tracks everything against your monthly budget.

```
"I spent $42 on groceries"
"coffee $12, gas $55, haircut $40"
"Got paid $3,200"
```

No bank connections, no external APIs, no account numbers. Your data stays in local files you own.

## Features

- **Transaction logging** — natural language input, batch entry, auto-categorization
- **Budget tracking** — monthly targets per category with over-budget warnings
- **Savings goals** — named goals with deadlines and pace tracking
- **Bank CSV import** — pull in exports from your bank and auto-map columns
- **Spreadsheet export** — CSV always available, multi-sheet .xlsx with openpyxl
- **Spending trends** — monthly averages, year-to-date totals, month-over-month changes

## Getting started

1. Open this project in Claude Code
2. Say **"Set up my budgets"** — the agent walks you through monthly targets
3. Add any savings goals: *"I'm saving $5,000 for Japan by December"*
4. Start logging transactions

## Data storage

All data lives in a `finances/` directory created on first use:

```
finances/
  ledger-YYYY-MM.md       # monthly transaction log (append-only)
  budgets.md              # monthly budget targets per category
  goals.md                # savings goals and progress
  exports/                # generated CSV and Excel files
```

Transaction history is never deleted — corrections are added as new entries.

## Skills

| Skill | Trigger |
|---|---|
| `budget-setup` | "Set up my budgets" / first session |
| `monthly-review` | "Monthly review" / "How did I do in April?" |
| `export-spreadsheet` | "Export this month to a spreadsheet" |
| `import-csv` | "I have a CSV from my bank" |
| `spending-trends` | "Show me spending trends" / "Year to date" |

## Spreadsheet export

Exported .xlsx files include four sheets:
- **Transactions** — full ledger for the selected period
- **Budget vs Actual** — category comparison
- **Goals** — savings progress
- **Monthly Summary** — one row per month, YTD view

Requires Python 3 and `openpyxl` for .xlsx output. Falls back to CSV automatically if unavailable.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- Python 3 + `openpyxl` (optional, for .xlsx export)
