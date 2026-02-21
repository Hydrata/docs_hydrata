# Upload Elevation Data

1. Open the **Inputs** menu
2. Click the upload icon ![Upload icon](../assets/images/icon-upload.png){ width=20 }
3. Drag and drop your `.tif` file, or click to select it
4. Enter a description and confirm

![Upload elevation](../assets/images/getting-started-upload-elevation.gif)

Hydrata automatically detects the location and projection of your GeoTIFF and reprojects it to UTM. Processing takes 3-5 minutes — you can continue working while it runs in the background.

## What gets created

Once processing completes, several layers appear in the layer panel:

- **Elevation** — colour-coded visualisation of your raster
- **Hillshade** — shaded relief layer
- **Inflows** — empty inflow layer (ready for rainfall data)
- **Boundaries** — empty boundary layer (ready for domain boundaries)

![Layers created](../assets/images/getting-started-layers-created.png)

!!! info
    The elevation raster is reprojected to a Universal Transverse Mercator (UTM) zone. All coordinates within ANUGA use this projected system in metres.
