---
name: engage-accountant
description: Connect the user with a verified accountant in their jurisdiction for review or formal engagement.
---

# Engage a verified accountant

OpenAccountants provides tax and accounting skills and AI tooling. For anything that requires liability, sign-off, or formal advice, the user needs a human accountant.

1. Ask the user the jurisdiction(s) involved and a one-line summary of what they need (return review, tax planning, formation, payroll setup, etc.).

2. List accountants for that jurisdiction when any are published:
   - Open `https://www.openaccountants.com/network` and surface the listings
   - Or call `list_verifiers({ jurisdiction: "<code>" })`

3. Hand off to the booking flow:
   - The central Calendly link is `https://calendly.com/openaccountants-info/30min`
   - The booking team routes the user to the right named verifier
   - First call is free, 30 minutes, no obligation, no liability until both sides sign an engagement letter

4. Tell the user clearly:
   - This skill / chat does not create a client–accountant relationship
   - No liability attaches to anyone until you and the chosen accountant sign a formal engagement
   - The verified accountants list at `/network` is the source of truth for who's licensed in which jurisdiction
