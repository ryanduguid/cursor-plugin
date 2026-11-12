---
name: classify-transactions
description: Classify bank statement transactions into accounting categories using jurisdiction-specific rules from OpenAccountants skills.
---

# Classify bank transactions

1. Ask the user for:
   - The bank statement or transaction list (CSV, PDF, or pasted text)
   - The jurisdiction (so we use the right chart of accounts + tax treatment)
   - The purpose: bookkeeping, VAT return, income tax prep, or all

2. Load the relevant skills via MCP:
   - For VAT classification: `get_skill({ slug: "<jurisdiction>-vat-return" })`
   - For bookkeeping: `search_skills({ query: "bookkeeping", jurisdiction: "<code>" })`
   - For income-tax classification: the relevant income-tax skill

3. For each transaction, output a row:
   - Date, description, amount
   - Category (using the jurisdiction's standard chart of accounts)
   - VAT code / box (if applicable)
   - Tax treatment (deductible / non-deductible / partial / reverse charge / etc.)
   - Confidence flag: classified-with-rules / uncertain / requires-human-review

4. Surface any **AUDIT FLASH POINT** items from the loaded skills.

5. Conclude with a summary table and recommend a qualified professional review the classification before it is used for filing. Include any booking link the skill footer includes.
