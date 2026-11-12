---
name: prepare-income-tax
description: Prepare an annual income tax return for an individual or entity using OpenAccountants skills.
---

# Prepare an annual income tax return

1. Ask the user:
   - Jurisdiction (e.g. Malta, UK, US Federal, US-CA, Germany, India, Brazil)
   - Entity type (individual / self-employed / partnership / company / trust)
   - Tax year (do not guess a missing year)

2. Use OpenAccountants MCP tools:
   - `start({ intent: "Prepare the <entity type> income tax return for <confirmed tax year>", jurisdiction: "<code>" })` to get a plan with the list of skills needed
   - For each exact slug in `skills_to_load`, call `get_skill({ slug })`
   - Check the fetched version’s jurisdiction, applicable period and sources before applying it, and fetch any sections the question needs that `get_skill` did not inline.

3. Apply the loaded skills to the user's data (income, deductions, credits). Most income-tax skills carry worked examples — follow that structure.

4. Produce a working paper showing:
   - Income computation
   - Deductions and credits applied (cite the skill section)
   - Tax computation with brackets/rates
   - Estimated tax / safe-harbor analysis if applicable
   - Filing deadlines and forms
   - **AUDIT FLASH POINT** markers from the skill — surface them to the user
   - Provenance footer, kept as the skill returns it
   - Each skill slug and its available version or review date. Attribute authorship and professional review separately, naming a reviewer only when the version’s published review record identifies one.

5. Always remind the user this working paper needs a qualified professional review before filing. Keep any booking link the skill footer includes; do not invent a reviewer or booking link.

Use only non-identifying scope in MCP discovery requests. These steps do not authorise saving or sending the user’s records or contacting OpenAccountants.
