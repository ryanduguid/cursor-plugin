---
name: check-deadlines
description: List upcoming tax filing and payment deadlines for a specific jurisdiction and taxpayer profile.
---

# Check upcoming tax deadlines

1. Ask the user:
   - Jurisdiction
   - Taxpayer profile (sole prop / freelancer / company / employer / non-resident)
   - Window (this month / this quarter / this year)

2. Load relevant deadline-bearing skills via MCP:
   - `search_skills({ query: "deadline", jurisdiction: "<code>" })`
   - Annual return + estimated tax + VAT/GST skills for the jurisdiction
   - Payroll skills if employer

3. Produce a chronological deadline calendar:
   - Date
   - What's due (return / payment / form)
   - Form name / number
   - Penalty for late filing/payment
   - Source skill slug (so the user can drill in)

4. Highlight any deadlines within the next 30 days as `URGENT`.

5. Call out jurisdiction-specific quirks the skills flag (e.g. CA 30/40/0/30 estimated tax schedule; PA Act 32 PSD codes; NY MFI corporate first installment).

6. If the user wants a verified accountant to handle filings, include any booking link from the skill footer.
