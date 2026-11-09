# UnifiedModels for Cursor

Cursor plugin that connects agents to [UnifiedModels](https://www.unifiedmodels.com) through its official remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

UnifiedModels is a data-modeling platform: define each model, enum and constant once, then generate matching code in 31 languages and schema formats, including TypeScript, Go, Python, C#, Rust, OpenAPI, GraphQL, Protobuf, JSON Schema, Prisma, TypeORM, Mongoose, Zod, Joi and Typebox. With this plugin, the Cursor agent can read and edit your models, convert existing schemas, and push generated code to your GitHub repositories.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **UnifiedModels**.
3. Click **Install**, then complete the UnifiedModels sign-in prompt.

Or run `/add-plugin unifiedmodels` in chat.

## MCP

```json
{
  "mcpServers": {
    "unifiedmodels": {
      "type": "http",
      "url": "https://api.unifiedmodels.com/mcp"
    }
  }
}
```

Auth is OAuth 2.1 against your UnifiedModels account, with Dynamic Client Registration (DCR) and PKCE. Cursor registers itself and prompts you to sign in when the plugin first connects, so there is no API key to configure. Access tokens last one hour and Cursor refreshes them automatically.

## What the agent can do

- **Projects:** list, read, create, update, lint and delete projects
- **Models, enums and constants:** read and edit them, including single-field and single-row changes
- **History:** list versions, diff a version, and restore one
- **Generate:** render a project in any enabled language or schema format
- **Import:** detect a schema's format and parse it into models and enums, without saving until you ask
- **GitHub:** list repositories and branches, connect repositories to a project, and push generated code

## Example prompts

- "List my UnifiedModels projects."
- "What fields does the Customer model in my Store project have?"
- "Generate my Store project as TypeScript."
- "Convert this SQL `CREATE TABLE` into a UnifiedModels model, but don't save it yet."
- "Add an optional `nickname` string field to the Customer model."

## Notes

- Tool calls run as the UnifiedModels user who signs in, and can only reach projects that user owns or collaborates on.
- Generated code covers the languages enabled on each project. Enable a language in the project first if it isn't listed.
- Edits change your saved models. Use the version history tools to review or roll back a change.

## Docs

- UnifiedModels MCP guide: https://www.unifiedmodels.com/mcp
- Server URL: https://api.unifiedmodels.com/mcp
- Privacy policy: https://www.unifiedmodels.com/privacy
- Support: https://www.unifiedmodels.com/contact

## License

MIT
