# Structures

Structures represent building footprints or other solid obstacles within the domain. They modify both the elevation and the friction of the mesh.

## How structures work

When structures are present, two things happen during mesh setup:

1. **Elevation burn** — Building footprints are rasterised onto the DEM with a height of 5.0m added (using `gdal_rasterize`). This raises the ground surface to prevent water flowing through buildings.

2. **Friction override** — Building polygons receive a Manning's roughness coefficient of 10.0, further impeding any flow that does reach the raised elevation.

## Methods

Each structure feature has a `method` property:

| Method | Behaviour |
|--------|-----------|
| `Mannings` | Applies high friction (n=10) to the polygon |
| `Holes` | Removes the polygon from the mesh entirely |
| `Reflective` | Creates a reflective internal boundary |

!!! note
    The `Holes` and `Reflective` methods are experimental. For most use cases, the default `Mannings` method with elevation burn is recommended.
