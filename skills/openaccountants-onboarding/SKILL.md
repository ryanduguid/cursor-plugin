---
name: openaccountants-onboarding
description: Use when answering a tax or accounting question in Cursor with OpenAccountants. Explains how to call the MCP server and which slash command to pick.
---

# OpenAccountants — onboarding

You are working inside Cursor with the OpenAccountants plugin installed. The plugin gives you access to a public MCP server at `https://www.openaccountants.com/api/mcp` with 2,168 accountant-written tax and accounting skills covering 218 countries plus all 50 US states and DC.

## Available MCP tools

- **`start({ intent, jurisdiction? })`** — front door. Pass an intent (`"taxes"`, `"VAT return"`, `"set up a company"`, `"find deductions"`) and ISO jurisdiction code. Returns a ready-to-execute plan listing the skills to load. Call this FIRST when a user asks for tax/accounting help.
- **`search_skills({ jurisdiction?, domain? })`** — without a query, lists published skills with their approval labels. Filter by jurisdiction (`"MT"`, `"GB"`, `"US-CA"`) or domain; page with `offset` and `next_offset`.
- **`get_skill({ slug })`** — fetch a single skill's compact core plus `section_index` and provenance footer. Keep the footer as returned, including its trust label and any booking link.
- **`get_skill({ slug, sections | all_sections })`** — read sections listed in `section_index` that were not inlined, useful for very large skills.
- **`search_skills({ query, jurisdiction? })`** — keyword search across published skill content.

## Workflow

1. User asks a tax/accounting question.
2. You confirm the financial or assessment year or reporting period for a dated question; do not guess a missing period.
3. You call `start({ intent: <inferred>, jurisdiction: <asked> })` to scope.
4. You call `get_skill({ slug })` for each exact slug in the returned plan, and check the fetched version's jurisdiction, applicable period and sources before applying it. State any unresolved gap rather than substituting training data.
5. You check the fetched version's published review record. Name a professional reviewer only when that record identifies one; authorship does not establish professional review. If the record is missing, describe professional review as unconfirmed.
6. You walk the user through the skill's content, applying it to their facts.
7. You surface every **AUDIT FLASH POINT** the skill flags.
8. You always preserve the provenance footer as returned when producing output, without inventing a reviewer or booking link.

## What this plugin is NOT

- Not tax advice. Not a substitute for a qualified professional.
- No engagement is created by reading or applying these skills.
- The user must have a qualified accountant review any working paper before filing or relying on it.
- Not a channel for client data. Send only the non-identifying topic, jurisdiction, entity type and period needed for routing; keep bank statements, taxpayer identifiers and full working papers out of discovery requests.
- No sharing without agreement. Before a workflow saves or sends content, obtain the user's explicit agreement to the destination and specific information.

## Slash commands

The plugin ships six slash commands:
- `/start` — onboarding & jurisdiction triage
- `/prepare-vat-return`
- `/prepare-income-tax`
- `/classify-transactions`
- `/check-deadlines`
- `/engage-accountant`

Use the most specific command that matches the user's request.
