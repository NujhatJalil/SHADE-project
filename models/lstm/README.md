# LSTM Team Submission Guidelines

### Mikhail, Jennifer, Kyler

Welcome to the LSTM team! This document outlines how to submit your completed LSTM model for the heat risk prediction project.

## Development Notebook

Your main development notebook is located at:
**`notebooks/lstm_model.ipynb`**

This notebook contains:
- Complete setup code (data loading, imports, GPU setup)
- TODO sections for you to implement:
  - Sequential data preparation
  - LSTM architecture design
  - Model training and hyperparameter tuning
  - Model evaluation (regression and classification)
  - Model saving

## Submission Location

Save all your deliverables in this directory: **`models/lstm/`**

## File Naming Conventions

Use the following naming conventions for your files:

### Model Files
- **Regression model**: `lstm_regression.h5` or `lstm_regression.keras`
- **Classification model**: `lstm_classification.h5` or `lstm_classification.keras`

### Prediction Files
- **Validation predictions**: `predictions_val.csv`
- **Test predictions**: `predictions_test.csv`

### Documentation Files
- **Model architecture summary**: `model_architecture.txt` or `model_summary.txt`
- **Training history**: `training_history.csv` or `training_curves.png`

### Example Structure
```
models/lstm/
├── lstm_regression.h5
├── lstm_classification.h5
├── predictions_val.csv
├── predictions_test.csv
├── model_architecture.txt
├── training_history.csv
└── README.md (this file)
```

## Required Deliverables

### 1. Trained Model Weights

Submit your trained model files:
- **Regression model**: LSTM model trained to forecast heat index (apparent temperature)
- **Classification model**: LSTM model trained to predict heat risk (binary classification)

**Format**: `.h5` or `.keras` files (TensorFlow/Keras format)

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

### 3. Model Architecture Summary

Create a text file documenting:
- Number of LSTM layers
- Number of units in each LSTM layer
- Dense layers configuration
- Dropout rates
- Activation functions
- Total number of parameters

**Example format**:
```
LSTM Regression Model Architecture:
- Input: (batch_size, sequence_length, features)
- LSTM Layer 1: 50 units, return_sequences=True
- Dropout: 0.2
- LSTM Layer 2: 50 units, return_sequences=False
- Dropout: 0.2
- Dense Layer: 25 units
- Output Layer: 1 unit (linear activation)
- Total Parameters: XXX
```

### 4. Training History/Curves

Provide training history information:
- Option 1: CSV file with columns: `epoch`, `loss`, `val_loss`, `mae`, `val_mae`
- Option 2: PNG image showing training curves (loss and metrics over epochs)
- Option 3: Both

This helps reviewers understand model training progress and potential overfitting.

## How to Load and Use Your Model

Include code snippets showing how to load your models:

```python
import tensorflow as tf
from tensorflow import keras

# Load regression model
regression_model = keras.models.load_model('models/lstm/lstm_regression.h5')

# Load classification model
classification_model = keras.models.load_model('models/lstm/lstm_classification.h5')

# Make predictions
# (Include example of how to prepare input data and make predictions)
```

## Implementation Checklist

Before submitting, ensure you have:

- [ ] Trained both regression and classification models
- [ ] Saved model files using `.h5` or `.keras` format
- [ ] Generated predictions on validation set
- [ ] Generated predictions on test set
- [ ] Created prediction CSV files with required columns
- [ ] Documented model architecture
- [ ] Saved training history/curves
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

3. **Code Quality**:
   - Clean, well-commented code
   - Proper data preprocessing
   - Appropriate hyperparameter tuning

4. **Documentation**:
   - Clear model architecture description
   - Training history provided
   - Easy-to-understand predictions format

## Tips for Success

1. **Start Early**: LSTM training can take time, especially with hyperparameter tuning
2. **Use GPU**: Make sure you're using GPU runtime in Colab for faster training
3. **Monitor Training**: Watch for overfitting by comparing train vs validation loss
4. **Save Checkpoints**: Save models periodically during training
5. **Test Loading**: Verify models can be loaded before submitting
6. **Check Formats**: Ensure CSV files have correct columns and formats

## Resources

- **Learning Notebook**: `learning/all_models_demo.ipynb` - Section 1 (LSTM Demo)
- **Development Notebook**: `notebooks/lstm_model.ipynb`
- **TensorFlow/Keras Documentation**: https://keras.io/api/
- **LSTM Layer Documentation**: https://www.tensorflow.org/api_docs/python/tf/keras/layers/LSTM

## Questions?

If you have questions about:
- **Model implementation**: Refer to `learning/all_models_demo.ipynb`
- **Data format**: Check `data/processed/README.md`
- **Workflow**: See `notebooks/README.md`
- **General ML concepts**: Review `learning/simple_modeling.ipynb`

Good luck with your LSTM implementation!




