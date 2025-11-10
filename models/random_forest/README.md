# Random Forest Team Submission Guidelines

### Preston, Garret, Anthony Do

Welcome to the Random Forest team! This document outlines how to submit your completed Random Forest model for the heat risk prediction project.

## Development Notebook

Your main development notebook is located at:
**`notebooks/random_forest_model.ipynb`**

This notebook contains:
- Complete setup code (data loading, imports, Colab mounting)
- TODO sections for you to implement:
  - Feature preparation and selection
  - Categorical variable encoding
  - Random Forest regressor and classifier
  - Hyperparameter tuning (GridSearchCV or RandomSearchCV)
  - Model evaluation with feature importance
  - Model saving

## Submission Location

Save all your deliverables in this directory: **`models/random_forest/`**

## File Naming Conventions

Use the following naming conventions for your files:

### Model Files
- **Regression model**: `rf_regression.pkl`
- **Classification model**: `rf_classification.pkl`

### Prediction Files
- **Validation predictions**: `predictions_val.csv`
- **Test predictions**: `predictions_test.csv`

### Feature Importance
- **Feature importance plot**: `feature_importance.png` or `feature_importance_regression.png` and `feature_importance_classification.png`

### Documentation Files
- **Hyperparameters**: `hyperparameters.txt` or `hyperparameters.json`

### Example Structure
```
models/random_forest/
├── rf_regression.pkl
├── rf_classification.pkl
├── predictions_val.csv
├── predictions_test.csv
├── feature_importance_regression.png
├── feature_importance_classification.png
├── hyperparameters.txt
└── README.md (this file)
```

## Required Deliverables

### 1. Trained Model Files

Submit your trained model files:
- **Regression model**: Random Forest regressor trained to forecast heat index (apparent temperature)
- **Classification model**: Random Forest classifier trained to predict heat risk (binary classification)

**Format**: `.pkl` files (pickle format, use `joblib.dump()`)

### 2. Predictions on Validation and Test Sets

Create CSV files with predictions:

**`predictions_val.csv`** should contain:
- `Date`: Date column
- `actual_heat_index`: True heat index values (for regression)
- `predicted_heat_index`: Predicted heat index values (for regression)
- `actual_heat_risk`: True heat risk labels (0 or 1, for classification)
- `predicted_heat_risk`: Predicted heat risk labels (0 or 1, for classification)
- `predicted_heat_risk_proba`: Predicted probabilities (optional, for classification)

**`predictions_test.csv`** should have the same format for test set predictions.

### 3. Feature Importance Plots

Create visualizations showing feature importance:
- **Regression feature importance**: Bar chart or horizontal bar chart
- **Classification feature importance**: Bar chart or horizontal bar chart

**Format**: PNG images showing top N features (e.g., top 10-15 features)

**Tips**: Use matplotlib or seaborn to create clear, readable plots with feature names on axes.

### 4. Hyperparameter Values Used

Document the hyperparameters used for your final models:

**For Regression Model**:
- `n_estimators`: Number of trees
- `max_depth`: Maximum depth of trees
- `min_samples_split`: Minimum samples required to split
- `min_samples_leaf`: Minimum samples in leaf nodes
- `max_features`: Number of features to consider for best split
- Any other hyperparameters you tuned

**For Classification Model**:
- Same hyperparameters as above
- `class_weight`: If used for imbalanced data

**Format**: Text file or JSON file with clear formatting

**Example format**:
```
Random Forest Regression Hyperparameters:
- n_estimators: 200
- max_depth: 15
- min_samples_split: 5
- min_samples_leaf: 2
- max_features: 'sqrt'
- random_state: 42
```

## How to Load and Use Your Model

Include code snippets showing how to load your models:

```python
import joblib

# Load regression model
rf_regressor = joblib.load('models/random_forest/rf_regression.pkl')

# Load classification model
rf_classifier = joblib.load('models/random_forest/rf_classification.pkl')

# Make predictions
# (Include example of how to prepare input data and make predictions)
```

## Implementation Checklist

Before submitting, ensure you have:

- [ ] Trained both regression and classification models
- [ ] Saved model files using `.pkl` format (joblib)
- [ ] Generated predictions on validation set
- [ ] Generated predictions on test set
- [ ] Created prediction CSV files with required columns
- [ ] Created feature importance visualizations for both models
- [ ] Documented hyperparameter values used
- [ ] Performed hyperparameter tuning (GridSearchCV or RandomSearchCV)
- [ ] Tested that models can be loaded successfully
- [ ] Verified prediction file formats are correct

## Evaluation Criteria

Your models will be evaluated on:

1. **Regression Performance**:
   - RMSE (Root Mean Squared Error)
   - MAE (Mean Absolute Error)
   - R² Score

2. **Classification Performance**:
   - Accuracy
   - Precision
   - Recall
   - F1-Score
   - AUC-ROC (if probabilities provided)

3. **Feature Importance**:
   - Clear visualization
   - Interpretable feature names
   - Insights into which features matter most

4. **Code Quality**:
   - Clean, well-commented code
   - Proper feature engineering
   - Appropriate hyperparameter tuning strategy

5. **Documentation**:
   - Hyperparameters clearly documented
   - Feature importance analysis provided

## Tips for Success

1. **Hyperparameter Tuning**: Use GridSearchCV or RandomSearchCV to find optimal parameters
2. **Feature Engineering**: Consider creating time-based features and interactions
3. **Feature Importance**: Analyze which features are most important for predictions
4. **Handle Categorical Variables**: Properly encode categorical features (one-hot encoding or label encoding)
5. **Imbalanced Data**: Consider using `class_weight` parameter if heat risk events are rare
6. **Visualization**: Create clear, readable feature importance plots

## Hyperparameter Tuning Tips

### Key Hyperparameters to Tune:

- **n_estimators**: More trees = better performance but slower (start with 100-200)
- **max_depth**: Controls overfitting (deeper = more complex, risk of overfitting)
- **min_samples_split**: Higher values prevent overfitting (start with 2-10)
- **min_samples_leaf**: Higher values create simpler trees (start with 1-4)
- **max_features**: Controls randomness ('sqrt', 'log2', or number)

### Tuning Strategy:

```python
from sklearn.model_selection import GridSearchCV

param_grid = {
    'n_estimators': [100, 200],
    'max_depth': [10, 15, 20],
    'min_samples_split': [5, 10],
    'min_samples_leaf': [2, 4]
}

grid_search = GridSearchCV(
    estimator=RandomForestRegressor(random_state=42),
    param_grid=param_grid,
    cv=5,
    scoring='neg_mean_squared_error',
    n_jobs=-1
)
```

## Resources

- **Learning Notebook**: `learning/all_models_demo.ipynb` - Section 2 (Random Forest Demo)
- **Development Notebook**: `notebooks/random_forest_model.ipynb`
- **Scikit-learn Documentation**: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html
- **Feature Importance Guide**: https://scikit-learn.org/stable/auto_examples/ensemble/plot_forest_importances.html

## Questions?

If you have questions about:
- **Model implementation**: Refer to `learning/all_models_demo.ipynb`
- **Data format**: Check `data/processed/README.md`
- **Workflow**: See `notebooks/README.md`
- **General ML concepts**: Review `learning/simple_modeling.ipynb`

Good luck with your Random Forest implementation!




