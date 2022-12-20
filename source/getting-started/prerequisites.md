# Prerequisites
Our model needs three sets of input data in order to run:
* [Elevation](../inputs/elevation.md) data - the terrain model over which the water will flow. It is uploaded as a 
single raster file in geotiff format. If you wish to do this tutorial and don't have elevation data, you can use
[this tutorial file](https://hydrata-public.s3.us-west-2.amazonaws.com/Grand+Canyon+1m+DEM.tif) to get started.
* Inflow data - Where water enters the model. You can draw this by hand in the interface.
* Boundary data - Where water leaves the model. You can also draw this by hand in the interface.

You'll also make some choices about:
* Model resolution - how much detail do we want in the model?
* Model duration - how long should we let the water flow?

Each of these dot points can be a detailed topic on its own - however in this tutorial we will skip past the detail, 
to get started effectively. Once the model is running you will tune things where required.
