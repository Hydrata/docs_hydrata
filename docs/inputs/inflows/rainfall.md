# Rainfall

Rainfall inflows apply a spatially uniform rainfall intensity over a polygon within the domain.

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `type` | string | Must be `"Rainfall"` |
| `data` | string or array | Intensity in mm/hr (constant or time-varying) |

## Constant rainfall

Set **data** to a single numeric value (as a string):

```
"data": "50.0"
```

This applies 50 mm/hr for the entire simulation duration.

## Time-varying rainfall

Set **data** to a JSON array of timestamp/value pairs:

```json
[
    {"timestamp": "2024-01-01T00:00:00Z", "value": 0},
    {"timestamp": "2024-01-01T00:30:00Z", "value": 50},
    {"timestamp": "2024-01-01T01:00:00Z", "value": 0}
]
```

ANUGA interpolates linearly between data points using forward-fill for missing timesteps.

## How it works

Internally, rainfall polygons are applied as `Polygonal_rate_operator` instances with a conversion factor of 1.0 x 10^-6 (converting mm/hr to m/s, the units ANUGA uses internally).
