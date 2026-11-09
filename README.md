# Pineprompt MCP server

Pineprompt tracks how AI assistants talk about your brand. It runs your prompts daily on ChatGPT, Gemini, Claude, Google AI Overviews and Google AI Mode, and scores every answer for mentions, position, sentiment, cited sources and share of voice against your competitors.

The Pineprompt MCP server gives AI agents and MCP clients direct access to that data. Ask Claude, Cursor or any MCP client which competitors gained share of voice this week, which sources AI engines cite for your category, or how your sentiment moved on Gemini, and it answers from your own Pineprompt workspace.

This is the official, hosted remote MCP server, maintained by the Pineprompt team. This repository holds the listing metadata only; there is nothing to install or run locally.

- Endpoint: `https://pineprompt.com/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth 2.1 with dynamic client registration (sign in with your Pineprompt account)
- Documentation: https://pineprompt.com/docs/mcp
- Registry name: `com.pineprompt/pineprompt` in the official MCP Registry

## Requirements

A Pineprompt account on any paid plan. The MCP server is included on every plan. See https://pineprompt.com/pricing.

## Connect

### Claude (web and desktop)

Settings, then Connectors, then Add custom connector. Use `https://pineprompt.com/mcp` as the URL and sign in when prompted.

### Claude Code

```
claude mcp add --transport http pineprompt https://pineprompt.com/mcp
```

### Cursor, Windsurf, VS Code and other clients

```json
{
  "mcpServers": {
    "pineprompt": {
      "url": "https://pineprompt.com/mcp"
    }
  }
}
```

Clients that only support local stdio servers can use `mcp-remote`:

```json
{
  "mcpServers": {
    "pineprompt": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://pineprompt.com/mcp"]
    }
  }
}
```

### ChatGPT

Pineprompt is also available as a ChatGPT plugin: https://pineprompt.com/chatgpt-plugin

## Tools

Analytics (all accept an optional platforms filter):

- `list-brand-analytics`, `list-platform-analytics`, `list-prompt-analytics`, `list-monitor-analytics`
- `get-visibility-time-series`, `get-share-of-voice-time-series`, `get-position-time-series`, `get-sentiment-time-series`
- `list-source-analytics`, `list-source-url-analytics`, `list-source-url-prompt-analytics`, `get-source-type-analytics`, `get-source-url-type-analytics`, `get-source-usage-time-series`, `get-source-url-usage-time-series`

Answers and mentions:

- `list-responses`, `get-response`, `list-brand-mentions`, `get-brand-mention`, `list-citations`, `get-citation`, `list-sources`, `get-source`

Workspace:

- Organizations, projects, prompts, brands, monitors, segments and tags: `list-*`, `get-*`, `create-*`, `update-*` and `delete-*` tools
- Users and invitations: `list-users`, `update-user`, `delete-user`, `create-invitation`, `delete-invitation`

The `list-*` and `get-*` tools only read data. Tools that create, update or delete records change your workspace, so clients that support it should ask for confirmation before running them.

## Example prompts

- "Which brands gained share of voice in ChatGPT for my project over the last 30 days?"
- "List the domains AI engines cite most for my prompts, and which of them mention my competitors but not us."
- "How did my brand's average position on Gemini change week over week?"
- "Add these five prompts to my project and attach the tag 'pricing'."

## Support

Questions or problems: eric@pineprompt.com

Website: https://pineprompt.com
