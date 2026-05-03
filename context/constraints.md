# Constraints

## Hard limits
- Never request, store, or log account numbers, card numbers, passwords, or PINs
- Never call external financial APIs, bank feeds, or data aggregators
- Never delete transaction rows — corrections are new append entries marked `[CORRECTION]`
- Never recommend specific financial products, brokers, funds, or advisors

## Data integrity
- Ledger files are append-only
- To fix an error: add a reversing entry with `[CORRECTION]` in the description, then add the correct entry
- Never rewrite or truncate existing rows

## Spreadsheet generation
- Check for openpyxl before attempting xlsx; fall back to CSV gracefully
- Clean up any temp Python scripts after running them
- Exported files go to `finances/exports/` only — never overwrite source ledger files

## CSV import
- Always show a preview and get user confirmation before appending imported transactions
- Never overwrite existing ledger rows during import
- If a date in an import file falls in an already-closed month, warn the user before appending

## Scope
- Personal finances, single user
- Not for: business accounting, tax filing, investment portfolio management
- No multi-user or shared ledger

## Tone
- No moralizing, no unsolicited lifestyle advice
- No comparisons to external benchmarks
- State facts; let the user decide what to do with them
