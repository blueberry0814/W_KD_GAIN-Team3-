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

<img width="830" height="527" alt="그림1" src="https://github.com/user-attachments/assets/8819ee17-0ca4-4ab6-9698-b48258b88771" />


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

#### Criteo

1. Download dataset from [Kaggle]([https://www.kaggle.com/competitions/criteo-display-ad-challenge/data](https://www.kaggle.com/datasets/mrkmakr/criteo-dataset)
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
