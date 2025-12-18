# Python scripts for seasonal HLI, welfare categories, and exposure metrics
This repository provides the Python scripts used to process NEX-GDDP-CMIP6 climate model outputs and compute the Heat Load Index (HLI) on a 0.25° global grid under historical and future climate scenarios. The workflow builds an equal-weighted multi-model ensemble (MME) from 27 CMIP6 GCMs, classifies thermal welfare categories, and quantifies the land area exposed to extreme heat stress at global and national scales.

Outputs include CF-compliant NetCDF files, publication-ready figures, and tabular summaries (Excel).

# Repository contents
Core seasonal HLI and welfare-category scripts

- CliNO_HLI_Seasonal_MME_Public.py
Computes the baseline (1985–2014) seasonal climatology of HLI from 27 CMIP6 GCMs, producing an equal-weighted multi-model ensemble (MME) on a 0.25° × 0.25° global grid.

- Projections_HLI_Seasonal_MME_Public.py
Computes seasonal HLI climatologies for each SSP scenario (e.g. SSP1-2.6, SSP2-4.5, SSP3-7.0, SSP5-8.5) and each 25-year projection window (2026–2050, 2051–2075, 2076–2100), using the same 27-model MME framework.

- CliNo_Seasonal_WelfareCategories.py
Classifies baseline (1985–2014) seasonal HLI fields into welfare categories using predefined thresholds, and generates global welfare-category maps (e.g. “No stress”, “Mild”, “Moderate”, “Severe”, “Extreme”).

- Projections_Seasonal_WelfareCategories.py
Applies the same welfare-category classification to the SSP-specific seasonal HLI climatologies, producing global maps for each scenario and 25-year window.

# Global and country-level exposure scripts
- Uses the CliNo and SSP seasonal HLI NetCDF files to compute, for each season, SSP and time window, the fraction of global land area falling in:
Severe heat stress: 86 < HLI ≤ 96
Extreme heat stress: HLI > 96
- Derives baseline shares and future shares, then calculates absolute percentage-point (pp) changes relative to CliNo
- Outputs a CSV/Excel table (HLI_global_severe_extreme_area_changes.xlsx) summarising:
Baseline and future global land-area fractions (%)
pp changes in severe and extreme categories
- Intended use: reproduce the global statistics reported in the manuscript (e.g. values in Table 1)ù
  - - HLI_country_extreme_area_delta_maps.py
    - Uses a country shapefile (e.g. Natural Earth, EPSG:4326) and the CliNo/SSP seasonal HLI NetCDF files to:
    - Rasterise national boundaries onto the 0.25° grid
    - Compute, for each country and season, the percentage of national land area with HLI > 96 (extreme heat stress) in CliNo and in each SSP/time window
    - Derive percentage-point changes relative to the baseline (CliNo)
    - Produces multi-panel maps (PNG/TIFF) showing seasonal country-level changes in the fraction of land exposed to extreme heat stress for all SSPs and for a selected 25-year window (e.g. HLI_severe_area_delta_2026_2050.png, …2051_2075.png, … n     2076_2100.png).
    - Intended use: support country-level interpretation and creation of supplementary figures
   
# Typical workflow

1. Baseline seasonal HLI
Run CliNO_HLI_Seasonal_MME_Public.py to generate 1985–2014 HLI seasonal climatologies (MME) in NetCDF format.

2. Future seasonal HLI
Run Projections_HLI_Seasonal_MME_Public.py for each SSP and 25-year window of interest (2026–2050, 2051–2075, 2076–2100).

3. Baseline welfare categories
Run CliNo_Seasonal_WelfareCategories.py to classify CliNo HLI fields and generate global welfare-category maps.

4. Projected welfare categories
Run Projections_Seasonal_WelfareCategories.py to generate welfare-category maps for each SSP and time window.
5. Global exposure metrics (severe/extreme area)
Run HLI_global_severe_extreme_area_changes.py to compute global land-area fractions in severe and extreme categories and their pp changes vs CliNo (outputs: Excel table).

6. Country-level exposure maps
Run HLI_country_extreme_area_delta_maps.py for each projection window of interest to produce country-level maps of pp changes in national land area with HLI > 96 (outputs: PNG/TIFF figures).


# Input data

Climate variables from NEX-GDDP-CMIP6 on a 0.25° global grid:
Near-surface air temperature (tas)
Relative humidity (hurs)
Surface downwelling shortwave radiation (rsds)
Near-surface wind speed (sfcWind)
A global country boundaries shapefile in WGS84 latitude–longitude (e.g. Natural Earth 1:110m, EPSG:4326) for land masking and country-level aggregation.
