# CATNIP Analysis on DANDI Archive

This repository contains a Jupyter notebook demonstrating how to access and analyze the CATNIP (Cell Analysis Tool for NeuroImaging Pipeline) dataset hosted on the [DANDI Archive](https://dandiarchive.org). The dataset contains deconvolved and homogeneity-corrected images of c-FOS immunostained whole mouse brains from constitutive PACAP-knockout and control PACAP-flox/flox mice, along with analysis derivatives.

## Dataset Overview

The notebook demonstrates analysis of the [draft dandiset 001362](https://dandiarchive.org/dandiset/001362), which includes:

- **22 image samples** from **13 participants** (mice)
- Deconvolved and N4 inhomogeneity-corrected light sheet microscopy images (~7 GB per stack)
- Allen Mouse Brain Atlas registration and segmentation maps
- c-FOS signal segmentation masks across multiple threshold values (4000-32000)
- Regional quantification counts of c-FOS signals
- Downsampled heatmaps for 3D volume visualization

## Notebook Features

The `CATNIP_v3.ipynb` notebook provides:

1. **CatNabber Class**: A utility class for downloading files from the DANDI Archive S3 buckets, handling download URLs and local file management

2. **Data Access**: Demonstrates how to:
   - Access the BIDS-formatted dataset following the [BIDS microscopy extension](https://bids-specification.readthedocs.io/en/stable/modality-specific-files/microscopy.html)
   - Download sample metadata (`samples.tsv`)
   - Retrieve corrected image stacks and derivatives

3. **Image Visualization**:
   - Displays 2D slices from 3D image stacks
   - Visualizes Allen Mouse Brain Atlas segmentation maps with region-specific colormaps

4. **Segmentation Analysis**:
   - Demonstrates c-FOS signal segmentation using Fast Radial Symmetry Transform across multiple threshold values
   - Shows binary masks for different threshold levels

5. **Quantification**:
   - Accesses regional cell count data stored as TSV files
   - Demonstrates heatmap visualization and 3D volume rendering using the k3d library

## Related Publication

For more details on the CATNIP analysis methodology, please refer to the published paper:

- [CATNIP Analysis Paper](https://doi.org/10.1111/jne.13286)

## Usage

The notebook is designed to run on DandiHub servers, which provide sufficient computational resources and pre-installed dependencies. Users can also run it locally, though downloading the full dataset (each image stack is ~7 GB) may take considerable time depending on internet connection speed.

### Local Setup with UV

To run the notebook locally, you can use [UV](https://github.com/astral-sh/uv) to create a virtual environment and install dependencies. UV is a fast Python package installer and resolver.

#### Prerequisites

- Python 3.11 or higher
- UV installed (see [UV installation guide](https://github.com/astral-sh/uv#installation))

#### Setup Steps

1. **Create a virtual environment and install dependencies**:

   ```bash
   uv venv
   ```

2. **Activate the virtual environment**:
   - On macOS/Linux:

     ```bash
     source .venv/bin/activate
     ```

   - On Windows:

     ```bash
     .venv\Scripts\activate
     ```

3. **Install the project and its dependencies**:

   ```bash
   uv sync
   ```

4. **Launch Jupyter Notebook**:

   ```bash
   jupyter notebook
   ```

   Or if you prefer JupyterLab:

   ```bash
   jupyter lab
   ```

5. **Open the notebook**: Navigate to `CATNIP_v3.ipynb` in the Jupyter interface.

#### Alternative: Using UV Pip Install

Alternatively, you can use `uv pip install` to install the project and its dependencies:

```bash
uv pip install -e .
```

This will install the project in editable mode along with all dependencies specified in `pyproject.toml`. Then activate the environment and launch Jupyter as described above.
