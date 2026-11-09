# Unified.to for Cursor

Cursor plugin that connects agents to your [Unified.to](https://unified.to) workspace through Unified's official remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

Browse the integration catalog, create and inspect customer connections, look up API call logs and integration issues, manage webhooks and environments, and search the Unified docs, all from the Cursor agent.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **Unified.to**.
3. Click **Install**, then complete the Unified.to sign-in prompt.

Or run `/add-plugin unified-to` in chat.

## MCP

```json
{
  "mcpServers": {
    "unified": {
      "type": "http",
      "url": "https://mcp-api.unified.to/mcp"
    }
  }
}
```

Auth is OAuth 2.1 against Unified.to with Dynamic Client Registration (DCR) and PKCE. Cursor registers itself and prompts for Unified.to sign-in when the plugin connects, so there is no API key to configure.

### Using a workspace API key instead

If you prefer key-based auth, skip the plugin and add the server to `~/.cursor/mcp.json` (or a project's `.cursor/mcp.json`) with your key in an environment variable:

```json
{
  "mcpServers": {
    "unified-core": {
      "url": "https://mcp-api.unified.to/mcp",
      "headers": {
        "Authorization": "Bearer ${env:UNIFIED_API_KEY}"
      }
    }
  }
}
```

A workspace API key grants access to every connection in the account. Keep it out of committed files and shareable URLs.

## Regions

This plugin connects to the US region. Each region's server only sees that region's workspaces, so an EU or AU workspace can't sign in through it.

| Region | MCP URL |
| --- | --- |
| US | `https://mcp-api.unified.to/mcp` |
| EU | `https://mcp-api-eu.unified.to/mcp` |
| AU | `https://mcp-api-au.unified.to/mcp` |

If your workspace is in the EU or AU region, skip the plugin and add your region's server to `~/.cursor/mcp.json` (or a project's `.cursor/mcp.json`). Sign-in works the same way, with no API key:

```json
{
  "mcpServers": {
    "unified-core": {
      "type": "http",
      "url": "https://mcp-api-eu.unified.to/mcp"
    }
  }
}
```

Use `https://mcp-api-au.unified.to/mcp` for AU. The [MCP docs](https://docs.unified.to/mcp/core) list the regional hosts.

## What the agent can do

- List the integrations available in the Unified catalog
- Create, read, update, re-authorize, and remove connections
- Get the MCP URL for a specific connection
- Review API call logs and open integration issues
- Create, update, trigger, and resume webhooks
- Manage environments and secrets-manager configuration
- Search the Unified.to documentation

## Notes

- Tool calls run as the Unified.to user who authorizes the connection, with that user's workspace permissions.
- This plugin manages your Unified workspace. To give an agent access to an end user's connected account (their CRM, HRIS, and so on), use a connection's MCP URL instead. See the [MCP docs](https://docs.unified.to/mcp/core).

## Docs

- Unified MCP guide: https://docs.unified.to/mcp/core
- Server URL (US): https://mcp-api.unified.to/mcp

## License

MIT
