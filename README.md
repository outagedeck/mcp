# OutageDeck MCP server

[![OutageDeck on Glama](https://img.shields.io/badge/Glama-healthy%20%C2%B7%2014%20tools%20%C2%B7%204.3%2F5-12b981)](https://glama.ai/mcp/connectors/com.outagedeck/outagedeck-status)

[OutageDeck](https://outagedeck.com) gives AI coding agents live status, incident timelines, and independent uptime history for 172 cloud and SaaS vendors. The remote server reads each vendor's official status feed and needs no API key for public status checks.

Use it to answer **“is it us or them?” before debugging your code**.

- Remote MCP endpoint: `https://outagedeck.com/api/mcp`
- Transport: Streamable HTTP
- Public status tools: free, no account or key
- Official MCP Registry: `com.outagedeck/outagedeck-status`
- Full documentation: [outagedeck.com/developers/mcp](https://outagedeck.com/developers/mcp)

## Connect in one line

Claude Code:

```sh
claude mcp add --transport http outagedeck https://outagedeck.com/api/mcp
```

For MCP clients that accept JSON configuration:

```json
{
  "mcpServers": {
    "outagedeck": {
      "url": "https://outagedeck.com/api/mcp"
    }
  }
}
```

No package, daemon, or environment variable is required.

## What an agent can do

Ask your agent:

- “Before debugging this deploy, check AWS, Cloudflare, GitHub, and OpenAI.”
- “Is Claude down, or is this failure in my app?”
- “What major vendor incidents are active right now?”
- “Show GitHub's uptime and incident history for the last 30 days.”
- “Give me a citable timeline for the current Cloudflare incident.”

Public tools:

| Tool | Purpose |
| --- | --- |
| `get_provider_status` | Live status for one provider |
| `check_my_stack` | One verdict across up to 12 providers |
| `list_active_incidents` | Active incidents across the catalog |
| `get_incident_details` | A vendor's complete incident update timeline |
| `get_uptime` | Independent 7–90 day uptime history |
| `get_outage_report` | Cross-vendor reliability summary |
| `search_providers` | Find providers by company or product name |
| `search` and `fetch` | Search and retrieve citable OutageDeck documents |

Account tools let subscribers manage their own custom providers and alerts without sharing webhook credentials in a conversation: `list_custom_providers`, `add_custom_provider`, `update_custom_provider`, `remove_custom_provider`, and `watch_provider`.

## Data and trust model

OutageDeck reads official provider status feeds about every 10 minutes. It does not guess from social reports or claim to replace a provider's own status page. Tool results include source and OutageDeck links so an agent can cite what it reports.

Public tools are read-only. Account-specific tools require an OutageDeck API key, and each tool declares its read-only, idempotent, and destructive hints to MCP clients.

## Availability and plans

Provider status, incident history, the public API, RSS, badges, and the public MCP tools are free without an account. Free accounts add email alerts for up to five providers. Paid plans add Slack, Teams, Discord, and webhook alerts, custom providers, and higher API quotas.

- [Create a free alert](https://outagedeck.com/account)
- [See pricing](https://outagedeck.com/pricing)
- [Browse all providers](https://outagedeck.com/providers)

## Registry metadata

[`server.json`](server.json) mirrors the active record published to the official MCP Registry. This repository documents the hosted service; it does not contain the production server implementation. The MIT license applies to the documentation and registry metadata in this repository.

Questions or security reports: [hello@outagedeck.com](mailto:hello@outagedeck.com)
