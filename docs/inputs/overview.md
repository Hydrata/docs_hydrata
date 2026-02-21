# Inputs Overview

Every Hydrata model is built from a set of geospatial inputs. These are uploaded as files or drawn directly in the map interface.

## Input types

| Input | Format | Required | Description |
|-------|--------|----------|-------------|
| [Elevation](elevation.md) | GeoTIFF | Yes | Digital elevation model (DEM) |
| [Boundaries](boundaries.md) | GeoJSON (drawn) | Yes | Domain boundary lines with type tags |
| [Inflows](inflows/index.md) | GeoJSON (drawn) | Yes | Rainfall polygons or surface flow lines |
| [Mesh Regions](mesh-regions.md) | GeoJSON (drawn) | No | Areas with custom mesh resolution |
| [Friction Maps](friction-maps.md) | GeoJSON (drawn) | No | Zones with custom Manning's roughness |
| [Structures](structures.md) | GeoJSON (drawn) | No | Building footprints (burned into elevation) |

## Creating inputs

Inputs can be created in two ways:

1. **Upload** — drag and drop files (elevation rasters, GeoJSON)
2. **Draw** — use the map editing tools to create features interactively

## Coordinate systems

All inputs are stored in a projected coordinate system (UTM). When you upload a GeoTIFF, Hydrata detects its CRS and reprojects to the appropriate UTM zone. Drawn features inherit the project's CRS automatically.
