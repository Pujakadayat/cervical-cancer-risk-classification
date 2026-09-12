# Cervical Cancer Risk Classification

Predicting cervical cancer risk from patient-level clinical and behavioral risk factors, using the UCI Cervical Cancer (Risk Factors) dataset. Part 1 of a two-part project connecting individual-level risk prediction (this notebook) with population-level screening access in Nepal (Part 2, in progress).

## Dataset

- **Source:** [UCI Machine Learning Repository — Cervical Cancer (Risk Factors)](https://archive.ics.uci.edu/dataset/383/cervical+cancer+risk+factors)
- 858 patient records, 36 attributes covering demographics, habits (smoking), reproductive/sexual history, STD history, and 4 diagnostic test outcomes (Hinselmann, Schiller, Citology, Biopsy)
- **Target variable:** `Biopsy` (0 = negative, 1 = positive) — the most clinically definitive of the four test outcomes
- Licensed CC BY 4.0

## Approach

1. **Preprocessing** — converted mixed-type columns to numeric, imputed missing values (mode for binary columns, mean for continuous columns), computed after the train/test split to avoid leakage
2. **EDA** — class imbalance check, age distribution by diagnosis, feature correlation heatmap, risk factor prevalence comparison (positive vs. negative cases)
3. **Modeling** — Logistic Regression and Random Forest, both with `class_weight="balanced"` to address severe class imbalance (~15:1 negative:positive)
4. **Evaluation** — precision/recall/F1, ROC-AUC, 5-fold cross-validation, and threshold tuning (favoring recall, since missing a true positive is the costlier error in a screening context)


## Results

| Model | ROC-AUC | Precision | Recall | F1 |
|---|---|---|---|---|
| Logistic Regression | 1.00 | 1.00 | 1.00 | 1.00 |
| Random Forest | 1.00 | 1.00 | 1.00 | 1.00 |
| Random Forest (threshold = 0.3) | — | 1.00 | 1.00 | 1.00 |

**Top predictive features:** _fill in from `importances.head(10)`_

## Key finding

_One or two sentences once results are in — e.g. which risk factors mattered most, and how much recall improved at the lower threshold._

## Tech stack

Python, pandas, scikit-learn, seaborn/matplotlib

## Project structure

```
cervical-risk-classification/
├── 01_uci_risk_model.ipynb
├── data/
│   └── risk_factors_cervical_cancer.csv/
├── figures/
├── requirements.txt
└── README.md

