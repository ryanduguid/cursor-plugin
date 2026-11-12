# OpenAccountants — Cursor plugin

**2,168 accountant-written tax and accounting skills** covering **218 countries plus all 50 US states and DC**, directly inside Cursor.

> Built for AI agents that need tax and accounting computation — VAT/GST, income tax, payroll, formation, cross-border, and more.

## What this plugin does

Connects Cursor to the public OpenAccountants MCP server at `https://www.openaccountants.com/api/mcp` and registers six slash commands:

| Command | What it does |
|---|---|
| `/start` | Onboarding — figures out which jurisdiction and workflow applies |
| `/prepare-vat-return` | Guided VAT/GST/sales-tax return preparation |
| `/prepare-income-tax` | Annual income tax return for a jurisdiction |
| `/classify-transactions` | Bank-statement → P&L classification by jurisdiction |
| `/check-deadlines` | Upcoming filing and payment deadlines |
| `/engage-accountant` | Hand off to a verified accountant for human review |

Every command calls that MCP server.

## Install

Search "OpenAccountants" in the Cursor plugin marketplace and click install. Cursor configures the MCP connection automatically.

For a manual install, add this to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "openaccountants": {
      "url": "https://www.openaccountants.com/api/mcp"
    }
  }
}
```

No API key or other secret is required. The server URL is public.

## Coverage

2,168 accountant-written tax and accounting skills covering 218 countries, plus all 50 US states and DC. Examples:

- **Europe**: Malta, UK, Germany, Italy, France, Spain, Portugal, Ireland, Netherlands
- **North America**: United States (federal, all 50 states, and DC); Canada
- **Asia**: India, Indonesia, China (in 简体中文), Pakistan, Singapore, Japan
- **Latin America**: Brazil (in PT-BR), Mexico, Argentina, Chile
- **Africa**: South Africa, Nigeria, Kenya, Egypt
- **Middle East**: Saudi Arabia, UAE, Israel

Cross-border topics include PTE elections, sales-tax nexus, bonus depreciation conformity, 1099-K thresholds, FATCA/FBAR, and GILTI/FDII/BEAT.

## Important

These skills produce working papers. A qualified professional should review a working paper before filing or relying on it. Reading or applying a skill does not create a client–accountant relationship. That requires a formal engagement letter signed by you and an accountant.

## License

This plugin is MIT-licensed. Skill content is served by the OpenAccountants MCP server under its own terms: [openaccountants.com](https://www.openaccountants.com).

## Links

- Website: [openaccountants.com](https://www.openaccountants.com)
- Verified accountant network: [openaccountants.com/network](https://www.openaccountants.com/network)
- Book a verified accountant: [calendly.com/openaccountants-info/30min](https://calendly.com/openaccountants-info/30min)
