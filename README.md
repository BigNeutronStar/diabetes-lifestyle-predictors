# Lifestyle Predictors of Type 2 Diabetes

This repository contains a machine learning research project focused on identifying behavioral and demographic lifestyle factors that most strongly predict the presence of Type 2 Diabetes. 

The goal is to provide a robust statistical and predictive analysis using data from the CDC's Behavioral Risk Factor Surveillance System (BRFSS).

## Dataset

- **Source:** BRFSS 2015 (Preprocessed Kaggle version)
- **Size:** 253,680 records
- **Features:** 21 predictors (BMI, Physical Activity, Smoking, General Health, etc.)
- **Target:** `Diabetes_binary` (0 = No Diabetes, 1 = Prediabetes / Type 2 Diabetes)

## Repository Structure

```
.
├── data/
│   ├── raw/                  # Original datasets
│   └── processed/            # Scaled, balanced, and encoded datasets
├── models/                   # Saved model artifacts (scalers, pkl files)
├── notebooks/
│   ├── run_eda.py            # Iteration 1: Data extraction and Exploratory Data Analysis
│   └── run_iter2.py          # Iteration 2: Preprocessing, SMOTE, and Baseline LR
├── outputs/
│   └── figures/              # Generated visualizations and metrics plots
├── RESEARCH_LOG.md           # Detailed research log and findings for each iteration
└── README.md                 # Project overview
```

## Current Project Status

The project is being developed in iterative phases. Currently, **Iteration 1 and Iteration 2 are complete**.

### Iteration 1: Exploratory Data Analysis (EDA)
- Confirmed a significant class imbalance (86.1% negative vs. 13.9% positive cases).
- Identified strong positive predictors (General Health status, High Blood Pressure, BMI).
- Identified protective factors (Income, Education, Physical Activity).

### Iteration 2: Preprocessing & Baseline Model
- **Splits:** 70% Train, 15% Validation, 15% Test.
- **Scaling:** Applied `StandardScaler` to continuous variables (BMI, MentHlth, PhysHlth).
- **Balancing:** Applied `SMOTE` strictly to the training set, achieving a 1:1 class ratio.
- **Baseline Model:** Trained a Logistic Regression model.
- **Baseline Metrics (Validation):**
  - **ROC-AUC:** 0.8192
  - **Recall (Class 1):** 76% (The model effectively detects true positive cases).

## Next Steps (Iteration 3)
- Train advanced non-linear ensemble models: **Random Forest**, **XGBoost**, and **LightGBM**.
- Perform hyperparameter tuning using Optuna or GridSearchCV.
- Conduct feature importance and SHAP value analysis for interpretability.

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/BigNeutronStar/diabetes-lifestyle-predictors.git
   cd diabetes-lifestyle-predictors
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn pyarrow
   ```

3. Ensure the raw CSV data is placed in `data/raw/` (e.g., `diabetes_binary_health_indicators_BRFSS2015.csv`).

4. Run the pipelines sequentially:
   ```bash
   python notebooks/run_eda.py
   python notebooks/run_iter2.py
   ```
