# Inflows

Inflows add water to the simulation domain. Hydrata supports two types:

| Type | Geometry | Description |
|------|----------|-------------|
| [Rainfall](rainfall.md) | Polygon | Applies rainfall intensity (mm/hr) uniformly over an area |
| [Surface Flow](surface-flow.md) | LineString | Injects a volumetric flow rate (m^3/s) along a line |

Inflow features are drawn in the map interface or uploaded as GeoJSON. Each feature specifies a **type** and a **data** value.
