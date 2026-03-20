# Toward_fully_automated_urban_tree_inv_-_UFUG-2026
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19121499.svg)](https://doi.org/10.5281/zenodo.19121499)

Supporting materials, code, and notebooks for  
**“Toward Fully Automated Urban Tree Inventory: Integrating Mobile Lidar and Open‑Source Tools”**  
published in *Urban Forestry & Urban Greening* (2026‑02‑20).  
Article link: https://doi.org/10.1016/j.ufug.2026.129362  

This repository provides reproducible workflows and example scripts demonstrating mobile lidar
data collection, remote measurement of urban trees, and automated tree‑detection workflows using
open‑source tools. The materials here support the analysis presented in the UFUG publication and
serve as a resource for researchers and practitioners working with MLS data.

This directory contains all Python and R notebooks used to process and analyze data for the project.
Some files (e.g., `CHM.tif`, `MLS.las`) are too large to upload, but a **sample of 10 trees** is
provided in the `/data/Sample/` subdirectory. Output shapefiles, CSVs, and other results can be
found in the corresponding `/Output/` folders within each notebook workflow.

---

## 📖 Citation

If you use the code, notebooks, or workflows in this repository, please cite:

### **Repository (Zenodo DOI)**  
📌 https://doi.org/10.5281/zenodo.19121499

### **Original UFUG Journal Article**

Jones, J.J., S.C. Popescu, J. Perkins, and S. Webb, 2026. *Toward Fully Automated Urban Tree Inventory: Integrating Mobile Lidar and Open-Source Tools.* Urban Forestry & Urban Greening. https://doi.org/10.1016/j.ufug.2026.129362

Machine‑readable citation metadata is provided via the included `CITATION.cff` file.  
GitHub will automatically provide APA, BibTeX, and other formats through the  
**“Cite this repository”** button.

---

## 📝 Abstract

This repository contains supporting materials, code, and notebooks associated with the publication
“Toward Fully Automated Urban Tree Inventory: Integrating Mobile Lidar and Open‑Source Tools."
The study demonstrates methodologies for mobile lidar data collection, remote measurement of urban
trees, and automation of tree detection and validation workflows. Two open‑source R packages
(lidR and TreeLS) were evaluated, showing strong performance in estimating tree height, crown
metrics, and diameter at breast height (DBH), illustrating the viability of mobile lidar as an
efficient alternative to traditional urban tree inventory methods.

---

# 📦 Data & Samples

## Sample Mobile Lidar Scan (MLS) – LAS File

A sample of **10 trees** scanned using a mobile laser scanning system (MLS) is provided in the data folder. 
The full MLS dataset is too large to host in this repository; the sample dataset is provided so
users may test workflows and reproduce key steps in the methodology.

---

# 📚 Notebook Documentation

The following notebooks comprise the UFUG automated tree‑inventory workflow.  
Each appendix corresponds to a core step in the pipeline.

All notebooks assume the following structure:

- Notebook file resides in the project’s **main directory**
- Input files are placed in an **`_input/`** folder
- Output files will be written to an **`output/`** folder created automatically if missing

---

## **00_LAS_synpts_raster (Python)**

This notebook converts a raster into a synthetic point cloud by generating one XYZ point per raster
cell, storing the cell value as point elevation.

### Purpose  
- Create "synthetic" LAS/LAZ files from CHMs or DEMs  
- Fill canopy gaps or produce a “top‑of‑canopy LAS” for further processing  

### Workflow  
- Reads input raster  
- Writes a TXT formatted XYZ file  
- XYZ can be imported into Quick Terrain Modeler or similar tools  
- Negative Z values can optionally be set to 0 during export  

---

## **01_RMD1 (R Markdown)**

The first step toward automating tree measurements.

### Purpose  
- Preprocess input MLS/CHM data  
- Prepare structure for lidR-based analysis  

### Notes  
- Assumes the RMD file is in the main project directory  
- Input files stored under `_input/`  
- Outputs stored under `output/`

---

## **02_lidR_tt_cw (Python / R hybrid)**

This notebook performs automated tree‑top (TT) detection and crown‑width (CW) extraction using
`lidR` results as inputs.

### Inputs  
- TT points from `lidR`  
- CW polygons from `lidR`  
- Field inventory data

### Outputs  
- Improved Crown Width (ICW) calculations  
- CSV tables  
- Histograms and summary plots  

---

## **03_RMD2 (R Markdown)**

The third step in the automated tree‑measurement workflow.

### Purpose  
- Refine measurements from previous steps  
- Perform additional QA/QC on tree metrics  
- Export updated metrics for downstream processing  

---

## **04_TreeLS_inv (Python)**

Final step in the workflow using TreeLS outputs.

### Inputs  
- `TreeLS` output CSV  
- Existing tree inventory datasets  

### Outputs  
- Master inventory table (CSV + SHP)  
- Subset tables for statistical analysis  
- Scatterplots and summary figures  

### Workflow Overview  
- Join TreeLS outputs to field inventory  
- Clean and merge attributes  
- Produce final inventory products and visualizations  

---

## 🧑‍💻 Authors

- **Justinn J. Jones** — Texas A&M University  
  ORCID: https://orcid.org/0009-0007-5032-6657  

- **Sorin C. Popescu** — Texas A&M University  
  ORCID: https://orcid.org/0000-0002-8155-8801  

- **Joshuah S. Perkin** — Texas A&M University  
  ORCID: https://orcid.org/0000-0003-4928-9178  

---

## 🔗 Useful Links

- **UFUG Article DOI:** https://doi.org/10.1016/j.ufug.2026.129362  
- **Project Repository:** https://github.com/justinn-j-jones/Toward_fully_automated_urban_tree_inv_-_UFUG-2026  
- **Lab Website:** https://lasers.tamu.edu/

---

## 📝 License

This project is distributed under the **MIT License**.  
You are free to use, modify, and distribute the code.  
Please cite both the UFUG publication and the Zenodo DOI associated with this repository.

