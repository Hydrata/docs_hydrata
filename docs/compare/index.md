# Why Hydrata

Engineers spend roughly 68% of flood modeling project time on setup and data processing — mesh generation, boundary definition, friction mapping, DEM preprocessing. Only about 8% is spent actually running simulations. Hydrata addresses the 68%, not just the 8%.

## The Problem

Flood model setup is the most time-consuming task in hydraulic engineering. It relies on repetitive manual work and subjective decision-making. If a mesh is regenerated, all hand editing is lost. Models live as files on individual machines with no version control, no collaboration, and no audit trail.

Meanwhile, ANUGA — one of the most capable 2D solvers available — has been locked behind a Python scripting interface for 20 years. Excellent physics, near-zero accessibility for practicing engineers.

## What Hydrata Does Differently

| Traditional Workflow | Hydrata |
|---|---|
| Convert DEM in GIS, export, import to model | Upload DEM directly — Hydrata handles projection and tiling |
| Define boundaries in separate tools | Draw boundaries in the browser on your terrain data |
| Hand-edit mesh in desktop software | Mesh generated from your DEM and region definitions |
| Run simulation on local hardware | Submit to cloud compute — results in minutes |
| Post-process in GIS, format for reports | Results published as OGC WMS layers, shareable via URL |
| Email model files to colleagues | Team works on the same project, every change tracked |

## Learn More

- [Why ANUGA](why-anuga.md) — the solver behind Hydrata, and why it matters
- [Flood Modeling Challenges](flood-modeling-challenges.md) — industry-wide pain points and how Hydrata addresses them
- [Validation](../validation/index.md) — benchmark results and regulatory acceptance
