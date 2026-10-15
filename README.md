# Pineprompt MCP server

The official remote MCP server for [Pineprompt](https://pineprompt.com), maintained by the Pineprompt team.

Pineprompt tracks how AI search engines talk about your brand. It runs your prompts daily on ChatGPT, Gemini, Perplexity, Claude, Google AI Overviews, Google AI Mode and Copilot, and reports mentions, position, sentiment, cited sources, competitors and share of voice by country and language.

This MCP server lets your AI assistant query that data directly: visibility trends, competitor comparisons, cited sources and the raw answers behind them.

This repository holds the listing metadata only. The server is hosted; there is nothing to install or run.

## Connect

- URL: `https://pineprompt.com/mcp`
- Transport: Streamable HTTP
- Auth: OAuth (you sign in with your Pineprompt account when your client connects)

Claude Code:

```
claude mcp add --transport http pineprompt https://pineprompt.com/mcp
```

Cursor, VS Code and other clients that take a JSON config:

```json
{
  "mcpServers": {
    "pineprompt": {
      "url": "https://pineprompt.com/mcp"
    }
  }
}
```

In Claude.ai, add a custom connector with the URL above.

## Requirements

A paid Pineprompt plan (Starter and up). MCP access is included on every plan. See [pricing](https://pineprompt.com/pricing).

## Links

- Docs: https://pineprompt.com/docs/mcp
- Registry entry: `com.pineprompt/pineprompt` in the official MCP Registry (`server.json` in this repo)
- Support: eric@pineprompt.com
