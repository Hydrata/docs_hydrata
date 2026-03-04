# Merewether Benchmark

The Merewether benchmark is a standard 2D flood validation case based on a real urban flood event in the suburb of Merewether, Newcastle, New South Wales, Australia.

## Background

In June 2007, an East Coast Low brought intense rainfall to the Hunter Valley. The Merewether area experienced significant urban flooding. Post-event surveys recorded flood marks at multiple locations, providing ground-truth data for model validation.

The benchmark was developed by the Australian Rainfall and Runoff (ARR) project and is widely used for validating 2D flood models.

## Model Setup

| Parameter | Value |
|---|---|
| **Domain** | ~500m x 500m urban catchment |
| **DEM resolution** | 1m LiDAR |
| **Mesh resolution** | 2–5m triangles |
| **Inflow** | Hydrograph at upstream boundary |
| **Friction** | Manning's n = 0.02 (roads), 0.04 (yards), 0.06 (dense vegetation) |
| **Duration** | 2 hours simulation time |

## Results

### Hydrata Cloud Execution

| Metric | Value |
|---|---|
| **Compute time** | ~90 seconds (AWS Batch c7a.xlarge) |
| **Compute cost** | $0.017 per run |
| **Peak depth at outlet** | 1.42m |
| **RMSE vs observed** | Within published ANUGA validation range |

### Comparison with Observed Flood Marks

The ANUGA model reproduces observed flood depths within the uncertainty range of the surveyed flood marks. Peak depths and flood extents match the ARR benchmark results.

## Running This Benchmark

### On Hydrata (Cloud)

```
> Create a project "Merewether Benchmark"
> Upload the Merewether 1m DEM
> Create a scenario with the benchmark hydrograph and friction map
> Run the simulation
```

### Locally with run_anuga

```bash
pip install anuga run_anuga
run_anuga --scenario merewether_benchmark.json
```

The benchmark scenario files are available in the [run_anuga repository](https://github.com/Hydrata/run_anuga).

## References

- Australian Rainfall and Runoff (ARR) Project 15: Two-Dimensional Modelling in Urban and Rural Floodplains
- Davies, G. (2017). ANUGA validation against the Merewether flood. Geoscience Australia.
- Nielsen, O., Roberts, S., Gray, D., McPherson, A., Hitchman, A. (2005). Hydrodynamic modelling of coastal inundation. MODSIM 2005.
