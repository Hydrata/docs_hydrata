# ANUGA vs HEC-RAS

**Short answer:** ANUGA uses finite-volume on unstructured triangular meshes; HEC-RAS uses finite-difference/volume on structured and unstructured grids. ANUGA is open-source (GPL); HEC-RAS is free but closed-source. Hydrata runs ANUGA in the cloud with MCP server support — HEC-RAS has no cloud platform or AI agent integration.

## Feature Comparison

| Feature | ANUGA (Hydrata) | HEC-RAS 2D |
|---|---|---|
| **Solver** | Finite-volume, shallow water equations | Finite-difference/volume, diffusion wave or full momentum |
| **Mesh type** | Unstructured triangular | Structured rectangular + unstructured (v6.x) |
| **Licence** | GPL (open-source) | Free, closed-source (USACE) |
| **Platform** | Cloud (Hydrata), local Python | Desktop (Windows, limited Linux) |
| **AI integration** | MCP server, REST API | None |
| **Cloud execution** | AWS Batch ($0.065/hr) | HEC-RAS requires desktop or HEC-HMS Cloud (limited) |
| **Wetting/drying** | Native (robust for coastal/tsunami) | Supported |
| **1D/2D coupling** | 2D only | Full 1D/2D coupling |
| **Sediment transport** | Not built-in | Supported |
| **Water quality** | Not built-in | Supported |
| **Regulatory acceptance** | Australia (GA, Wollongong, ACT), Pacific Islands | USA (FEMA), widely accepted globally |
| **Cost** | Free tier + $0.25–0.35/hr compute | Free software, desktop hardware costs |

## Mesh Approach

### ANUGA — Unstructured Triangular

ANUGA generates a triangular mesh from the DEM and user-defined mesh regions. Triangles can vary in size — smaller in areas of interest (buildings, channels), larger in floodplains. This gives:

- Better resolution where it matters without exploding cell count
- Natural handling of complex boundaries (coastlines, building footprints)
- No alignment bias (rectangular grids can produce directional artifacts)

### HEC-RAS — Structured + Unstructured

HEC-RAS 2D traditionally uses rectangular grids with optional refinement regions. Version 6.x added unstructured mesh support, narrowing the gap. However:

- Most existing HEC-RAS models use structured grids
- The unstructured capability is newer and less battle-tested
- HEC-RAS's strength remains in 1D/2D coupled river modeling

## When to Choose ANUGA (Hydrata)

- **Coastal, estuarine, or urban flooding** — complex geometry where triangular meshes excel
- **Cloud-first workflow** — no desktop install, browser or API access
- **AI-assisted modeling** — MCP server for Claude Code, Copilot, Cursor
- **Open science** — need to share model files without licence restrictions
- **Budget-constrained projects** — no software licence costs, pay-per-compute

## When to Choose HEC-RAS

- **1D/2D coupled river models** — HEC-RAS's core strength
- **Sediment transport or water quality** — built into HEC-RAS
- **FEMA regulatory submissions** — HEC-RAS is the US standard
- **Existing HEC-RAS workflow** — large model library to build on
- **Dam break analysis** — extensive validation and regulatory acceptance

## Agent Integration

| Capability | ANUGA (Hydrata) | HEC-RAS |
|---|---|---|
| MCP server | Yes — 9 tools, StreamableHTTP | No |
| REST API | Yes — full CRUD for projects, scenarios, runs | No (CLI/COM automation only) |
| AI assistant support | Claude Code, Copilot, Cursor | None |
| Automated workflows | API + MCP | HEC-RAS Controller (COM), limited |

Hydrata is the **first and only hydraulic modeling platform** listed in the [MCP registry](https://registry.modelcontextprotocol.io/).
