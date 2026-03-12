# Cloud ANUGA

Professional ANUGA flood simulations with managed data, cloud compute, and published results. No Python environment, no desktop install.

## What is Cloud ANUGA?

Hydrata hosts the [ANUGA](https://github.com/anuga-community/anuga_core) open-source 2D flood solver on cloud infrastructure. You upload terrain data, configure scenarios, and Hydrata handles:

- **Mesh generation** — automatic triangulation from your DEM and region definitions
- **Compute provisioning** — cloud compute allocated on demand
- **Execution** — ANUGA runs on optimized compute instances
- **Results publishing** — flood outputs published as OGC WMS/WFS layers

## How It Works

```
Your DEM + scenario config
        ↓
    Hydrata API / MCP / Browser
        ↓
    Cloud compute (optimized instances)
        ↓
    ANUGA solver (unmodified)
        ↓
    Flood depth, velocity, extent → WMS layers
```

## Access Methods

| Method | Best for | Documentation |
|---|---|---|
| **Browser** | Interactive setup, visual results | [Getting Started](../getting-started/index.md) |
| **MCP Server** | AI-assisted modeling workflows | [MCP Server](../mcp/index.md) |
| **REST API** | Programmatic access, automation | [API Reference](https://hydrata.com/api/v2/) |
| **Python (local)** | Running locally with `run_anuga` | [Standalone Usage](../anuga/getting-started.md) |

## Solver Integrity

Hydrata runs **unmodified ANUGA**. We do not fork or modify the solver. Your results are identical to running ANUGA locally with the same inputs.

- Solver: `anuga_core` (GPL, Geoscience Australia + ANU)
- Runner: `run_anuga` (MIT, [GitHub](https://github.com/Hydrata/run_anuga))
- Model files: portable `scenario.json` format — export and run anywhere

## Validated

ANUGA has been validated against 30+ benchmark problems. See [Validation](../validation/index.md) for details, including the [Merewether benchmark](../validation/merewether.md) which completes in under 2 minutes on Hydrata cloud.

## Get Started

1. [Sign up free](https://hydrata.com/account/signup/) — no credit card required
2. [Create your first project](../getting-started/create-a-new-project.md) — upload a DEM and run a simulation
3. Or [connect your AI assistant](../mcp/index.md) — run flood models from Claude Code, Copilot, or Cursor
