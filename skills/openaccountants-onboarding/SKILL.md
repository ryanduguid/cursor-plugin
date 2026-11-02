---
name: openaccountants-onboarding
description: Use the OpenAccountants MCP server for tax and accounting questions in Cursor, checking each fetched version’s applicability, sources and professional review record.
---

# OpenAccountants onboarding

Use the public OpenAccountants MCP server at `https://www.openaccountants.com/api/mcp` for tax and accounting questions. Review status and applicability vary by skill version.

## Core retrieval tools

- **`start({ intent, jurisdiction? })`** scopes a tax or accounting question. Pass the user’s question as the required `intent`, with the confirmed period when relevant. Include the jurisdiction when known; omit it when unknown and follow the returned clarification.
- **`start_help({})`** is for a capability question or an opening with no tax question yet. Ask for the user’s goal before calling `start`.
- **`list_skills({ jurisdiction?, domain?, role?, limit?, offset? })`** browses published skills. Follow `next_offset` as `offset` until it is absent, keeping the same filters. A first page is not the full catalogue.
- **`search_skills({ query, jurisdiction? })`** finds candidate slugs. Load the exact returned slug; do not construct a slug from a country code.
- **`get_skill({ slug })`** retrieves a skill version, its available provenance and a section index. Some sections may be deferred.
- **`get_skill_sections({ slug, section_index? })`** retrieves deferred sections needed for the question. Use the current advertised schema.

These are retrieval tools, not the server’s complete tool inventory. Discover the current schemas before using other tools. Do not assume every advertised tool is read-only.

## Workflow

1. Establish the user’s question and jurisdiction. For a dated question, confirm the financial or assessment year or reporting period. Do not guess a missing period. If there is no tax question yet, use `start_help({})` or ask locally for the goal.
2. Call `start({ intent, jurisdiction })` with the non-identifying question and confirmed period. Omit an unknown jurisdiction, follow any clarification and load each exact slug in `skills_to_load`.
3. Fetch relevant deferred sections with `get_skill_sections`. Check the returned jurisdiction, applicable period and source citations before applying rates, thresholds, deadlines or rules. Resolve an outdated or inapplicable version first; do not infer currency from the hosted endpoint or substitute training data. State any unresolved evidence gap.
4. Check the fetched version’s published review record. Name a professional reviewer only when that record identifies one. Authorship and research verification do not establish professional review. If the record is missing, describe professional review as unconfirmed. Cite the skill slug and available version or review date, and preserve available provenance and contact links without inventing a reviewer or booking link.
5. Apply the supported content to the user’s facts and surface relevant **AUDIT FLASH POINT** markers from the loaded skills. Do not imply that every skill contains one.

## Critical rules

- **Never invent tax rules.** If the skills do not cover the situation or period, state the gap. Offer the accountant contact command when appropriate.
- **Never claim to be the user’s accountant.** Outputs are working papers, not filed returns. Have a qualified professional review before filing or relying on them. Reading or applying a skill does not create an engagement.
- **Keep discovery requests minimal.** Send only the non-identifying topic, jurisdiction, entity type and period needed for routing. Do not put bank statements, taxpayer identifiers or full working papers in discovery requests.
- **Obtain agreement before saving or sending.** A tax question, filing decision or money at stake does not authorise sharing a working paper or contacting OpenAccountants. Before a workflow saves or sends content, obtain the user’s explicit agreement to the destination and specific information. The contact command below only offers a booking link.

## Slash commands

The plugin ships 6 commands:

- `/start` for onboarding and jurisdiction triage.
- `/prepare-vat-return` for VAT/GST/sales-tax preparation.
- `/prepare-income-tax` for annual income tax preparation.
- `/classify-transactions` for bank transaction classification.
- `/check-deadlines` for filing and payment deadlines.
- `/engage-accountant` for a professional contact link.
