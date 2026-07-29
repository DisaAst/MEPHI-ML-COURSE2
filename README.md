# Machine Learning for Toxicological Analysis

An applied machine learning study of biological activity and toxicity indicators for chemical compounds.

The project develops regression and classification pipelines for three targets:

- **CC50** — half-maximal cytotoxic concentration;
- **IC50** — half-maximal inhibitory concentration;
- **SI** — selectivity index.

The work covers exploratory analysis, data cleaning, feature selection, model comparison, cross-validation, and interpretation of the strongest results.

## Dataset

- 1,001 samples
- 214 molecular descriptors and target columns
- 36 missing values across 12 columns
- 32 exact duplicates removed during preprocessing
- strongly skewed target distributions handled with logarithmic transformations

## Tasks

### Regression

- Predict continuous CC50 values
- Predict continuous IC50 values
- Predict continuous SI values

### Classification

- CC50 above the median
- IC50 above the median
- SI above the median
- SI above a fixed threshold of 8

## Model comparison

The experiments compare linear baselines, Random Forest, XGBoost, and related classical ML approaches using held-out evaluation and cross-validation.

### Selected results

| Task | Best model | Main result |
| --- | --- | ---: |
| CC50 regression | Random Forest | R² = 0.418 |
| IC50 regression | Random Forest | R² = 0.445 |
| SI regression | Random Forest | R² = 0.382 |
| CC50 classification | Random Forest | ROC-AUC = 0.876, F1 = 0.871 |
| IC50 classification | Random Forest | ROC-AUC ≈ 0.891, F1 ≈ 0.886 |
| SI above median | Random Forest | ROC-AUC = 0.923, F1 = 0.918 |
| SI above 8 | Random Forest | ROC-AUC ≈ 0.908, F1 ≈ 0.902 |

Classification was substantially more reliable than direct regression for this dataset. The strongest result was SI-above-median classification with a ROC-AUC of 0.923.

## Workflow

```text
Raw molecular descriptors
        │
        ▼
Missing-value and duplicate handling
        │
        ▼
Distribution and correlation analysis
        │
        ▼
Feature filtering and target transforms
        │
        ▼
Model training and cross-validation
        │
        ▼
Held-out evaluation and comparison
```

## Technology stack

- Python
- pandas and NumPy
- scikit-learn
- XGBoost
- Matplotlib and Seaborn
- Jupyter Notebook

## Repository contents

The notebooks are organized around EDA, three regression tasks, and four classification tasks. Generated figures are stored in the `images/` directory.

## Scope

This repository is an academic ML project. The reported metrics apply to the included dataset and evaluation setup; they are not a substitute for laboratory validation or clinical assessment.
