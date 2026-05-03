# Budget Setup Skill

Triggered on first session (when `finances/budgets.md` doesn't exist), or when the user says "set up my budgets", "redo my budget", or "start over".

## Purpose
Guide the user through setting their monthly income and per-category budget targets. Write the result to `finances/budgets.md`.

## Steps

1. **Check for existing budgets.** If `finances/budgets.md` exists, confirm the user wants to overwrite before proceeding.

2. **Ask for monthly take-home income.** This is after-tax income. Use it as the anchor for suggested budget percentages.

3. **Walk through categories one at a time.** For each major category, suggest a default based on common guidelines (see below), show the dollar amount at their income level, and let them accept, adjust, or skip.

   Suggested defaults (adjust to income):
   | Category | Default % of take-home |
   |---|---|
   | housing | 30% |
   | food-groceries | 10% |
   | food-dining | 5% |
   | transport | 10% |
   | health | 5% |
   | personal | 3% |
   | entertainment | 5% |
   | subscriptions | 3% |
   | savings | 20% |
   | other | 9% |

4. **Show a summary** of all entered budgets and the total. Flag if total exceeds income.

5. **Confirm and write** to `finances/budgets.md` using the standard format.

6. **Offer to set savings goals** as a follow-up: "Want to set up any savings goals now?"

## Notes
- Don't push the user toward any particular allocation — the percentages are suggestions, not rules
- If total budgeted > income, note the gap and ask how they'd like to adjust — don't refuse to save
- If they skip a category, omit it from the file; it can be added later
