## `pantanal_climate`

This repository contains code and documentation for downloading and processing temperature and relative humidity for the Pantanal region using ERA5-Land datasets accessed through the [Climate Data Store (CDS)](https://cds.climate.copernicus.eu/). The extraction is performed using the [`KrigR`](https://github.com/ArdenB-Na/KrigR) R package, which enables spatial interpolation of ERA5-Land data at high resolution.

## Contents

- `pantanal_climate.Rmd`: R Markdown file containing code to:
  - Authenticate with the CDS API
  - Define the spatial and temporal extent
  - Download and process temperature and dew point data from ERA5-Land
  - Calculate relative humidity
  - Output and organize cleaned data
- `pantanal_climate.html`: Rendered HTML document with code.
- Recommended folder structure under the `data/` directory for reproducibility.

## Prerequisites

### 1. CDS API Access

To download data from the CDS, you must:

- [Register an account](https://www.ecmwf.int/)
- Accept the terms of use
- Follow the [CDS API setup instructions](https://cds.climate.copernicus.eu/api-how-to)

### 2. R Packages

Install the necessary R packages:

```r
if(!require("devtools")) install.packages("devtools")
if(!require("KrigR")) devtools::install_github("https://github.com/ErikKusch/KrigR")

install.packages(c("tidyverse", "sf", "terra", "slider"))
```

## Directory Structure

Ensure your working directory has the following layout:

```bash
pantanal_climate/
├── 01_get climate data.Rmd
├── 01_get climate data.html
├── pantanal_climate_data.Rproj
└── data/
    ├── raw/         # Raw data with locations and dates of collections
    ├── interim/     # Intermediate processed files from ERA5-Land
    └── processed/   # Final clean datasets
```

You can create the directory structure in R:

```r

dir.create("data/raw", recursive = TRUE)
dir.create("data/interim", recursive = TRUE)
dir.create("data/processed", recursive = TRUE)
```

## Usage

1. Clone this repository:

```bash
git clone https://github.com/pcarc1/pantanal_climate.git
cd pantanal_climate
```
2. Open RProject file (pantanal_climate_data.Rproj), then open pantanal_climate.Rmd in RStudio and run all code chunks.

3. Output files will be saved in the appropriate data/ subfolders.

## License
This project is licensed under the MIT License. See the LICENSE file for more details.

## Acknowledgements
Climate data provided by the Copernicus Climate Data Store (CDS), produced by ECMWF.
