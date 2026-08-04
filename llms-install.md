# Install OutageDeck MCP

OutageDeck is a hosted Streamable HTTP MCP server. Do not clone this repository, install a package, start a process, or ask the user for a credential.

Endpoint: `https://outagedeck.com/api/mcp`

For Claude Code, run:

```sh
claude mcp add --transport http outagedeck https://outagedeck.com/api/mcp
```

For clients that accept MCP JSON, add:

```json
{
  "mcpServers": {
    "outagedeck": {
      "url": "https://outagedeck.com/api/mcp"
    }
  }
}
```

After connecting, call `tools/list`. Confirm that `get_provider_status`, `check_my_stack`, and `list_active_incidents` are present. Public status tools are read-only and keyless. Account-specific tools may request authorization when used.
