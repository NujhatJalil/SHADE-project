# XGBoost/AdaBoost Team Submission Guidelines

### Anthony Zhou, Prince, Sharaf

Welcome to the XGBoost/AdaBoost team! This document outlines how to submit your completed XGBoost and AdaBoost models for the heat risk prediction project.

## Development Notebook

Your main development notebook is located at:
**`notebooks/xgboost_adaboost_model.ipynb`**

This notebook contains:
- Complete setup code (data loading, imports, Colab mounting)
- TODO sections for you to implement:
  - Feature preparation and selection
  - Categorical variable encoding
  - XGBoost regressor and classifier
  - AdaBoost regressor and classifier
  - Hyperparameter tuning for both models
  - Model evaluation and comparison
  - Feature importance analysis
  - Model saving

## Submission Location

Save all your deliverables in this directory: **`models/xgboost_adaboost/`**

## File Naming Conventions

Use the following naming conventions for your files:

### Model Files
- **XGBoost regression**: `xgb_regression.pkl`
- **XGBoost classification**: `xgb_classification.pkl`
- **AdaBoost regression**: `adaboost_regression.pkl`
- **AdaBoost classification**: `adaboost_classification.pkl`

### Prediction Files
- **Validation predictions**: `predictions_val.csv`
- **Test predictions**: `predictions_test.csv`

### Feature Importance
- **XGBoost feature importance**: `xgb_feature_importance.png`
- **AdaBoost feature importance**: `adaboost_feature_importance.png`

### Documentation Files
- **Model comparison**: `model_comparison.txt` or `comparison_results.csv`
- **Hyperparameters**: `hyperparameters.txt` or `hyperparameters.json`

### Example Structure
```
models/xgboost_adaboost/
├── xgb_regression.pkl
├── xgb_classification.pkl
├── adaboost_regression.pkl
├── adaboost_classification.pkl
├── predictions_val.csv
├── predictions_test.csv
├── xgb_feature_importance.png
├── adaboost_feature_importance.png
├── model_comparison.txt
├── hyperparameters.txt
└── README.md (this file)
```

## Required Deliverables

### 1. Trained Model Files

Submit your trained model files for both XGBoost and AdaBoost:

**XGBoost Models**:
- **Regression model**: XGBoost regressor trained to forecast heat index
- **Classification model**: XGBoost classifier trained to predict heat risk

**AdaBoost Models**:
- **Regression model**: AdaBoost regressor trained to forecast heat index
- **Classification model**: AdaBoost classifier trained to predict heat risk

**Format**: `.pkl` files (pickle format, use `joblib.dump()`)

### 2. Predictions on Validation and Test Sets

Create CSV files with predictions from **both** models:

**`predictions_val.csv`** should contain:
- `Date`: Date column
- `actual_heat_index`: True heat index values
- `xgb_predicted_heat_index`: XGBoost predicted heat index
- `adaboost_predicted_heat_index`: AdaBoost predicted heat index
- `actual_heat_risk`: True heat risk labels (0 or 1)
- `xgb_predicted_heat_risk`: XGBoost predicted heat risk
- `adaboost_predicted_heat_risk`: AdaBoost predicted heat risk
- `xgb_predicted_heat_risk_proba`: XGBoost predicted probabilities (optional)
- `adaboost_predicted_heat_risk_proba`: AdaBoost predicted probabilities (optional)

**`predictions_test.csv`** should have the same format for test set predictions.

### 3. Feature Importance Plots

Create visualizations showing feature importance for both models:
- **XGBoost feature importance**: Bar chart showing top features
- **AdaBoost feature importance**: Bar chart showing top features

**Format**: PNG images showing top N features (e.g., top 10-15 features)

**Tips**: Use matplotlib or seaborn. Consider side-by-side comparison plots.

### 4. Model Comparison Results

Document comparison between XGBoost and AdaBoost:

**For Regression**:
- RMSE comparison
- MAE comparison
- R² comparison
- Training time comparison (optional)

**For Classification**:
- Accuracy comparison
- Precision comparison
- Recall comparison
- F1-Score comparison
- AUC-ROC comparison (if probabilities provided)

**Format**: Text file or CSV file with clear comparison table

**Example format**:
```
Model Comparison - Regression:
Metric          XGBoost    AdaBoost
RMSE            2.45       2.67
MAE             1.89       2.12
R²              0.87       0.84

Model Comparison - Classification:
Metric          XGBoost    AdaBoost
Accuracy        0.89       0.86
Precision       0.91       0.88
Recall          0.87       0.84
F1-Score        0.89       0.86
```

### 5. Hyperparameter Values Used

Document the hyperparameters used for your final models:

**XGBoost Hyperparameters**:
- `n_estimators`: Number of boosting rounds
- `max_depth`: Maximum tree depth
- `learning_rate`: Step size shrinkage
- `subsample`: Subsample ratio of training instances
- `colsample_bytree`: Subsample ratio of columns
- `reg_alpha`: L1 regularization (for regression)
- `reg_lambda`: L2 regularization

