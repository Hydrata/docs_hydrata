# Cloud ANUGA

Run ANUGA flood simulations in the cloud. No Python environment, no desktop install, no IT department approval.

## What is Cloud ANUGA?

Hydrata hosts the [ANUGA](https://github.com/anuga-community/anuga_core) open-source 2D flood solver on AWS cloud infrastructure. You upload terrain data, configure scenarios, and Hydrata handles:

- **Mesh generation** — automatic triangulation from your DEM and region definitions
- **Compute provisioning** — AWS Batch allocates resources on demand
- **Execution** — ANUGA runs on optimized compute instances
- **Results publishing** — flood outputs published as OGC WMS/WFS layers

## How It Works

```
Your DEM + scenario config
        ↓
    Hydrata API / MCP / Browser
        ↓
    AWS Batch (c7a.xlarge spot, $0.065/hr)
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

## Pricing

| Tier | Cost | Includes |
|---|---|---|
| **Free** | $0 | 3 simulation runs, no credit card required |
| **Pay-as-you-go** | $0.25–0.35/hr | Unlimited runs, AWS Batch spot instances |
| **Team** | Contact us | Shared workspace, dedicated compute, priority support |

Typical costs:

- **Merewether benchmark** (small urban model): ~$0.017/run
- **Medium catchment** (1–5 km²): ~$0.50–2.00/run
- **Large floodplain** (50+ km²): ~$5–20/run

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
