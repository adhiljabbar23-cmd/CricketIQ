# CricketIQ

An ODI cricket match prediction system built using Python, data engineering, statistical analysis, and machine learning.

## 1. Project Overview

CricketIQ is a machine-learning project designed to analyze historical One Day International (ODI) cricket data and predict match outcomes.

The system combines historical team performance, head-to-head records, venue information, player statistics, and recent team form to generate pre-match predictions.

The project follows a structured data science workflow, from data collection and preprocessing to feature engineering, model development, evaluation, and model interpretation.

## 2. Objectives

- Collect and organize historical ODI match and player data.
- Clean, validate, and integrate datasets from different sources.
- Develop meaningful pre-match team and player performance features.
- Build machine-learning models for binary match outcome prediction.
- Evaluate models using appropriate classification and probability metrics.
- Analyze model errors, feature importance, and prediction reliability.

## 3. Technology Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Data Processing | Pandas, NumPy |
| Statistical Analysis | SciPy, Statsmodels |
| Machine Learning | Scikit-learn, XGBoost |
| Model Interpretation | SHAP |
| Visualization | Matplotlib, Seaborn |
| Data Collection | Requests, BeautifulSoup |
| Development Environment | Jupyter Notebook |

## 4. Project Workflow

The project is organized into the following stages:

1. Data exploration and collection
2. Afghanistan ODI match data collection and processing
3. ODI data processing and player data preparation
4. Dataset integration and validation
5. Team-level feature engineering
6. Player data processing and identity management
7. Player-level feature engineering
8. Final team-level feature engineering
9. Exploratory data analysis and feature validation
10. Model training, evaluation, and diagnostics

## 5. Machine Learning Approach

The prediction task is formulated as binary classification.

The target variable is `team_1_win`:

- `1`: Team 1 wins.
- `0`: Team 2 wins.

Matches without a decisive result are excluded from binary supervised model training.

### Models evaluated

- Logistic Regression
- Random Forest
- XGBoost

### Final model

The selected model is XGBoost with a maximum tree depth of 3.

The model uses historical team and player performance features, along with a classification threshold of 0.60 selected using out-of-fold training predictions.

### Final test results

Evaluation was performed on a chronological test set containing 392 matches.

| Metric | Test Result |
|---|---:|
| Accuracy | 64.54% |
| Balanced Accuracy | 64.56% |
| Precision | 65.76% |
| Recall | 61.42% |
| Macro F1-score | 64.51% |
| ROC-AUC | 0.7055 |
| Log Loss | 0.6287 |
| Brier Score | 0.2191 |
| MCC | 0.2917 |

These results represent the performance on the held-out test period. They should not be interpreted as a guarantee of future prediction accuracy.

## 6. Model Analysis and Diagnostics

The model development process also includes:

- Chronological training, validation, and test splits.
- Date-grouped cross-validation.
- Threshold selection using out-of-fold predictions.
- Confusion matrix and classification error analysis.
- Confidence-based prediction analysis.
- Year-wise performance and data drift investigation.
- Feature-group ablation experiments.
- SHAP-based model interpretation.
- Probability calibration experiments.

The final model was retained without additional probability calibration because the tested calibration methods did not improve validation Brier score or Log Loss.

## 7. Repository Structure

```text
CricketIQ/
│
├── data/
│   ├── raw/
│   ├── processed/
│   │   ├── afghanistan_odi/
│   │   ├── integrated/
│   │   ├── model_ready_pre_match/
│   │   └── player_data/
│   │
│   └── features/
│       └── player_data/
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_afghanistan_match_collection.ipynb
│   ├── 03_cricsheet_odi_processing.ipynb
│   ├── 04_dataset_integration.ipynb
│   ├── 05_feature_engineering.ipynb
│   ├── 06_player_data_processing.ipynb
│   ├── 07_player_feature_engineering.ipynb
│   ├── 08_team_level_feature_engineering.ipynb
│   ├── 09_exploratory_data_analysis.ipynb
│   └── 10_model_training_and_evaluation.ipynb
│
├── Reports/
│   └── Technical reports and analysis documents
│
├── requirements.txt
├── project_inventory.csv
├── .gitignore
└── README.md
