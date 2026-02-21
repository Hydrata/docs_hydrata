# Selecting Inputs

Each scenario references a specific set of inputs. Changing inputs creates a new scenario variant without modifying the original data.

## Required inputs

Every scenario needs at minimum:

- **Elevation** — the DEM raster
- **Boundary** — domain boundary lines
- **Inflow** — at least one rainfall polygon or surface flow line

## Optional inputs

| Input | Effect if omitted |
|-------|-------------------|
| Friction | Default Manning's n (0.04) applied everywhere |
| Structures | No buildings — flat terrain only |
| Mesh Regions | Uniform mesh resolution across entire domain |
| Catchment | No hydrological routing |

## Comparing scenarios

You can create multiple scenarios within a project, each with different inputs or parameters. This is useful for:

- **Sensitivity analysis** — vary one input at a time
- **Design comparison** — test existing vs proposed conditions
- **Climate scenarios** — run different rainfall intensities
