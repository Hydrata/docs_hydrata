# Hydrata MCP Server

Hydrata provides a native [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) server for AI coding assistants. Manage flood model inputs, run simulations, and retrieve results directly from your AI assistant.

**Endpoint:** `https://hydrata.com/mcp/`
**Transport:** StreamableHTTP
**Registry:** [registry.modelcontextprotocol.io](https://registry.modelcontextprotocol.io/)

## Available Tools

The MCP server exposes 9 tools for the complete flood modeling workflow:

| Tool | Description |
|---|---|
| `list_projects` | List all projects for the authenticated user |
| `create_project` | Create a new flood modeling project |
| `get_project` | Get project details including scenarios and runs |
| `create_scenario` | Configure model inputs — DEM, boundaries, friction, rainfall |
| `list_scenarios` | List scenarios within a project |
| `run_simulation` | Submit an ANUGA simulation to cloud compute |
| `get_run_status` | Check simulation progress and status |
| `get_results` | Retrieve simulation outputs — depth maps, velocity, extents |
| `list_runs` | List all runs for a scenario |

## Supported Clients

- [Claude Code](setup-claude-code.md) — Anthropic's CLI assistant
- [GitHub Copilot](setup-copilot.md) — VS Code with MCP support
- [Cursor](setup-cursor.md) — AI-first code editor

Any MCP-compatible client can connect via the StreamableHTTP transport.

## Authentication

All MCP requests require a Bearer token. Get your API key by:

1. [Sign up](https://hydrata.com/account/signup/) for a free Hydrata account
2. API key is provisioned on email confirmation
3. Pass it as `Authorization: Bearer <your-token>` header

## Quick Start

```bash
# Add Hydrata MCP server to Claude Code
claude mcp add hydrata https://hydrata.com/mcp/ \
  --transport streamable-http \
  --header "Authorization: Bearer $HYDRATA_TOKEN"
```

Then ask Claude to create a flood model:

```
> Create a flood model for my site using a 5m DEM
```

See [Getting Started](getting-started.md) for a complete walkthrough.
