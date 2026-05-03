# Spending Trends Skill

Triggered when the user says "trends", "year to date", "compare months", "averages", "how does this month compare", "am I spending more than usual".

## Purpose
Aggregate data across all available monthly ledger files to show patterns, averages, and anomalies.

## Steps

### 1. Discover available data
Glob all `finances/ledger-YYYY-MM.md` files. Parse each one. Compute per-category totals per month.

### 2. Determine scope
Default: all available months. Accept scoping: "last 6 months", "this year", "2025".

### 3. Produce the trends report

**Year-to-date totals (or period totals):**
```
## Spending Summary: Jan–Apr 2026

| Category       | Jan    | Feb    | Mar    | Apr    | Avg/mo | YTD    |
|----------------|--------|--------|--------|--------|--------|--------|
| housing        | $1,500 | $1,500 | $1,500 | $1,500 | $1,500 | $6,000 |
| food-groceries |  $380  |  $410  |  $295  |  $312  |  $349  | $1,397 |
| food-dining    |  $120  |  $185  |  $210  |  $210  |  $181  |  $725  |
```

**Month-over-month change (current vs. prior average):**
```
## This Month vs. Your Average

 food-dining: $210 vs. avg $138 (+52%) ↑
 transport:    $95 vs. avg $190 (-50%) ↓  ← unusually low
```

**Biggest movers:**
Top 3 categories with the largest absolute change vs. prior month.

**Income trend:**
Monthly income over the period, average, and any months where spending exceeded income.

**Savings rate:**
Average % of income saved per month over the period.

### 4. Offer follow-ups
- "Export this as a spreadsheet?"
- "Want to see a drill-down on any category?"
- "Run the monthly review for a specific month?"

## Notes
- If only one month of data exists, say so and offer to start building history
- Exclude `[CORRECTION]` entries from totals
- Flag months where total spending exceeded income with a note — no lecture, just a fact
