---
name: start
description: Onboarding for OpenAccountants — figure out which jurisdiction and tax workflow applies to the user.
---

# Start an OpenAccountants tax workflow

Use the `start` tool from the OpenAccountants MCP server to figure out which jurisdiction and intent applies.

1. If there is no tax or accounting question yet, call `start({ intent: "" })` to see the topics and jurisdictions covered, or ask the user what they want.
2. Ask the user for their jurisdiction (ISO 2-letter code, e.g. `MT`, `GB`, `US-CA`) and their question. For a dated question, confirm the financial or assessment year or reporting period; do not guess a missing period.
3. Call `start({ intent, jurisdiction })` with the question and confirmed period to get a plan listing the skills to load. Omit an unknown jurisdiction and follow the returned clarification.
4. For each exact slug in `skills_to_load`, call `get_skill({ slug })`. Check the fetched version's jurisdiction, applicable period and sources before applying it, and fetch any sections the question needs that `get_skill` did not inline.
5. Walk the user through the workflow described in the loaded skills. Cite each skill slug and its available version or review date. Attribute authorship and professional review separately, naming a reviewer only when the version's published review record identifies one. Preserve available provenance and contact links; do not invent a reviewer or booking link.

Use only non-identifying scope in MCP discovery requests. These steps do not authorise saving or sending the user's records or contacting OpenAccountants.

If the user is non-technical, prefer the more specific commands instead:
- `/prepare-vat-return` — VAT/GST/sales-tax return
- `/prepare-income-tax` — annual income tax return
- `/classify-transactions` — bank-statement classification
- `/check-deadlines` — what's due this quarter
- `/engage-accountant` — book a verified accountant
