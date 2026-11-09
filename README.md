# Unified.to plugins for Cursor

Official [Cursor](https://cursor.com) plugins from [Unified.to](https://unified.to). Each plugin connects the Cursor agent to one of Unified's remote [Model Context Protocol](https://modelcontextprotocol.io/) servers, with OAuth sign-in and no API keys to manage.

| Plugin | What it does | MCP server |
| --- | --- | --- |
| [**Unified.to**](plugins/unified-to) (`unified-to`) | Manage your Unified.to workspace: browse integrations, create and inspect connections, debug API calls and issues, configure webhooks and environments, and search the docs. | `https://mcp-api.unified.to/mcp` (US region; for EU and AU see [Regions](plugins/unified-to#regions)) |
| [**UnifiedModels**](plugins/unifiedmodels) (`unifiedmodels`) | Define data models once and generate them in 31 languages and schema formats, import existing schemas, and push generated code to GitHub. | `https://api.unifiedmodels.com/mcp` |

## Install

From the Cursor Marketplace, search for **Unified.to** or **UnifiedModels** and click **Install**, or run one of these in chat:

```
/add-plugin unified-to
/add-plugin unifiedmodels
```

Each plugin prompts you to sign in to its service the first time it connects.

## Repository layout

```
.cursor-plugin/marketplace.json   # lists both plugins
plugins/
  unified-to/                     # Unified.to workspace plugin
  unifiedmodels/                  # UnifiedModels plugin
```

Each plugin folder has its own `.cursor-plugin/plugin.json`, `mcp.json`, logo and README.

## Test locally

Copy a plugin folder (not a symlink) into `~/.cursor/plugins/local/`, then restart Cursor or run **Developer: Reload Window**:

```bash
cp -R plugins/unifiedmodels ~/.cursor/plugins/local/unifiedmodels
```

## License

MIT
