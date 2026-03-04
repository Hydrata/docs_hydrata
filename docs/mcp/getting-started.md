# Getting Started with the Hydrata MCP Server

This guide walks through connecting your AI coding assistant to Hydrata and running your first flood simulation.

## Prerequisites

1. A [Hydrata account](https://hydrata.com/account/signup/) (free tier includes 3 simulation runs)
2. Your API token (provisioned on email confirmation)
3. An MCP-compatible AI assistant ([Claude Code](setup-claude-code.md), [GitHub Copilot](setup-copilot.md), or [Cursor](setup-cursor.md))

## Step 1: Connect Your Client

=== "Claude Code"

    ```bash
    claude mcp add hydrata https://hydrata.com/mcp/ \
      --transport streamable-http \
      --header "Authorization: Bearer $HYDRATA_TOKEN"
    ```

=== "GitHub Copilot (VS Code)"

    Add to `.vscode/settings.json`:
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

=== "Cursor"

    Add to `.cursor/mcp.json`:
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

## Step 2: Verify Connection

Ask your AI assistant:

```
> List my Hydrata projects
```

You should see a response from the `list_projects` tool showing your projects (empty list if you're new).

## Step 3: Create a Flood Model

Here's a typical workflow conversation:

```
> Create a new flood modeling project called "Site Assessment"
```

The assistant calls `create_project` and returns the project ID.

```
> Upload my DEM file site_dem_5m.tif to the project
```

The assistant calls `upload_dem` with your file.

```
> Create a scenario with Manning's n = 0.035 and a 100-year 6-hour rainfall event
```

The assistant calls `create_scenario` with your parameters.

```
> Run the simulation
```

The assistant calls `run_simulation`. The job runs on AWS Batch — typically 2–10 minutes depending on model size.

```
> Check the status
```

The assistant calls `get_run_status` and reports progress.

```
> Show me the results
```

The assistant calls `get_results` and returns flood depth maps, maximum velocities, and result URLs.

## Available Tools Reference

### Project Management

| Tool | Parameters | Returns |
|---|---|---|
| `list_projects` | — | Array of projects with IDs, names, dates |
| `create_project` | `name` | New project ID and details |
| `get_project` | `project_id` | Full project with scenarios and runs |

### Scenario Configuration

| Tool | Parameters | Returns |
|---|---|---|
| `create_scenario` | `project_id`, model parameters | New scenario ID |
| `list_scenarios` | `project_id` | Array of scenarios |

### Simulation

| Tool | Parameters | Returns |
|---|---|---|
| `run_simulation` | `scenario_id` | Run ID, initial status |
| `get_run_status` | `run_id` | Current status, progress |
| `get_results` | `run_id` | Result URLs, summary statistics |
| `list_runs` | `scenario_id` | Array of runs with status |

## Common Workflows

### Quick Site Assessment

```
> Create a project "Quick Assessment", upload dem.tif, create a scenario with
  default friction and 50-year rainfall, run it, and show results when done.
```

### Scenario Comparison

```
> For project 42, create three scenarios: one with 10-year, one with 50-year,
  and one with 100-year rainfall. Run all three and compare peak depths.
```

### Sensitivity Analysis

```
> Run the same scenario with Manning's n = 0.02, 0.035, and 0.05.
  Compare the results to understand friction sensitivity.
```

## Next Steps

- [Claude Code Setup](setup-claude-code.md) — detailed configuration for Claude Code
- [GitHub Copilot Setup](setup-copilot.md) — VS Code configuration
- [Cursor Setup](setup-cursor.md) — Cursor IDE configuration
- [Validation](../validation/index.md) — benchmark results and regulatory acceptance
