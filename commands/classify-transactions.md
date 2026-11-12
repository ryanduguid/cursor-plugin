---
name: classify-transactions
description: Classify bank statement transactions into accounting categories using jurisdiction-specific rules from OpenAccountants skills.
---

# Classify bank transactions

1. Ask the user for:
   - The bank statement or transaction list (CSV, PDF, or pasted text)
   - The jurisdiction (so we use the right chart of accounts + tax treatment)
   - The reporting period
   - The purpose: bookkeeping, VAT return, income tax prep, or all

2. Load the relevant skills via MCP:
   - Call `start({ intent: "Classify transactions for <purpose> for <confirmed period>", jurisdiction: "<code>" })` and load each exact slug in `skills_to_load` with `get_skill({ slug })`
   - For further discovery: `search_skills({ query: "bookkeeping", jurisdiction: "<code>" })`, then load the exact returned slugs. Do not construct a slug from the country code.
   - Check the fetched version’s jurisdiction, applicable period and sources before applying it.

3. For each transaction, output a row:
   - Date, description, amount
   - Category (using the jurisdiction's standard chart of accounts)
   - VAT code / box (if applicable)
   - Tax treatment (deductible / non-deductible / partial / reverse charge / etc.)
   - Confidence flag: classified-with-rules / uncertain / requires-human-review

4. Surface any **AUDIT FLASH POINT** items from the loaded skills.

5. Conclude with a summary table and recommend a qualified professional review the classification before it is used for filing. Cite each skill slug and its available version or review date. Attribute authorship and professional review separately, naming a reviewer only when the version’s published review record identifies one. Include any booking link the skill footer includes; do not invent a reviewer or booking link.

Keep bank statements and identifiers out of MCP discovery requests. These steps do not authorise saving or sending the user’s records or contacting OpenAccountants.
