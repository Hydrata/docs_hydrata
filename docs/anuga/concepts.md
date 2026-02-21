# ANUGA Concepts

[ANUGA](https://github.com/anuga-community/anuga_core) is an open-source two-dimensional hydrodynamic model that solves the shallow water equations on an unstructured triangular mesh. Hydrata uses ANUGA as its core computational engine.

## What ANUGA does

Given a terrain surface, boundary conditions, and water inflows, ANUGA simulates how water flows across the landscape over time. It produces time-series outputs of:

- **Depth** — water depth at each point
- **Velocity** — flow speed and direction
- **Stage** — water surface elevation (depth + terrain elevation)
- **Momentum** — depth-integrated velocity

## Key concepts

### Triangular mesh

ANUGA discretises the domain into an unstructured mesh of triangles. Each triangle is a computational cell where depth, velocity, and stage are calculated at each timestep.

The mesh is generated from:

- A **bounding polygon** (from boundary lines)
- A **maximum triangle area** (from the resolution setting)
- Optional **interior regions** (from mesh regions) with finer resolution

### Manning's roughness (n)

Manning's n is a dimensionless coefficient that describes surface friction. It controls how fast water flows over different terrain types:

- Lower values (0.01-0.03): smooth surfaces, fast flow
- Higher values (0.05-0.10): vegetated surfaces, slower flow
- Very high values (10.0): buildings, effectively blocking flow

### Boundary conditions

Boundary conditions control what happens at the edges of the domain:

| Type | Effect |
|------|--------|
| **Reflective** | Water bounces back (solid wall) |
| **Transmissive** | Water passes through freely |
| **Dirichlet** | Fixed water level (typically 0) |

### Yield steps

ANUGA runs internally at very small adaptive timesteps for numerical stability, but only writes output at **yield steps**. The yield step interval is computed automatically:

- At most every 60 seconds (`MIN_YIELDSTEP_S`)
- At least every 30 minutes (`MAX_YIELDSTEP_S`)
- No more than 100 yield steps total (`MAX_YIELDSTEPS`)

### Checkpointing

For long simulations, ANUGA periodically saves the domain state to pickle files. If a run is interrupted, it can restart from the last checkpoint using the `batch_number` and `checkpoint_time` parameters.

## The simulation pipeline

```
1. Parse scenario.json          → setup_input_data()
2. Generate mesh                → create_mesher_mesh() or create_anuga_mesh()
3. Set elevation on mesh        → domain.set_quantity('elevation', ...)
4. Set friction on mesh         → domain.set_quantity('friction', ...)
5. Apply boundary conditions    → domain.set_boundary(...)
6. Apply inflow operators       → Polygonal_rate_operator / Inlet_operator
7. Evolve domain                → domain.evolve(yieldstep, finaltime)
8. Post-process to GeoTIFFs     → post_process_sww()
```

This pipeline runs inside `run_sim()` in `run_anuga/run.py`. Steps 1-6 happen once; step 7 iterates over yield steps until the simulation duration is reached.
