# Configuring Runs

A scenario brings together your inputs and simulation parameters into a runnable configuration.

## Scenario settings

| Setting | Description | Default |
|---------|-------------|---------|
| **Duration** | Simulation time in seconds | Required |
| **Resolution** | Base mesh triangle size in metres | Required |
| **Simplify Mesh** | Use adaptive mesher for mesh generation | false |
| **Max RMSE Tolerance** | Error tolerance for adaptive mesher | 1.0 |
| **Model Start** | Simulation start time (for time-varying inflows) | 1970-01-01 |

## How to run

1. Open a project and navigate to the **Scenarios** panel
2. Select or create a scenario
3. Choose the inputs (elevation, boundary, inflow, etc.)
4. Set duration and resolution
5. Click **Run**

The simulation is queued and executed on Hydrata's compute infrastructure. Progress is reported as a percentage in the scenario status.

## Outputs

After a successful run, the following outputs are generated:

| Output | Format | Description |
|--------|--------|-------------|
| SWW file | NetCDF | Full time-series of depth, velocity, stage |
| Depth max | GeoTIFF | Maximum water depth at each point |
| Velocity max | GeoTIFF | Maximum flow velocity at each point |
| Depth-integrated velocity max | GeoTIFF | Maximum momentum at each point |
| Stage max | GeoTIFF | Maximum water surface elevation |

Outputs are viewable in the map interface or downloadable for use in GIS software.