**AdaBoost Hyperparameters**:
- `n_estimators`: Number of estimators
- `learning_rate`: Learning rate
- `base_estimator`: Base estimator used (DecisionTreeClassifier/Regressor parameters)

**Format**: Text file or JSON file with clear formatting

## How to Load and Use Your Models

Include code snippets showing how to load your models:

```python
import joblib

# Load XGBoost models
xgb_regressor = joblib.load('models/xgboost_adaboost/xgb_regression.pkl')
xgb_classifier = joblib.load('models/xgboost_adaboost/xgb_classification.pkl')

# Load AdaBoost models
adaboost_regressor = joblib.load('models/xgboost_adaboost/adaboost_regression.pkl')
adaboost_classifier = joblib.load('models/xgboost_adaboost/adaboost_classification.pkl')

# Make predictions
# (Include example of how to prepare input data and make predictions)
```

## Implementation Checklist

Before submitting, ensure you have:

- [ ] Trained XGBoost regression and classification models
- [ ] Trained AdaBoost regression and classification models
- [ ] Saved all model files using `.pkl` format (joblib)
- [ ] Generated predictions on validation set (both models)
- [ ] Generated predictions on test set (both models)
- [ ] Created prediction CSV files with required columns
- [ ] Created feature importance visualizations for both models
- [ ] Documented model comparison results
- [ ] Documented hyperparameter values used
- [ ] Performed hyperparameter tuning for both models
- [ ] Tested that models can be loaded successfully
- [ ] Verified prediction file formats are correct

## Evaluation Criteria

Your models will be evaluated on:

1. **Regression Performance**:
   - RMSE, MAE, R² for both XGBoost and AdaBoost
   - Comparison between models

2. **Classification Performance**:
   - Accuracy, Precision, Recall, F1-Score for both models
   - Comparison between models

3. **Model Comparison**:
   - Clear comparison analysis
   - Understanding of when each model performs better
   - Insights into model differences

4. **Feature Importance**:
   - Clear visualizations for both models
   - Comparison of feature importance between models

5. **Code Quality**:
   - Clean, well-commented code
   - Proper feature engineering
   - Appropriate hyperparameter tuning strategy

6. **Documentation**:
   - Hyperparameters clearly documented
   - Model comparison clearly presented

## Tips for Success

1. **Hyperparameter Tuning**: Both XGBoost and AdaBoost have many hyperparameters to tune
2. **XGBoost Tips**:
   - Start with default parameters
   - Tune `learning_rate` and `n_estimators` together
   - Use early stopping to prevent overfitting
   - Consider regularization parameters (`reg_alpha`, `reg_lambda`)

3. **AdaBoost Tips**:
   - Choose appropriate base estimator (DecisionTreeClassifier/Regressor)
   - Tune `learning_rate` and `n_estimators`
   - Consider `max_depth` of base estimator

4. **Feature Importance**: Compare feature importance between XGBoost and AdaBoost
5. **Model Comparison**: Create visualizations comparing performance metrics
6. **Early Stopping**: Use early stopping for XGBoost to prevent overfitting

## Hyperparameter Tuning Tips

### XGBoost Key Hyperparameters:

- **n_estimators**: Number of boosting rounds (start with 100-200)
- **max_depth**: Maximum tree depth (3-10, start with 6)
- **learning_rate**: Step size (0.01-0.3, start with 0.1)
- **subsample**: Row sampling (0.6-1.0, start with 0.8)
- **colsample_bytree**: Column sampling (0.6-1.0, start with 0.8)
- **reg_alpha**: L1 regularization (0-10, optional)
- **reg_lambda**: L2 regularization (0-10, optional)

### AdaBoost Key Hyperparameters:

- **n_estimators**: Number of estimators (start with 50-100)
- **learning_rate**: Learning rate (0.01-2.0, start with 1.0)
- **base_estimator**: DecisionTreeClassifier/Regressor with max_depth (3-10)

### Tuning Strategy Example:

```python
# XGBoost Grid Search
param_grid_xgb = {
    'n_estimators': [100, 200],
    'max_depth': [4, 6, 8],
    'learning_rate': [0.05, 0.1],
    'subsample': [0.8, 1.0]
}

# AdaBoost Grid Search
param_grid_ada = {
    'n_estimators': [50, 100],
    'learning_rate': [0.5, 1.0, 1.5],
    'base_estimator__max_depth': [3, 5, 7]
}
```

## Resources

- **Learning Notebook**: `learning/all_models_demo.ipynb` - Section 3 (XGBoost/AdaBoost Demo)
- **Development Notebook**: `notebooks/xgboost_adaboost_model.ipynb`
- **XGBoost Documentation**: https://xgboost.readthedocs.io/
- **AdaBoost Documentation**: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostRegressor.html
- **XGBoost vs AdaBoost**: Compare performance and understand differences

## Questions?

If you have questions about:
- **Model implementation**: Refer to `learning/all_models_demo.ipynb`
- **Data format**: Check `data/processed/README.md`
- **Workflow**: See `notebooks/README.md`
- **General ML concepts**: Review `learning/simple_modeling.ipynb`

Good luck with your XGBoost and AdaBoost implementations!




