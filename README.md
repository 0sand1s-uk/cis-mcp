# 0s and 1s CIS MCP server

Free calculators for the UK Construction Industry Scheme (CIS), as a remote MCP server and a JSON API. For contractors who pay subcontractors, and the bookkeepers who do it for them.

- MCP server: `https://0sand1s.co.uk/mcp` (Streamable HTTP, no sign-in)
- REST API: `https://0sand1s.co.uk/api/v1` ([OpenAPI](https://0sand1s.co.uk/api/v1/openapi.json))
- Docs: https://0sand1s.co.uk/developers

No key and no account. Nothing you send is stored. Up to 60 requests a minute from one address, the API and the MCP server together.

## Tools

| Tool | What it works out |
|---|---|
| `cis_deduction` | The CIS deduction on a payment: gross, VAT and materials in, deduction and net out, with the working |
| `cis_gross_up` | The gross to pay so the subcontractor receives a given net |
| `cis_tax_month` | The tax month a date falls in, the return due date (19th) and the electronic payment date (22nd, moved for weekends and bank holidays) |
| `cis_late_penalties` | What a late CIS300 or nil return costs, stage by stage |
| `cis_gross_payment_turnover_test` | Whether a business meets the turnover test for gross payment status |
| `cis_needs_verification` | Whether a subcontractor must be verified with HMRC before a payment |
| `cis_nil_return_check` | Whether a nil return is due for a tax month |

Money goes in as pounds (`"1,200.00"`) and comes back as pence and pounds. Dates are `YYYY-MM-DD`. Every answer lists the GOV.UK and legislation.gov.uk pages it follows. Answers follow the published rules; they are not tax advice and do not come from HMRC.

## Connect

**Claude** (claude.ai and the desktop app): Customize, Connectors, Add custom connector, then name it `0s and 1s` with the URL `https://0sand1s.co.uk/mcp`.

**Claude Code**:

```
claude mcp add --transport http 0sand1s https://0sand1s.co.uk/mcp
```

**Cursor** (`~/.cursor/mcp.json`):

```json
{ "mcpServers": { "0sand1s": { "url": "https://0sand1s.co.uk/mcp" } } }
```

**VS Code** (`.vscode/mcp.json`):

```json
{ "servers": { "0sand1s": { "type": "http", "url": "https://0sand1s.co.uk/mcp" } } }
```

## Try the API

```
curl "https://0sand1s.co.uk/api/v1/deduction?gross=1200&vat=200&materials=300&rate=20"
```

## About this repository

This repository holds the listing for the [official MCP registry](https://registry.modelcontextprotocol.io) (`server.json`, name `uk.co.0sand1s/cis`) and this README. The server is hosted by [0s and 1s](https://0sand1s.co.uk), CIS filing software for contractors. Questions: support@0sand1s.co.uk.
