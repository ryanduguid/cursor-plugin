---
name: openaccountants-onboarding
description: Use when answering a tax or accounting question in Cursor with OpenAccountants. Explains how to call the MCP server and which slash command to pick.
---

# OpenAccountants — onboarding

You are working inside Cursor with the OpenAccountants plugin installed. The plugin gives you access to a public MCP server at `https://www.openaccountants.com/api/mcp` with 2,168 accountant-written tax and accounting skills covering 218 countries plus all 50 US states and DC.

## Available MCP tools

- **`start({ intent?, jurisdiction? })`** — front door. Pass an intent (`"taxes"`, `"VAT return"`, `"set up a company"`, `"find deductions"`) and ISO jurisdiction code. Returns a ready-to-execute plan listing the skills to load. Call this FIRST when a user asks for tax/accounting help.
- **`list_skills({ jurisdiction?, category? })`** — list published skills. Filter by jurisdiction (`"MT"`, `"GB"`, `"US-CA"`) or category.
- **`get_skill({ slug })`** — fetch a single skill's full markdown and provenance footer. Keep the footer as returned, including its trust label and any booking link.
- **`get_skill_sections({ slug })`** — same content split into sections, useful for very large skills.
- **`search_skills({ query, jurisdiction? })`** — keyword search across published skill content.

## Workflow

1. User asks a tax/accounting question.
2. You call `start({ intent: <inferred>, jurisdiction: <asked> })` to scope.
3. You call `get_skill({ slug })` for each skill in the returned plan.
4. You walk the user through the skill's content, applying it to their facts.
5. You surface every **AUDIT FLASH POINT** the skill flags.
6. You always preserve the provenance footer as returned when producing output.

## What this plugin is NOT

- Not tax advice. Not a substitute for a qualified professional.
- No engagement is created by reading or applying these skills.
- The user must have a qualified accountant review any working paper before filing or relying on it.

## Slash commands

The plugin ships six slash commands:
- `/start` — onboarding & jurisdiction triage
- `/prepare-vat-return`
- `/prepare-income-tax`
- `/classify-transactions`
- `/check-deadlines`
- `/engage-accountant`

Use the most specific command that matches the user's request.
