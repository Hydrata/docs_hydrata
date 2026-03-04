# Cursor Setup

Connect [Cursor](https://cursor.com/) (AI-first code editor) to Hydrata's MCP server.

## Prerequisites

- Cursor editor installed
- A [Hydrata account](https://hydrata.com/account/signup/) with API token

## Configuration

Create or edit `.cursor/mcp.json` in your project root:

```json
{
  "mcpServers": {
    "hydrata": {
      "url": "https://hydrata.com/mcp/",
      "transport": "streamable-http",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN_HERE"
      }
    }
  }
}
```

## Verify Connection

1. Open Cursor's AI chat panel
2. Type: "List my Hydrata projects"
3. Cursor should call the `list_projects` tool and return results

## Usage

In Cursor's chat, interact with your flood models:

```
Create a flood model project, upload terrain data from ./data/site_dem.tif,
and run a simulation with 50-year rainfall
```

Cursor will chain the Hydrata MCP tools to complete the workflow.

## Tips

- **Project-scoped config**: Keep `.cursor/mcp.json` in your project root for per-project setup
- **Token security**: Don't commit tokens to git — use environment variables or add `.cursor/` to `.gitignore`
- **Composer mode**: Use Cursor's Composer for multi-step workflows — it handles tool chaining well
