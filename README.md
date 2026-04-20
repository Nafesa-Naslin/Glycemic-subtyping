# Glycemic subtyping from CGM features (T2DM)

This repository contains code to discover **glycemic subtypes** from continuous glucose monitoring (CGM) data using engineered features and unsupervised clustering, followed by clinical interpretation and validation.

## What’s in this repo

- `scripts/` — analysis scripts organized by pipeline step  
- `docs/` — plain-language documentation for each script + pipeline run order  
- `manuscript/` — conference materials + manuscript drafts (optional)  
- `data/` — **not tracked by default** (see `data/README.md`)  
- `results/` — outputs (figures tracked; CSV tables ignored by default)

## Key methods implemented

- Feature engineering: mean glucose, SD, MAGE, TIR/TAR/TBR, CV
- Clustering:
  - K-means (baseline and 7-feature solution)
  - Hierarchical clustering (Ward linkage)
- Validation:
  - Silhouette score (cluster separation)
  - Bootstrap stability via Adjusted Rand Index (ARI)
  - ANOVA + Tukey HSD for Age/BMI/HbA1c
  - Chi-square tests for complication association
- Interpretation:
  - UMAP visualization
  - SHAP feature importance for hierarchical clusters

## Quickstart

### 1) Create a Python environment
```bash
python -m venv .venv
source .venv/bin/activate      # macOS/Linux
# .venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

### 2) Place your local data
See `data/README.md` for expected files and column names.

### 3) Run the pipeline
Start here:
- `docs/PIPELINE.md`

## Reproducibility notes

- K-means scripts set `random_state=42` for reproducibility.
- Bootstrap stability scripts use fixed seeds and iterate multiple resamples.

## Citation
See `CITATION.cff`.

## License
MIT (see `LICENSE`).
