# GitHub Copilot Setup

Connect GitHub Copilot in VS Code to Hydrata's MCP server.

!!! note "MCP Support in Copilot"
    GitHub Copilot's MCP support requires VS Code 1.99+ and Copilot Chat extension. Check [GitHub's MCP documentation](https://docs.github.com/en/copilot/using-github-copilot/using-extensions-to-integrate-external-tools-with-copilot-chat) for the latest status.

## Prerequisites

- VS Code 1.99+ with GitHub Copilot Chat extension
- A [Hydrata account](https://hydrata.com/account/signup/) with API token

## Configuration

Add to your project's `.vscode/settings.json`:

```json
{
  "github.copilot.chat.mcpServers": {
    "hydrata": {
      "url": "https://hydrata.com/mcp/",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN_HERE"
      }
    }
  }
}
```

Or add to your user settings for global access.

## Verify Connection

1. Open the Copilot Chat panel (`Ctrl+Shift+I`)
2. Type: "List my Hydrata projects"
3. Copilot should call the `list_projects` tool

## Usage

In Copilot Chat, ask about your flood models:

```
@workspace Create a new flood modeling project and configure a 100-year storm scenario
```

Copilot will use Hydrata's MCP tools to create the project and configure the scenario.

## Tips

- Use `@workspace` mention to give Copilot access to MCP tools
- Don't commit `.vscode/settings.json` with your API token — use environment variables or `.gitignore`
