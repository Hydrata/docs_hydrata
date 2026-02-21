# Friction Maps

Friction maps define zones with custom Manning's roughness coefficients. Areas not covered by a friction polygon use the default value (0.04).

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `mannings` | number | Manning's roughness coefficient for this zone |

## Common Manning's n values

| Surface | Manning's n |
|---------|-------------|
| Smooth concrete | 0.012 |
| Short grass | 0.025 |
| Dense grass / crops | 0.035 |
| Light brush | 0.050 |
| Dense brush | 0.100 |
| Buildings (default) | 10.0 |

## How it works

Friction polygons are combined into a composite function using ANUGA's `composite_quantity_setting_function`. The function evaluates polygons in order, with an `['All', 0.04]` catchall applied last for any uncovered areas.

Building footprints (from the Structures input) automatically receive a Manning's n of 10.0, effectively blocking flow through them.
