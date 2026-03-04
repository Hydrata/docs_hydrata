# Compare Flood Modeling Software

Hydrata runs the ANUGA open-source 2D flood solver in the cloud. How does it compare to other hydraulic modeling platforms?

## Comparisons

| Comparison | Summary |
|---|---|
| [ANUGA vs HEC-RAS](anuga-vs-hecras.md) | Finite-volume vs finite-difference, mesh types, regulatory acceptance, agent integration |
| [Flood Modeling Software 2026](flood-modeling-software.md) | Multi-platform comparison: HEC-RAS, TUFLOW, ANUGA, MIKE+, Flood Platform |

## Why ANUGA?

ANUGA uses a **finite-volume method on unstructured triangular meshes**. This makes it particularly well-suited for:

- **Complex topography** — coastal, estuarine, and urban terrain where rectangular grids struggle
- **Wetting and drying** — robust handling of flow fronts moving across dry land
- **Dam break and tsunami** — validated for rapid transient flows
- **Open science** — GPL licence, no vendor lock-in, portable model files

ANUGA was developed by **Geoscience Australia** and the **Australian National University** and has been validated against 30+ benchmark problems including laboratory experiments, field observations, and analytical solutions.

## Hydrata's Advantage

Hydrata is the **only hydraulic modeling platform with a native MCP server**. No other platform — HEC-RAS, TUFLOW, MIKE+, or Flood Platform — can be called directly from an AI coding assistant.

- **Browser interface** — no desktop install, no Python environment
- **MCP server** — Claude Code, GitHub Copilot, Cursor integration
- **REST API** — full programmatic access to projects, scenarios, and results
- **AWS Batch compute** — $0.065/hr, no queues, auto-scaling
