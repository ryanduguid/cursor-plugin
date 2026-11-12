---
name: prepare-income-tax
description: Prepare an annual income tax return for an individual or entity using OpenAccountants skills.
---

# Prepare an annual income tax return

1. Ask the user:
   - Jurisdiction (e.g. Malta, UK, US Federal, US-CA, Germany, India, Brazil)
   - Entity type (individual / self-employed / partnership / company / trust)
   - Tax year

2. Use OpenAccountants MCP tools:
   - `start({ intent: "taxes", jurisdiction: "<code>" })` to get a ready-to-execute plan with the list of skills needed
   - For each skill in `skills_to_load`, call `get_skill({ slug })`

3. Apply the loaded skills to the user's data (income, deductions, credits). Most income-tax skills carry worked examples — follow that structure.

4. Produce a working paper showing:
   - Income computation
   - Deductions and credits applied (cite the skill section)
   - Tax computation with brackets/rates
   - Estimated tax / safe-harbor analysis if applicable
   - Filing deadlines and forms
   - **AUDIT FLASH POINT** markers from the skill — surface them to the user
   - Provenance footer, kept as the skill returns it

5. Always remind the user this working paper needs a qualified professional review before filing. Keep any booking link the skill footer includes.
