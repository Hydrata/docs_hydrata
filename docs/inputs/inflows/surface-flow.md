# Surface Flow

Surface flow inflows inject water along a line at a specified volumetric flow rate.

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `type` | string | Must be `"Surface"` |
| `data` | string | Flow rate in m^3/s |

## Usage

Surface inflows are drawn as **LineString** features. The flow rate is distributed along the line.

```
"data": "0.5"
```

This injects 0.5 m^3/s along the line for the entire simulation.

## How it works

Internally, surface inflow lines are applied as ANUGA `Inlet_operator` instances. The line must be within the domain boundary — lines outside the boundary are silently ignored.

!!! tip
    Surface inflows are useful for modelling pipe outfalls, creek inflows, or other point/line sources of water entering the domain.
