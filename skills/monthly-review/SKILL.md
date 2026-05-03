# Monthly Review Skill

Triggered when the user says "monthly review", "review [month]", "how did I do in [month]", "summarize [month]".

## Steps

1. **Identify target month.** Default to current month. Accept named months ("March") or YYYY-MM format.

2. **Read** `finances/ledger-YYYY-MM.md`, `finances/budgets.md`, `finances/goals.md`.

3. **Compute per-category totals** — net of any correction entries.

4. **Produce the review:**

```
## [Month Year] Review

### Income
- Total in: $X

### Spending
| Category       | Budget | Actual | Diff  | % Used |
|----------------|--------|--------|-------|--------|
| housing        | $1,500 | $1,500 |    $0 |  100%  |
| food-groceries |   $400 |   $312 |  +$88 |   78%  |
| food-dining    |   $150 |   $210 | -$60  |  140% ⚠ |

**Total spending:** $X
**Net (income − spending):** $X

### Highlights
[2–3 factual observations — highest category, biggest change from last month if data exists, etc.]

### Goals
- Japan trip: $1,200 / $5,000 (24%) — on track / behind pace
- Emergency fund: $4,300 / $10,000 (43%)

### Next month
[One optional prompt based on what the numbers show — only if a clear pattern exists]
```

5. **Offer to save** the review to `finances/review-YYYY-MM.md` and/or export to spreadsheet.

## Notes
- ⚠ marker for any category over 100% of budget
- If prior month data exists, add a "vs. last month" column to the spending table
- Keep highlights factual — no editorializing
