# Define Boundaries

Boundaries define the extent of your simulation domain. Each boundary line segment has a type that controls how water behaves at the edge.

## Drawing boundaries

1. Select the **Boundaries** layer
2. Click the pencil icon ![Edit](../assets/images/icon-pencil.png){ width=20 } to enter edit mode
3. Click **Add New Feature** ![Add](../assets/images/icon-add-new-feature.png){ width=20 }
4. Draw a polygon around your domain on the map
5. Click **Save Changes**

![Drawing boundaries](../assets/images/getting-started-rename-layers.gif)

## Boundary types

| Type | Behaviour |
|------|-----------|
| **Reflective** | Water is reflected back — acts as a solid wall |
| **Transmissive** | Water passes freely through the boundary |
| **Dirichlet** | Maintains a fixed water level (stage = 0) |

!!! tip
    For most models, use **Transmissive** boundaries on the downstream edge where water should flow out, and **Reflective** boundaries on the sides and upstream.
