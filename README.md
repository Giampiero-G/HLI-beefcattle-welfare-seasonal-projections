# HLI-beefcattle-welfare-seasonal-projections
Python scripts to compute seasonal Heat Load Index (HLI) on a 0.25° global grid from NEX-GDDP-CMIP6 (tas, hurs, rsds, sfcWind), build an equal-weighted 27-GCM ensemble, and render welfare category maps for CliNO (1985-2014) and CMIP6 projections (2026-2100). Outputs: CF-compliant NetCDF and publication-ready figures.

Python scripts for seasonal HLI baseline, projections, and welfare categories

This repository provides the Python scripts used to process climate model outputs and compute the Heat Load Index (HLI) under historical and future climate scenarios (CMIP6).

Repository contents

CliNO_HLI_Seasonal_MME_Public.py Computes the baseline (1985–2014) seasonal climatology of HLI from 27 CMIP6 GCMs, producing a multi-model ensemble (MME).

Projections_HLI_Seasonal_MME_Public.py Computes seasonal HLI climatology for each climate scenario (SSP) and 25-year projection window (e.g., 2026–2050, 2051–2075, 2076–2100), using the same ensemble approach.

CliNo_Seasonal_WelfareCategories.py Generates welfare categories maps for the baseline (1985–2014) seasonal climatology.

Projections_Seasonal_WelfareCategories.py Generates welfare categories maps for each climate scenario (SSP) and 25-year projection window .


Usage

Each script is intended to be run separately. Typical workflow:

Run CliNO_HLI_Seasonal_MME_Public.py to create the baseline climatology files.

Run Projections_HLI_Seasonal_MME_Public.py for each scenario and time window.

Run CliNo_Seasonal_WelfareCategories.py to generate CliNo seasonal welfare categories map.

Run Projections_Seasonal_WelfareCategories.py to generate seasonal welfare categories map for each scenario and ofr the 25-year window selected (e.g., 2026–2050, 2051–2075, 2076–2100) .

The scripts assume CMIP6 NetCDF input files structured by model, scenario, and time period.

Requirements

Python 3.8+

Libraries: numpy, netCDF4, matplotlib, cartopy, geopandas, rasterio
