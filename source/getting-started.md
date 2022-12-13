# Getting Started 

This tutorial will show you how to build the minimum complexity model possible. We recommend it as your first steps. Once 
this is complete, you can build out the model with more detail using the `reference` guide. 

## Prerequisites
Our model needs three sets of input data in order to run:
* [Elevation](inputs/elevation.md) data - somewhere for the water to flow over. Usually a geotiff format. If you wish to 
do this tutorial and you don't have elevation data, you can download 
* [this file](https://hydrata-public.s3.us-west-2.amazonaws.com/Grand+Canyon+1m+DEM.tif) to use.
* Inflow data - how much water goes into the model, and where? You can draw this by hand in the interface.
* Boundary data - how does water leave the model.

You'll also make some choices about:
* model resolution - how much detail do we want in the model?
* model duration - how long should we let the water flow?

Each of these dot points can be a detailed topic on its own - however in this tutorial we will use some 
example values to get you started. Once the model is running you can always tune things where required later.

```{note}
Here is a note.
```

## Create a new project
Visit <https://hydrata.com> to sign up or sign in. Once you are logged in, make sure you are on the <https://hydrata.com/>
homepage and create a new project by naming it and clicking "Create".

It will take a few seconds to create and load your project. It's ready when it looks like this:

