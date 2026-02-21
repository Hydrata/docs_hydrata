# Simulation Defaults

All hardcoded simulation constants are defined in `run_anuga/defaults.py`. These values are used when a scenario does not specify an explicit override.

## Constants reference

### Structure parameters

| Constant | Value | Description |
|----------|-------|-------------|
| `BUILDING_BURN_HEIGHT_M` | 5.0 | Height (metres) added to the DEM where building footprints are rasterised. This effectively creates walls that prevent water from flowing through buildings. |
| `BUILDING_MANNINGS_N` | 10.0 | Manning's roughness coefficient applied to building footprint polygons. A very high value that impedes flow. |
| `DEFAULT_MANNINGS_N` | 0.04 | Default Manning's roughness applied to all areas not covered by explicit friction polygons. Typical of light grass or bare soil. |

### Rainfall conversion

| Constant | Value | Description |
|----------|-------|-------------|
| `RAINFALL_FACTOR` | 1.0 x 10^-6 | Conversion factor from mm/hr rainfall intensity to m/s, which ANUGA uses internally. Applied as the `factor` parameter in `Polygonal_rate_operator`. |

### Domain evolution

| Constant | Value | Description |
|----------|-------|-------------|
| `MINIMUM_STORABLE_HEIGHT_M` | 0.005 | Minimum water depth (metres) stored in SWW output files. Cells with less water than this are treated as dry in the output. |
| `MIN_ALLOWED_HEIGHT_M` | 1.0 x 10^-5 | Minimum water depth (metres) used during velocity extrapolation in post-processing. Prevents division by near-zero depth. |
| `MAX_YIELDSTEPS` | 100 | Maximum number of yield steps during domain evolution. The yield step interval is `duration / MAX_YIELDSTEPS` or `MIN_YIELDSTEP_S`, whichever is larger. |
| `MIN_YIELDSTEP_S` | 60 | Minimum yield step interval in seconds. ANUGA will not write output more frequently than once per minute. |
| `MAX_YIELDSTEP_S` | 1800 | Maximum yield step interval in seconds (30 minutes). Even for very long simulations, output is written at least this often. |

### Mesh generation

| Constant | Value | Description |
|----------|-------|-------------|
| `MAX_TRIANGLE_AREA` | 10_000_000 | Maximum triangle area (m^2) in the mesher configuration. Acts as an upper bound for the coarsest possible mesh. |

### Post-processing

| Constant | Value | Description |
|----------|-------|-------------|
| `K_NEAREST_NEIGHBOURS` | 3 | Number of nearest neighbours used when interpolating ANUGA mesh results to regular GeoTIFF grids. |

### External tools

| Constant | Value | Description |
|----------|-------|-------------|
| `DEFAULT_MESHER_EXE` | `/opt/venv/hydrata/bin/mesher` | Default path to the mesher binary used for adaptive mesh generation. Override with the `MESHER_EXE` environment variable. |
