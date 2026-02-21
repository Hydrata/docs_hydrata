# Mesh Regions

Mesh regions let you vary the computational mesh resolution across your domain. Use finer resolution in areas of interest and coarser resolution elsewhere to balance accuracy and runtime.

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `resolution` | number | Target triangle edge length in metres |

## How they work

Each mesh region is a polygon with a target resolution. During mesh generation:

- **With `simplify_mesh` enabled** (mesher): Regions are processed as separate elevation clips at their target resolution, then merged into a combined mesh.
- **Without `simplify_mesh`** (ANUGA native): Regions are passed as interior regions to `create_mesh_from_regions`, constraining the maximum triangle area within each polygon.

## Tips

- Use a coarse base resolution (e.g. 20m) for the full domain
- Add mesh regions at 2-5m for areas where you need detailed results
- Finer resolution significantly increases triangle count and runtime
