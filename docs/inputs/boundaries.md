# Boundaries

Boundary lines define the outer extent of your simulation domain. Each line segment has a **type** that controls how water behaves at that edge during the simulation.

## Boundary types

| Type | ANUGA class | Behaviour |
|------|-------------|-----------|
| **Reflective** | `Reflective_boundary` | Water reflects off the edge (solid wall) |
| **Transmissive** | `Transmissive_boundary` | Water passes freely through |
| **Dirichlet** | `Dirichlet_boundary` | Fixed water level (stage, momentum = 0) |

## Drawing boundaries

Boundaries are drawn as **LineString** features in the map interface. Together they must form a closed polygon around the domain.

1. Select the Boundaries layer
2. Enter edit mode (pencil icon)
3. Draw each boundary segment
4. Assign the boundary type via the properties panel
5. Save changes

!!! warning
    All boundary segments must connect end-to-end to form a closed polygon. Gaps between segments will cause mesh generation to fail.

## How boundaries work internally

Hydrata sorts boundary line segments in clockwise order around the domain centroid, then joins them into a single closed polygon. This polygon defines the ANUGA mesh extent. Each segment's type is preserved as a boundary tag, so ANUGA applies the correct boundary condition to each edge.
