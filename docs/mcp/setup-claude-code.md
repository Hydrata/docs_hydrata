# Claude Code Setup

Connect [Claude Code](https://claude.ai/claude-code) (Anthropic's CLI assistant) to Hydrata's MCP server.

## Prerequisites

- Claude Code installed (`npm install -g @anthropic-ai/claude-code`)
- A [Hydrata account](https://hydrata.com/account/signup/) with API token

## Configuration

### Option 1: CLI Command (Recommended)

```bash
export HYDRATA_TOKEN="your-api-token-here"

claude mcp add hydrata https://hydrata.com/mcp/ \
  --transport streamable-http \
  --header "Authorization: Bearer $HYDRATA_TOKEN"
```

### Option 2: Project Config File

Add to your project's `.mcp.json`:

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

### Option 3: Global Config

Add to `~/.claude/.mcp.json` to make Hydrata available in all projects.

## Verify Connection

Start Claude Code and check that Hydrata tools are available:

```bash
claude
```

Then ask:

```
> List my Hydrata projects
```

You should see Claude call the `list_projects` tool and return your project list.

## Example Session

```
$ claude

> Create a flood model for Merewether, NSW using a 5m DEM

  I'll set up the flood model. Let me:

  1. Create the project
  Tool: create_project("Merewether Flood Study")                    ✓

  2. Upload the DEM
  Tool: upload_dem(project_id=42, file="merewether_5m.tif")         ✓

  3. Configure the scenario
  Tool: create_scenario(friction=0.03, rainfall="100yr_6hr")        ✓

  4. Run the simulation
  Tool: run_simulation(scenario_id=87)                              ✓

  5. Get results
  Tool: get_results(run_id=201)                                     ✓

  Simulation complete. Peak depth: 1.42m at outlet.
  Results: https://hydrata.com/catalogue/merewether-flood-depth-201
```

## Tips

- **Environment variable for token**: Set `HYDRATA_TOKEN` in your shell profile to avoid hardcoding the token
- **Project-scoped config**: Use `.mcp.json` in your project root for team sharing (but don't commit tokens)
- **Multiple tools in one prompt**: Claude Code can chain multiple Hydrata tools in a single response — ask for the full workflow in one message

## Troubleshooting

### "Tool not found" error
Restart Claude Code after adding the MCP server config. Run `claude mcp list` to verify the server is registered.

### Authentication failures
Verify your token: `curl -H "Authorization: Bearer $HYDRATA_TOKEN" https://hydrata.com/api/v2/`

### Timeout on simulation
Large models can take 10+ minutes. Ask Claude to check status: "What's the status of run 201?"
