# Requirements

## Core function
Conversational personal finance tracker. Local markdown storage. No external integrations. Five discrete skills covering setup, review, export, import, and trend analysis.

## Transaction logging
- Natural-language input, including batch entry
- Category inference from description; prompt only when ambiguous
- Date defaults to today; accepts explicit dates and relative dates ("yesterday", "last Friday")
- Append-only ledger format
- Confirm each log with running category total

## Budget tracking
- Monthly targets per category stored in `finances/budgets.md`
- On-demand comparison: budgeted vs. actual with over/under and % used
- Flag categories >80% spent with a visual indicator
- Budget changes take effect next month by default (current month stays as-is)

## Goals
- Named savings goals with target amount and optional deadline
- Track contributions via tagged savings transactions
- Show projected completion date based on current monthly savings rate
- Warn when user is off-pace to hit a deadline

## Spreadsheet export (export-spreadsheet skill)
- Output: CSV (always) or .xlsx (if openpyxl available)
- Scope: single month, date range, or all-time
- Multi-sheet xlsx: Transactions, Budget vs Actual, Goals, Monthly Summary
- Saved to `finances/exports/` with timestamped filename

## Bank CSV import (import-csv skill)
- Read user-provided CSV file
- Detect or ask for column mapping (date, description, amount, optional category)
- Preview first 5 rows before committing
- Auto-categorize using description matching; flag unknowns for user review
- Handle both "single amount column" and "debit/credit column" formats
- Append to the correct monthly ledger file(s)

## Spending trends (spending-trends skill)
- Read all available monthly ledger files
- Compute per-category monthly averages
- Show month-over-month change for the current month vs. prior average
- Year-to-date totals by category
- Highest-spend month per category

## First-time setup (budget-setup skill)
- Prompt for monthly take-home income
- Walk through major categories one at a time, suggest a default based on income %
- Write completed budgets to `finances/budgets.md`
- Optionally seed initial savings goals
