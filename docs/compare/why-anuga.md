# Why ANUGA

ANUGA is a 2D shallow water equation solver developed by **Geoscience Australia** and the **Australian National University**. It has been in active development for over 20 years and is validated against 30+ benchmark problems.

Hydrata is the web platform that makes ANUGA accessible to practicing engineers — the interface it never had.

## Technical Strengths

### Unstructured Triangular Mesh

ANUGA uses a finite-volume method on unstructured triangular meshes. This is a fundamental advantage for real-world flood modeling:

- **Variable resolution** — small triangles where detail matters (buildings, channels), large triangles in open floodplain. No wasted cells.
- **Complex boundaries** — coastlines, building footprints, and irregular terrain are represented naturally, not forced onto rectangular grids.
- **No directional bias** — rectangular grids can produce artifacts aligned with grid axes. Triangular meshes do not.

### Robust Wetting and Drying

ANUGA handles flow fronts moving across dry land without numerical instabilities. This makes it well-suited for:

- Dam break and sudden inundation events
- Tidal flooding and storm surge
- Overland flow from intense rainfall

### Large Catchment Performance

ANUGA has been demonstrated on catchments up to 85,000 km² — orders of magnitude larger than typical desktop model domains.

### High Froude Number Stability

ANUGA handles supercritical flow transitions (high Froude numbers) that cause instabilities in some other solvers. Important for steep urban channels and dam break scenarios.

## Institutional Backing

| Organisation | Role |
|---|---|
| **Geoscience Australia** | Primary developer, national tsunami risk assessments |
| **Australian National University** | Mathematical Sciences Institute, solver algorithms |
| **ANUGA Community** | Open-source maintenance, validation suite |

This is government-agency-grade software, not a research prototype. GA uses ANUGA for Australia's national disaster preparedness program.

## Open Source (GPL)

- Full source code: [github.com/anuga-community/anuga_core](https://github.com/anuga-community/anuga_core)
- GPL licence — no vendor lock-in, no licence fees
- 100+ peer-reviewed publications using ANUGA
- Portable model files — export from Hydrata and run locally anytime

## The Accessibility Problem

Despite excellent physics, ANUGA has 213 GitHub stars and approximately 3 active maintainers after 20 years. Why?

**ANUGA has no GUI.** To use it, you write Python scripts that define geometry, boundary conditions, friction values, mesh resolution, and solver parameters. This excludes the vast majority of practicing civil and hydraulic engineers, who work in visual tools.

Hydrata solves this. Upload your terrain data, define scenarios in the browser, and run simulations on cloud compute. The same ANUGA solver, without the Python scripting barrier.

## Validated

ANUGA has been validated against:

- 30+ benchmark problems (analytical solutions, laboratory experiments, field observations)
- The [Merewether benchmark](../validation/merewether.md) — urban flood in Newcastle, NSW
- National-scale tsunami inundation mapping for Australia and Pacific Island nations

See [Validation](../validation/index.md) for details.
