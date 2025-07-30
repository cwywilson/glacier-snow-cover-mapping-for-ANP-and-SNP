
# Glacier Snow Cover Mapping for Auyuittuq (ANP) and Sirmilik National Parks (SNP)

Adapted from:
[Rainey Aberle](https://github.com/RaineyAbe) and [Ellyn Enderlin](https://github.com/ellynenderlin) – Department of Geosciences, Boise State University
[![DOI](https://zenodo.org/badge/427402996.svg)](https://zenodo.org/doi/10.5281/zenodo.10616385)

## Description
This project provides an enhanced pipeline for mapping **seasonal snow-covered area (SCA)**, **accumulation area ratio (AAR)**, and **snowline altitude (SLA)** on mountain glaciers in **Auyuittuq National Park (ANP)** and **Sirmilik National Park (SNP)** using Sentinel-2 and Landsat 8/9 imagery.

It builds upon the original work of Rainey Aberle by introducing:

---

## ✨ Key Improvements in This Fork

| Feature | Description |
|--------|-------------|
| ❄️ **Snow Cover Ratio (SCR) Filter** | Filters scenes based on glacier-wide snow cover percentage to improve SLA detection accuracy |
| 📊 **Elevation-Binned SLA Extraction** | Uses DEM elevation binning to determine more robust snowline elevations |
| 🔍 **Automated Image Asset Querying** | Dynamically fetches image asset IDs using glacier AOIs and filtering criteria |
| 🌐**Max Ablation-Season SLA Detection** | Identifies SLA based on the scene with minimum SCR (usually in late summer) |

---
## 🗂️ Repository Structure

| File / Folder  in notebooks | Purpose |
|---------------|---------|
| `01_snow_classification_pipeline.ipynb` | Automatically query and download Sentinel-2/Landsat images and run ML classification |
| `02_filter_snowline_timeseries_automatic.ipynb` | Aggregate the daily SCA, SLA to time series, output the max SLA |
| `03_Plot graph.ipynb` | Plot all the graph |
---

## 🚀 Basic Workflow

1. **Query, Download, and Classify Imagery**  
   Run `01_snow_classification_pipeline.ipynb` to query Sentinel-2 and Landsat data from GEE, apply preprocessing masks, classify snow/ice/rock, and extract daily SLA using DEM binning.

2. **Aggregate SLA and SCA Time Series**  
   Use `02_filter_snowline_timeseries_automatic.ipynb` to process all classified outputs, compute daily SCR, identify maximum ablation-season SLA (minimum SCR date), and export results.

3. **Visualize Results**  
   Use `03_Plot graph.ipynb` to generate publication-ready figures of SLA trends, SCA time series, and comparisons between sites or years.

---

## 📊 Example Output

- Time series of maximum ablation-season snowline altitude (SLA) for 2016–2023
- Annual minimum SCR date used to represent peak ablation
- Elevation-binned SLA maps with ArcticDEM

![Example SLA](figures\3-SLAmax.png")

---

## 🔧 Requirements

- **Google Earth Engine** account ([sign up](https://earthengine.google.com/))
- Python packages: `geemap`, `earthengine-api`, `numpy`, `matplotlib`, `rasterio`, `xarray`, `sklearn`
- AOI shapefile (glacier polygon) in `.shp` format
- (Optional) Local DEM or it will use ArcticDEM Mosaic / NASADEM

---

## Installation
Please see the [Installation Instructions](https://github.com/RaineyAbe/snow-cover-mapping/blob/main/docs/installation_instructions.md).


