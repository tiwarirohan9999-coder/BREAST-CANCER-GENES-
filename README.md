# Breast Cancer Survival Prediction Report

A Jupyter notebook that analyzes the **METABRIC** breast cancer gene-expression and clinical
dataset to explore factors associated with patient survival and to build/compare two
machine-learning models that predict patient outcome (Deceased vs. Alive).

## Overview

The notebook (`BREAST_CANCER_report.ipynb`) walks through a full mini data-science
pipeline:

1. **Load & inspect** the METABRIC dataset (clinical + gene expression + mutation features).
2. **Explore correlations** between numeric features and the `overall_survival` target.
3. **Visualize** the top correlated features, age vs. mutation count, and the survival
   class balance.
4. **Preprocess** the data — drop missing values, label-encode categorical columns,
   scale features, and balance the classes with SMOTE.
5. **Train and evaluate** two classifiers:
   - Logistic Regression
   - Decision Tree
6. **Compare model performance** and plot a confusion matrix for the better-performing model.

## Dataset

- **File expected:** `METABRIC_RNA_Mutation.csv`
- **Shape:** 1,904 rows × 693 columns (clinical attributes, gene expression values, and
  mutation status columns)
- **Target column:** `overall_survival` (1 = Alive, 0 = Deceased)

> The CSV is **not included** in this repo/notebook — place `METABRIC_RNA_Mutation.csv`
> in the same directory as the notebook before running it. It's publicly available on
> [Kaggle](https://www.kaggle.com/datasets/raghadalharbi/breast-cancer-gene-expression-profiles-metabric).

## Requirements

```
python >= 3.9
pandas
numpy
scikit-learn
imbalanced-learn
matplotlib
seaborn
jupyter
```

Install with:

```bash
pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn jupyter
```

## How to Run

1. Place `METABRIC_RNA_Mutation.csv` in the project folder.
2. Launch Jupyter:
   ```bash
   jupyter notebook BREAST_CANCER_report.ipynb
   ```
3. Run all cells in order (`Kernel → Restart & Run All`).

## Pipeline Details

| Step | Description |
|---|---|
| Data loading | Reads the CSV, prints shape, `info()`, and `describe()` |
| Correlation analysis | Computes correlation of all numeric features with `overall_survival`, ranks top 10 |
| Heatmap | Correlation heatmap of the top 10 features + target |
| Scatter plot | `age_at_diagnosis` vs `mutation_count`, colored by survival |
| Cleaning | Drops rows with missing values, label-encodes text/categorical columns |
| Split & scale | 80/20 train-test split (stratified), `StandardScaler` on features |
| Class balancing | SMOTE oversampling applied to the training set only |
| Survival pie chart | Class distribution of Deceased vs. Alive |
| Model 1 | Logistic Regression (`max_iter=1000`) |
| Model 2 | Decision Tree (`max_depth=5`) |
| Comparison | Bar chart comparing test accuracy of both models |
| Confusion matrix | Plotted for whichever model scored higher accuracy |

## Results

After dropping missing values, the cleaned dataset had **1,093 rows**; test set = 219 samples.

| Model | Accuracy | Recall | F1 Score | MSE |
|---|---|---|---|---|
| Logistic Regression | 59.4% | 0.536 | 0.539 | 0.406 |
| **Decision Tree** | **68.5%** | **0.608** | **0.631** | **0.315** |

The **Decision Tree** classifier outperformed Logistic Regression on all metrics and is
used for the final confusion matrix.

## Output Files

Running the notebook generates the following image files in the working directory:

- `heatmap.png` — correlation heatmap of top features vs. survival
- `scatter_plot.png` — age vs. mutation count, colored by survival
- `survival_pie_chart.png` — class distribution pie chart
- `model_comparison.png` — accuracy bar chart (Logistic Regression vs. Decision Tree)
- `confusion_matrix.png` — confusion matrix of the best-performing model

## Notes / Possible Improvements

- Class balance is only 55.7% Alive / 44.3% Deceased, so accuracy alone can be
  misleading — recall/F1 are also reported for this reason.
- Only two simple models are compared; results could likely be improved with
  ensemble methods (Random Forest, Gradient Boosting) or hyperparameter tuning.
- A large number of columns are dropped implicitly via `dropna()` — an imputation
  strategy could preserve more of the original 1,904 rows.

##  AUTHOR
ROHAN TIWARI , RESEARCHER , CO- DSAI , TIET- UQ CENTER
