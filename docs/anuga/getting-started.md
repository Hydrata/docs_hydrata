# Standalone Usage

You can run ANUGA simulations outside of the Hydrata web platform using the `run_anuga` Python package. This is useful for:

- Local development and testing
- Running on your own HPC infrastructure
- Automating batch simulations
- CI/CD pipelines

## Installation

### Prerequisites

- Python 3.10+
- GDAL system libraries (`gdal-bin`, `libgdal-dev`)
- ANUGA (for running simulations)

### Install run_anuga

```bash
# Clone the repository
git clone https://github.com/Hydrata/run_anuga.git
cd run_anuga

# Install in editable mode
pip install -e .

# With ANUGA support (required to actually run simulations)
pip install -e ".[anuga]"

# With development tools (pytest, ruff)
pip install -e ".[dev]"
```

## Running a simulation

### Using the CLI

```bash
run-anuga --package_dir /path/to/package/
```

With Hydrata server authentication (for progress reporting):

```bash
run-anuga user@example.com password --package_dir /path/to/package/
```

### Using the Python API

```python
from run_anuga.run import run_sim

run_sim("/path/to/package")
```

### Using MPI (parallel execution)

For large domains, run across multiple CPU cores:

```bash
mpirun -np 4 python -m run_anuga.run --package_dir /path/to/package/
```

## Running the example

The repository includes an example package:

```bash
cd run_anuga
run-anuga --package_dir examples/australian_floodplain/
```

!!! note
    The example includes a 200x200m DEM clipped from 1m elevation data sourced from the [Geoscience Australia ELVIS portal](https://elevation.fsdf.org.au/) (CC BY 4.0). See `examples/australian_floodplain/LICENSE_DATA.md` for attribution.

## Inspecting outputs

After a run completes, outputs are in the `outputs_*` directory:

```bash
ls outputs_1_1_1/
# run_1_1_1.sww
# run_1_1_1_depth_max.tif
# run_1_1_1_velocity_max.tif
# run_1_1_1_depthIntegratedVelocity_max.tif
# run_1_1_1_stage_max.tif
# run_anuga_1.log
```

Open the GeoTIFF files in QGIS or any GIS software to visualise results.

## Validating a package

Before running, you can validate a scenario.json against the schema:

```python
from run_anuga.schema import validate_scenario
import json

with open("scenario.json") as f:
    config = json.load(f)

validate_scenario(config)
print("Valid!")
```

## Parsing inputs without running

To inspect a package without executing a simulation:

```python
from run_anuga.run_utils import setup_input_data

input_data = setup_input_data("/path/to/package")

print(f"Project: {input_data['scenario_config']['project']}")
print(f"Duration: {input_data['scenario_config']['duration']}s")
print(f"EPSG: {input_data['scenario_config']['epsg']}")
print(f"Mesh file: {input_data['mesh_filepath']}")
```
