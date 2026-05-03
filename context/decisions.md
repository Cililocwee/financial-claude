# Design Decisions

## Plain markdown as source of truth
All transaction data is stored as human-readable markdown tables. JSON/CSV/SQLite would be more queryable but less portable and less editable by hand. For personal use, owning your data matters more than query performance.

## CSV and xlsx as export formats only
The ledger is markdown; spreadsheets are outputs. This separation means the user can always recover from a corrupt export by re-running the export skill — the source data is untouched.

## openpyxl for xlsx generation
Chosen over xlsxwriter and xlwt because it handles both reading and writing, is well-maintained, and is the most common Python xlsx library. If unavailable, CSV is a complete fallback that opens in any spreadsheet app.

## Append-only ledger with correction entries
Audit trail over convenience. A user who discovers a wrong entry 3 months later needs to see what happened, not a sanitized history.

## Monthly files over single ledger
One file per month keeps file size manageable, makes archiving natural, and makes it easy to scope operations to a specific period.

## No bank API integration
Deliberate. Integrations add auth complexity, third-party data exposure, and maintenance surface. Manual entry and CSV import cover 95% of the use case without any of the risk.

## Five skills over a flat prompt interface
Named skills make the agent's capabilities discoverable and keep each interaction focused. A user who says "export" shouldn't have to explain what format they want every time.

## Assumptions made during generation
- Single user, personal finances
- Python likely available in the user's environment (common in dev setups)
- User comfortable with CLI/Claude Code workflow
- Prefers owning local data over cloud sync
