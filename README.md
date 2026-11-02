# OpenAccountants — Cursor plugin

Connect Cursor to OpenAccountants tax skills via MCP for VAT/GST, income tax, payroll, formation and cross-border questions.

Skills include accountant-reviewed versions and source-cited drafts. Check the [current catalogue](https://www.openaccountants.com/skills) and [review method](https://www.openaccountants.com/review-method) for each skill's review status, reviewer, version and review date. Authorship or a jurisdiction lead's name does not establish professional review of every skill version.

## What this plugin does

Connects Cursor to the public OpenAccountants MCP server at `https://www.openaccountants.com/api/mcp` and registers six slash commands:

| Command | What it does |
|---|---|
| `/start` | Onboarding — figures out which jurisdiction and workflow applies |
| `/prepare-vat-return` | Guided VAT/GST/sales-tax return preparation |
| `/prepare-income-tax` | Annual income tax return for any jurisdiction |
| `/classify-transactions` | Bank-statement → P&L classification by jurisdiction |
| `/check-deadlines` | Upcoming filing & payment deadlines |
| `/engage-accountant` | Hand off to a verified accountant for human review |

Under the hood, every command calls the same MCP server. Skill source is available in [openaccountants/openaccountants](https://github.com/openaccountants/openaccountants); see its [licensing document](https://github.com/openaccountants/openaccountants/blob/main/LICENSING.md) for content terms.

## Install

If OpenAccountants is listed in your Cursor plugin marketplace, install it there to load the commands, onboarding skill and MCP connection. Marketplace availability has not been established by this repository.

To configure only the MCP connection, add this entry to your project’s `.cursor/mcp.json`, preserving other server entries:

```json
{
  "mcpServers": {
    "openaccountants": {
      "url": "https://www.openaccountants.com/api/mcp"
    }
  }
}
```

This manual MCP configuration connects the tools; it does not install the plugin’s command or skill files. Use the current advertised schemas. `start` requires an intent; for an opening with no tax question, use `start_help({})`. Send only non-identifying discovery scope and obtain explicit agreement to the destination and specific information before any workflow saves or sends content. See the [privacy policy](https://www.openaccountants.com/privacy).

## Jurisdictions covered

Every UN member state has at least foundational coverage. Deep packs exist for:

- **Europe**: Malta, UK, Germany, Italy, France, Spain, Portugal, Ireland, Netherlands
- **North America**: US federal + 24 deep state packs (CA, NY, TX, FL, IL, OH, PA, MA, NJ, NC, MI, OR, WA, NH, DE, VA, GA, AZ, CO, NV, MN, MO, MD, …); Canada federal + provincial
- **Asia**: India, Indonesia, China (in 简体中文), Pakistan, Singapore, Japan
- **Latin America**: Brazil (in PT-BR), Mexico, Argentina, Chile
- **Africa**: South Africa, Nigeria, Kenya, Egypt
- **Middle East**: Saudi Arabia, UAE, Israel

Plus cross-border matrices (PTE elections, sales-tax nexus, bonus depreciation conformity, 1099-K thresholds, FATCA/FBAR, GILTI/FDII/BEAT, etc.).

## Important

These skills produce **working papers, not filed returns**. Check each fetched version’s jurisdiction, applicable period, sources and published review record before using it, and retrieve relevant deferred sections. Preserve available provenance and contact links; do not invent a reviewer or booking link. Reading or applying skills does not create an engagement. Have a qualified professional review before filing or relying on a working paper.

## Licence

MIT for this plugin wrapper. Skill content has separate terms from this wrapper. The source repository's [licensing document](https://github.com/openaccountants/openaccountants/blob/main/LICENSING.md) describes the source-available Open Accountants Skills License, commercial options, third-party copyleft exceptions and prior AGPL releases. Check the terms for the skill version you use.

## Links

- Website: [openaccountants.com](https://www.openaccountants.com)
- Skills source: [github.com/openaccountants/openaccountants](https://github.com/openaccountants/openaccountants)
- Verified accountant network: [openaccountants.com/network](https://www.openaccountants.com/network)
- Book a verified accountant: [calendly.com/openaccountants-info/30min](https://calendly.com/openaccountants-info/30min)
