# W-KD-GAIN

**Special Topics in Data Science** | 1st Semester | Team 3

---

## Overview

| Model | Description |
|---|---|
| **GAIN** | Generative Adversarial Imputation Networks (baseline) |
| **WGAN-FWAL** | Wasserstein GAN with Feature-Weighted Adaptive Loss |
| **KD (2-stage)** | Knowledge Distillation — Student trained from WGAN-FWAL Teacher |

---

## Architecture

> Place your architecture diagram here.
> Suggested path: `assets/architecture.png`

<!--
<img width="830" height="527" alt="그림1" src="https://github.com/user-attachments/assets/94590862-5ef7-454c-8a7d-e06bca30746d" />

-->

---

## Datasets

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

1. Download dataset from [Kaggle]([https://www.kaggle.com/competitions/criteo-display-ad-challenge/data](https://www.kaggle.com/datasets/mrkmakr/criteo-dataset))
2. Place the file at:
   ```
   data/criteoDB/train.txt, test.txt
   ```


**Expected directory structure after setup:**

```
GAIN/
├── data/
│   ├── HIGGS.csv
│   └── criteoDB/
│       └── train.txt
│       └── test.txt
├── results/
└── final_code_0610.ipynb
```

---
