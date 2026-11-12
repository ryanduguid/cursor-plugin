---
name: prepare-vat-return
description: Prepare a VAT, GST, or sales-tax return for a specific jurisdiction using OpenAccountants skills.
---

# Prepare a VAT / GST / sales-tax return

1. Ask the user which jurisdiction (e.g. Malta, UK, Germany, Italy, India GST, US-CA sales tax) and which period (e.g. `Q1 2025`, `January 2025`).

2. Use the OpenAccountants MCP tools to load the right skill:
   - `search_skills({ query: "VAT return", jurisdiction: "<ISO code>" })` to find the right slug
   - `get_skill({ slug: "<chosen slug>" })` to load the full skill content
   - For EU jurisdictions, also load `eu-vat-directive` and `vat-workflow-base`

3. Apply the loaded skill's classification rules to the user's transactions or invoices.

4. Produce a working paper showing:
   - Each transaction classified by VAT box / code
   - Box totals
   - Reconciliation against gross receipts
   - Deadlines and filing mechanics for the jurisdiction
   - Provenance footer, kept as the skill returns it

5. Remind the user this working paper needs a qualified professional review before filing. Keep any booking link the skill footer includes.

**Out of scope** by default: cross-border OSS/IOSS (load the cross-border skills), margin schemes, partial exemption, VAT groups, capital goods scheme — unless the skill explicitly covers them.
