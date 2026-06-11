# W-KD-GAIN

**Special Topics in Data Science** | 1st Semester | Team 3

---

## Overview

This project benchmarks three GAN-based missing data imputation models across both small and large-scale tabular datasets under MCAR (Missing Completely At Random) conditions.

| Model | Description |
|---|---|
| **GAIN** | Generative Adversarial Imputation Networks (baseline) |
| **WGAN-FWAL** | Wasserstein GAN with Feature-Weighted Adaptive Loss |
| **KD (2-stage)** | Knowledge Distillation — Student trained from WGAN-FWAL Teacher |

**Evaluation metrics**: RMSE, MAE, AUROC, PredAUC, FLOPs, Latency, FID, Diversity

---

## Architecture

> Place your architecture diagram here.
> Suggested path: `assets/architecture.png`

<!--
![Architecture](assets/architecture.png)
-->

---

## Datasets

### Light Datasets (auto-downloaded)

Light datasets are fetched automatically from the [UCI ML Repository](https://archive.ics.uci.edu/) via `ucimlrepo` at runtime. No manual setup required.

| Dataset | UCI ID | Rows | Features | Missing Rates Tested |
|---|---|---|---|---|
| Breast Cancer | 14 | 569 | 30 | 5%, 10%, 20%, 30%, 50% |
| Spam | 94 | 4,601 | 57 | 5%, 10%, 20%, 30%, 50% |
| Credit | 222 | 1,000 | 20 | 5%, 10%, 20%, 30%, 50% |
| Wine | 109 | 6,497 | 11 | 5%, 10%, 20%, 30%, 50% |
| Student | 697 | 649 | 30 | 5%, 10%, 20%, 30%, 50% |

### Heavy Datasets (manual download required)

Heavy datasets must be downloaded manually and placed in the `data/` directory before running the heavy experiment cells.

#### HIGGS

1. Download from the [UCI ML Repository — HIGGS](https://archive.ics.uci.edu/dataset/280/higgs)
2. Extract and place the file at:
   ```
   data/HIGGS.csv
   ```
   > ~1.1 GB uncompressed. Contains 11M rows × 28 features. Only the first `max_samples` rows are loaded (default: 100,000).

#### Criteo

1. Download `train.txt` from [Kaggle — Criteo Display Advertising Challenge](https://www.kaggle.com/competitions/criteo-display-ad-challenge/data)
2. Place the file at:
   ```
   data/criteoDB/train.txt
   ```
   > ~11 GB uncompressed. Contains ~45M rows. Only 13 integer features (columns 2–14) are used; the 26 categorical hash features are excluded. Only the first `max_samples` rows are loaded (default: 100,000).

**Expected directory structure after setup:**

```
GAIN/
├── data/
│   ├── HIGGS.csv
│   └── criteoDB/
│       └── train.txt
├── results/
└── final_code_0610.ipynb
```

---

## Requirements

- Python 3.10+
- CUDA 12.x compatible GPU (recommended)

Install dependencies (run Cell 1 in the notebook, or manually):

```bash
pip install torch --index-url https://download.pytorch.org/whl/cu126
pip install pandas matplotlib seaborn scikit-learn ucimlrepo tqdm scipy
```

> If your CUDA driver version differs, replace `cu126` with the appropriate build tag (e.g. `cu124`, `cu121`). Check your driver version with `nvidia-smi`.

---

## How to Run

Open `final_code_0610.ipynb` and run all cells in order.

- **Cells 1–2**: Install packages and imports
- **Cells 3–9**: Utility, evaluation, and loader functions
- **Cells 10–14**: Model definitions (GAIN, WGAN-FWAL, KD)
- **Cells 15+**: Light DB experiment → Heavy DB experiment → result plots

Results are saved under `results/`.

---

## Results

Output files are saved to `results/final_results_<date>/`:

| File | Description |
|---|---|
| `light_final_*.csv` | Per-dataset per-missing-rate metrics (Light) |
| `heavy_final_*.csv` | Per-dataset per-missing-rate metrics (Heavy) |
| `all_results_*.csv` | Combined results |
| `efficiency_*.csv` | FLOPs, latency, parameter counts |
| `fig_*.png` | RMSE / MAE plots |
| `table_*.png` | Summary tables |
