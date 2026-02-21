# Package Format

A Hydrata scenario package is a self-contained directory (or zip file) with everything needed to run an ANUGA simulation.

## Directory structure

```
package/
  scenario.json                    # simulation configuration
  inputs/
    dem.tif                        # elevation raster (GeoTIFF, projected CRS)
    boundary.geojson               # domain boundary lines
    inflow.geojson                 # rainfall / surface inflow features
    friction.geojson               # friction zones (optional)
    structure.geojson              # building footprints (optional)
    mesh_region.geojson            # mesh refinement regions (optional)
    catchment.geojson              # catchment polygons (optional)
    nodes.geojson                  # network nodes (optional)
    links.geojson                  # network links (optional)
  outputs_<project>_<scenario>_<run>/   # created at runtime
    run_<p>_<s>_<r>.sww            # ANUGA SWW time-series output
    run_<p>_<s>_<r>_depth_max.tif
    run_<p>_<s>_<r>_velocity_max.tif
    run_<p>_<s>_<r>_depthIntegratedVelocity_max.tif
    run_<p>_<s>_<r>_stage_max.tif
    run_<p>_<s>_<r>_depth_*.tif    # per-timestep depth rasters
    run_anuga_<batch>.log          # simulation log
    checkpoints/                   # checkpoint pickle files
```

## Input file formats

### Elevation (`dem.tif`)

- **Format:** GeoTIFF
- **CRS:** Any projected system (e.g. EPSG:28355). Must be in metres.
- **Band:** Single-band float with elevation in metres above datum

### Boundary (`boundary.geojson`)

GeoJSON FeatureCollection with LineString features. Each feature has:

- `properties.boundary` — one of `Reflective`, `Transmissive`, `Dirichlet`
- `properties.location` — `External` (only external boundaries form the domain polygon)
- `crs.properties.name` — EPSG code string

### Inflow (`inflow.geojson`)

GeoJSON FeatureCollection. Features can be:

- **Rainfall** (Polygon): `properties.type = "Rainfall"`, `properties.data` = intensity in mm/hr
- **Surface** (LineString): `properties.type = "Surface"`, `properties.data` = flow rate in m^3/s

### Friction (`friction.geojson`)

GeoJSON Polygon features with `properties.mannings` (float).

### Structure (`structure.geojson`)

GeoJSON Polygon features with `properties.method`:

- `Mannings` — high-friction zone (n=10)
- `Holes` — removed from mesh
- `Reflective` — internal reflective boundary

## Output files

| File pattern | Description |
|-------------|-------------|
| `*.sww` | ANUGA's native NetCDF format with full time-series |
| `*_depth_max.tif` | Maximum water depth (metres) at each cell |
| `*_velocity_max.tif` | Maximum flow velocity (m/s) at each cell |
| `*_depthIntegratedVelocity_max.tif` | Maximum momentum at each cell |
| `*_stage_max.tif` | Maximum water surface elevation (metres) |
| `*_<quantity>_NNNNNN.tif` | Per-timestep rasters (seconds in filename) |
| `run_anuga_*.log` | Simulation log with progress and diagnostics |
