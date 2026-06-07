# Cirrhosis Patient Survival Prediction

A machine learning project that predicts the survival status of cirrhosis patients based on clinical and laboratory features. The model classifies patients into three outcomes: **D** (Deceased), **C** (Censored / survived), and **CL** (Censored due to liver transplant).

---

## Objectives

- **Risk Factor Identification** — Determine which clinical features (e.g., bilirubin, albumin, prothrombin time) are most strongly associated with patient survival.
- **Survival Prediction** — Train and evaluate machine learning classifiers to predict a patient's survival status from medical data.

---

## Dataset

The dataset (`cirrhosis.csv`) contains **418 patient records** and **20 features** covering patient demographics, clinical symptoms, and laboratory blood test results. The target variable is `Status`, which indicates patient outcome — **D** (deceased), **C** (censored/survived), or **CL** (censored due to liver transplant).

---

## Project Structure

```
├── cirrhosis.csv             # Raw dataset
├── cirrhosis_notebook.ipynb  # Main Google Colab notebook
├── train_data.csv            # Training split (80%)
├── test_data.csv             # Test split (20%)
├── status_predictions.csv    # Model predictions on test data
├── random_forest_classifier.pkl
├── decision_tree_classifier.pkl
└── xgb_classifier.pkl
```

---

## Pipeline

### 1. Data Loading & Preprocessing
- Load raw CSV and convert `Age` from days to years.
- Identify numerical and categorical columns.
- Impute missing values using **KNN Imputer** (numerical) and **mode imputation** (categorical).
- Encode categorical variables using **Label Encoding**.
- Normalize features using **MinMaxScaler**.

### 2. Exploratory Data Analysis
- Histograms and boxplots for all numerical features.
- Count plots for categorical features.
- **ANOVA tests** to assess numerical feature significance vs. survival status — all features showed statistically significant differences (p < 0.05).
- **Chi-Square tests** for categorical features — Ascites, Hepatomegaly, Spiders, and Edema showed strong associations with survival status.

### 3. Model Training
Four classifiers were trained and evaluated:

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| K-Nearest Neighbors | 0.77 | 0.77 | 0.77 | 0.76 |
| Decision Tree | 0.77 | 0.77 | 0.77 | 0.77 |
| Random Forest | 0.80 | 0.76 | 0.80 | 0.78 |
| **XGBoost** | **0.87** | **0.87** | **0.87** | **0.86** |

**XGBoost** achieved the best performance and was selected as the final model.

### 4. Testing & Prediction
- The saved XGBoost model is loaded and run on the held-out test set.
- Predictions (0, 1, 2) are decoded back to original labels (C, CL, D).
- Final predictions are saved to `status_predictions.csv`.

---

## Key Findings

- **Bilirubin, Copper, N_Days, and Prothrombin** showed the highest F-statistics in ANOVA, making them the strongest predictors of survival outcome.
- **Drug type** showed no significant association with survival status (Chi-Square p = 0.99).
- Several features including bilirubin, cholesterol, and alkaline phosphatase exhibited **right-skewed distributions**, consistent with clinical presentations in diseased populations.

---

## How to Run (Google Colab)

1. Open the notebook in [Google Colab](https://colab.research.google.com/).
2. Upload `cirrhosis.csv` via the **Files** panel on the left.
3. Run each section in order:
   - Data Loading & Preprocessing
   - Exploratory Data Analysis & Visualisation
   - Model Training
   - Testing & Prediction
4. Output files (`train_data.csv`, `test_data.csv`, `status_predictions.csv`, and `.pkl` model files) will be generated in the working directory.

---

## Dependencies

```
numpy
pandas
scikit-learn
matplotlib
seaborn
scipy
xgboost
keras / tensorflow
joblib
```

Install all dependencies with:
```bash
pip install numpy pandas scikit-learn matplotlib seaborn scipy xgboost tensorflow joblib
```

---

## Results

The XGBoost classifier achieves **87% accuracy** on the held-out test set, correctly classifying patient survival outcomes across all three categories. Predictions are exported to `status_predictions.csv` for downstream use.
