# Prerequisites

To build a model in Hydrata you need three input data sets:

| Input | Required | Format | Notes |
|-------|----------|--------|-------|
| **Elevation data** | Yes | GeoTIFF (.tif) | Must be in a projected coordinate system |
| **Inflow data** | Yes | Drawn in interface | Rainfall polygons or surface flow lines |
| **Boundary data** | Yes | Drawn in interface | External boundary lines around the domain |

You will also need to decide on:

- **Model resolution** — the mesh triangle size in metres
- **Duration** — how long the simulation should run (in seconds)

## Tutorial elevation data

For this tutorial, you can download a sample elevation file:

[Download tutorial DEM (Grand Canyon 1m)](https://hydrata-geoserver.s3-us-west-2.amazonaws.com/tutorial/tutorial_dem.tif){ .md-button }

This is a 1m resolution GeoTIFF covering a small area suitable for a quick test run.
