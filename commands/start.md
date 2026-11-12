---
name: start
description: Onboarding for OpenAccountants — figure out which jurisdiction and tax workflow applies to the user.
---

# Start an OpenAccountants tax workflow

Use the `start` tool from the OpenAccountants MCP server to figure out which jurisdiction and intent applies.

1. Call `start()` with no arguments to see what's needed.
2. Ask the user for their jurisdiction (ISO 2-letter code, e.g. `MT`, `GB`, `US-CA`) and their intent (`taxes`, `VAT return`, `set up a company`, `find deductions`, etc.).
3. Call `start({ intent, jurisdiction })` to get a ready-to-execute plan listing the skills to load.
4. For each skill in `skills_to_load`, call `get_skill({ slug })` to fetch the full markdown.
5. Walk the user through the workflow described in the loaded skills.

If the user is non-technical, prefer the more specific commands instead:
- `/prepare-vat-return` — VAT/GST/sales-tax return
- `/prepare-income-tax` — annual income tax return
- `/classify-transactions` — bank-statement classification
- `/check-deadlines` — what's due this quarter
- `/engage-accountant` — book a verified accountant
