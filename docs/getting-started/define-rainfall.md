# Define Rainfall

Rainfall is the most common inflow type. It applies a rainfall intensity (in mm/hr) uniformly over a polygon within your domain.

## Adding rainfall

1. Select the **Inflows** layer
2. Click the pencil icon to enter edit mode
3. Click **Add New Feature**
4. Draw a polygon covering the area where rainfall should be applied
5. Set the **Type** to `Rainfall`
6. Enter the rainfall intensity in the **Data** field (e.g. `50` for 50 mm/hr)
7. Click **Save Changes**

!!! tip
    For a simple uniform rainfall event, draw a single polygon that covers the entire domain boundary. The rainfall intensity will be applied uniformly within the polygon.

## Time-varying rainfall

For time-varying rainfall, the **Data** field accepts a JSON array of timestamp/value pairs:

```json
[
    {"timestamp": "2024-01-01T00:00:00Z", "value": 0},
    {"timestamp": "2024-01-01T00:10:00Z", "value": 25},
    {"timestamp": "2024-01-01T00:30:00Z", "value": 50},
    {"timestamp": "2024-01-01T01:00:00Z", "value": 10},
    {"timestamp": "2024-01-01T01:30:00Z", "value": 0}
]
```

Values are in mm/hr. ANUGA interpolates linearly between data points.

## Next steps

With elevation, boundaries, and rainfall defined, you're ready to [configure and run a scenario](../running-scenarios/configuring-runs.md).
