# DataAnalysisVisualization - Affordable Liveability Index (ALI)

This repository contains a reproducible workflow for building a **composite indicator** that compares countries on **Affordable Liveability** in **2022**.

---

## What is ALI?

**ALI (Affordable Liveability Index)** is a country-level composite score designed to compare overall living conditions **relative to affordability pressures**.

- **Unit of analysis:** countries/territories  
- **Reference year:** 2022  
- **Output:** a single score (**ALI**) plus sub-scores (“pillars”) and ranks

### Pillars
ALI is built from three sub-indices (pillars):

1. **CP - Cost Pressure** *(higher = more affordable in this project’s scoring)*
2. **EO - Economic Opportunity** *(higher = better opportunity)*
3. **QOL - Quality of Life** *(higher = better living conditions)*

The final ALI score is formed by aggregating these pillars (baseline: equal weights).

See `report/index_definition.md` for the conceptual model and baseline weighting/normalisation assumptions.

---

## How to run

### 1) Create and activate a Python environment

Using `venv`:

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
```

### 2) Install dependencies

```bash
pip install -U pandas numpy matplotlib seaborn scikit-learn plotly kaleido
```

> `kaleido` is required for Plotly PNG export via `fig.write_image(...)`.

### 3) Provide HDI comparison data

Place an HDI dataset at:

- `data/raw/hdi.csv`

Minimum required columns:
- `iso3`
- `hdi_2022`

Optional columns (used if present):
- `country`
- `tier_hdi`
- `hdi_rank`

### 4) Run notebooks in order

1. `01_data_collection_wdi.ipynb` - download/collect indicators (WDI) for 2022  
2. `02_clean_impute.ipynb` - clean data and impute missing values  
3. `03_multivariate_and_clustering.ipynb` - correlation checks + k-means clustering  
4. `04_index_construction.ipynb` - normalisation + pillar scores + ALI aggregation + ranking  
5. `05_visualisations_map_and_comparison.ipynb` - maps/figures + ALI vs HDI comparison  

---

## Key outputs

### Processed data
- `data/processed/ali_2022_index.csv` - ALI + pillars + ranks (2022)
- `data/processed/ali_hdi_comparison.csv` - ALI joined to HDI (where available)

### Figures
- `outputs/figures/ali_map.png` - ALI choropleth map
- `outputs/figures/cp_map.png` - Cost Pressure pillar map
- `outputs/figures/eo_map.png` - Economic Opportunity pillar map
- `outputs/figures/qol_map.png` - Quality of Life pillar map
- `outputs/figures/clusters_map.png` - k-means clusters (k=4)
- `outputs/figures/ali_bottom20.png` - bottom 20 countries by ALI
- `outputs/figures/ali_vs_hdi.png` - scatter plot comparing ALI vs HDI

### Interactive map
- `outputs/ali_2022_map.html`
