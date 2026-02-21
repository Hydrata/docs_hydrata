# Elevation

The elevation raster (DEM) is the foundation of every Hydrata model. It defines the terrain surface over which water flows.

## Requirements

- **Format:** GeoTIFF (.tif)
- **CRS:** Any projected coordinate system (Hydrata reprojects to UTM automatically)
- **Resolution:** 1m to 50m typical. Finer resolution = more triangles = longer runtime.
- **Coverage:** Must cover the entire domain boundary

## Uploading

1. Open **Inputs** in the project sidebar
2. Click the upload icon and select your `.tif` file
3. Processing takes 3-5 minutes depending on file size

After upload, Hydrata creates:

- A colour-coded elevation visualisation layer
- A hillshade layer for context
- Default empty Inflow and Boundary layers

## Sources of elevation data

| Source | Coverage | Resolution | License |
|--------|----------|------------|---------|
| [Geoscience Australia ELVIS](https://elevation.fsdf.org.au/) | Australia | 1m - 5m | CC BY 4.0 |
| [USGS 3DEP](https://www.usgs.gov/3d-elevation-program) | USA | 1m - 10m | Public domain |
| [OpenTopography](https://opentopography.org/) | Global | Varies | Varies |

## How elevation is used

ANUGA uses the elevation raster to set the `elevation` quantity on the computational mesh. During mesh generation, elevation values are interpolated from the raster to mesh vertices or centroids.

If structures (buildings) are present, their footprints are "burned" into the elevation by adding a height offset (default: 5m) before mesh generation.
