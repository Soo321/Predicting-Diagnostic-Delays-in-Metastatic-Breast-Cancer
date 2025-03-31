# Predicting Diagnostic Delays in Metastatic Breast Cancer
## Project Overview


## Objectives


## Data
- **Source**:
- **Size**: 100,000+ patient records
- **Key variables**:


## Modeling Approach

- **Problem Type**: Regression
- **Evaluation Metrics**: RMSE, MAE, R²
- **Algorithms Used**:
  - Individual Models: CatBoost, XGBoost, LightGBM, Random Forest, Gradient Boosting, AdaBoost, SVR, Ridge, MLP, HistGradientBoosting
  - Ensemble Model: **Stacking Regressor** (Meta-model: Linear Regression)


## Performance Optimization Techniques

| Strategy | Description |
|----------|-------------|
| **Feature Importance** | Identified key features using CatBoost, XGBoost, and Random Forest |
| **Mutual Information** | Selected top 20 features using `SelectKBest` with `mutual_info_regression` |
| **PCA Analysis** | Analyzed explained variance and loadings for potential dimensionality reduction |
| **Hyperparameter Tuning** | Tuned parameters like `depth`, `learning_rate`, and `n_estimators` |
| **Cross-Validation** | Used 10-fold K-Fold cross-validation to validate model stability |
| **Stacking Ensemble** | Combined 4 base models with a linear meta-model for final prediction |


## Model Performance (on Test Set)

| Model | RMSE | R² |
|-------|------|------|
| **Stacking Regressor** | **83.50** | **0.42** |
| CatBoost | 83.60 | 0.418 |
| GradientBoostingRegressor | 83.61 | 0.418 |
| RandomForestRegressor | 83.67 | 0.417 |
| XGBoost | 83.89 | 0.414 |
| LightGBM | 84.03 | 0.412 |
| AdaBoost | 86.40 | 0.379 |
| MLPRegressor | 108.95 | 0.012 |
| SVR | 122.06 | -0.240 |

> The **Stacking Regressor** outperformed all individual models, achieving the lowest RMSE and the highest R².


## Tools & Libraries
- Python (pandas, numpy, matplotlib, seaborn)
- Scikit-learn
- CatBoost / XGBoost / LightGBM
- SHAP (optional for future explainability)
- PCA & Mutual Info for feature selection

## Key Takeaways
- Tree-based models generally performed well, but stacking them further boosted accuracy.
- Feature engineering (via mutual info and PCA) helped focus on the most impactful predictors.
- Ensemble methods are powerful when individual models perform similarly but make different errors.
