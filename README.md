# BREAST - Breast cancer Expression Analysis Software Tool  
**A Shiny toolkit combining a single-cell breast tumor atlas viewer with a T-47D ChIP-Atlas browser.**

BREAST is an R/Shiny application that provides:
1) **Interactive exploration of the Wu et al. breast cancer single-cell atlas** (PMID: 34493872) via a Seurat object, with publication-ready plots and an **in-app differential expression workflow (Gene+ vs Gene−)**.  
2) **A T-47D ChIP Viewer** to visualize **ChIP-Atlas peaks around any HGNC gene**, optionally overlaid with **ENCODE cCREs**.

---

## Features

### 1) Single-cell module (BREAST)
Using the provided `seurat_obj.rds`, you can:

- **Subset by tumor subtype** (e.g., ER+, HER2+, TNBC; depends on metadata column `subtype`)
- **Visualize gene expression** for any gene in the object:
  - **FeaturePlot** on a UMAP
  - **Jitter plot** by major cell type
- **Explore major and minor structure**
  - A global UMAP of the selected subtype (recomputed in-app)
  - Optional **reclustering within a selected major cell type** (minor clusters)
- **Run differential expression (FindMarkers) without writing new code**
  - Choose a gene, define a threshold, and compare **Gene+ vs Gene−**
  - Scope can be:
    - All cells within the selected subtype, or
    - Only cells from a selected **major cell type**
  - Outputs:
    - A **downloadable CSV** of DE results
    - A quick **volcano plot**
    - An interactive **results table**

> This Gene+ vs Gene− comparison is useful to generate hypotheses on pathways and programs associated with expression of a gene of interest inside a defined cellular compartment (e.g., “cancer epithelial cells expressing GABBR1 vs not expressing it”).

### 2) T-47D ChIP Viewer
With `T47D_formatted_50.bed` (ChIP-Atlas export) and optional `ENCFF389ZVZ_cCREs.bigBed`:

- Enter a **gene symbol** (HGNC; ENSG also supported if present)
- Define a **flanking window (bp)**
- Display peaks as an interactive **plotly scatter**
  - Filter by factor, minimum score, point size
  - **Click on any point to open the SRX** entry on ChIP-Atlas
- Optionally overlay **ENCODE cCREs** (PLS/pELS/dELS/CTCF-only/DNase-H3K4me3)
- Export a **static PDF** version of the plot

---

## Requirements

- **R** (recommended ≥ 4.2)
- Packages listed in the script (Shiny, Seurat, plotly, EnsDb.Hsapiens.v86, rtracklayer, DT, etc.)
- Input files placed in the **same folder** as your `app.R`:
  - **Mandatory (Single-cell):**
    - `seurat_obj.rds`
  - **Mandatory (ChIP viewer):**
    - `T47D_formatted_50.bed`
    - `ENCFF389ZVZ_cCREs.bigBed`

---

## Installation / Setup

1. Create a new folder (project directory), then place inside:
   - `app.R` (the script)
   - `seurat_obj.rds`
   - `T47D_formatted_50.bed`
   - `ENCFF389ZVZ_cCREs.bigBed`

2. In RStudio:

set you working directory either with session -> set working directory -> choose directory
   ```r
   setwd("path/to/your/project_folder")
```

3. Install the packages one time:
  ```r
   
install.packages(c(
  "shiny","bslib","Seurat","ggplot2","RColorBrewer","Matrix","plotly",
  "dplyr","readr","tibble","htmlwidgets","AnnotationFilter","GenomicRanges",
  "IRanges","rtracklayer","stringr","tidyr","DT"
))
# Bioconductor packages
if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")
BiocManager::install(c("EnsDb.Hsapiens.v86"))
```
4. Press Run app




## Credits 

Breast cancer atlas:
Wu, S. Z., Al-Eryani, G., Roden, D. L., Junankar, S., Harvey, K., Andersson, A., ... & Swarbrick, A. (2021). A single-cell and spatially resolved atlas of human breast cancers. Nature genetics, 53(9), 1334-1347.

ChIP-Atlas:
Zou, Z., Ohta, T., & Oki, S. (2024). ChIP-Atlas 3.0: a data-mining suite to explore chromosome architecture together with large-scale regulome data. Nucleic Acids Research, 52(W1), W45-W53.
licensed under CC-BY 4.0 

ENCODE cCREs: ENCFF389ZVZ





