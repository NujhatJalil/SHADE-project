# Introduction and Setup Guide

This guide provides a step-by-step walkthrough for getting started with the Heat Risk Prediction ML Project. Follow along with the learning notebooks to build your foundational knowledge.

## Section 1: Project Overview

### What is This Project?

This project focuses on building an ensemble machine learning model to predict heat risk using historical weather data. Heat risk is defined as:
- **(Daily Heat Index >= 105°F) OR (Daily High Temperature >= 95th percentile)** for at least **2 consecutive days**

### Why Are We Doing This?

Heat risk prediction is crucial for:
- Public health safety and early warning systems
- Resource allocation for cooling centers
- Climate change impact assessment
- Understanding weather patterns and extreme events

### Project Structure

The project is organized into three main areas:

1. **`learning/`**: Complete, executable tutorials for learning prerequisites
2. **`notebooks/`**: Partial notebooks with setup code complete, modeling sections with TODOs for teams
3. **`teams/`**: Storage location for final trained models and team submissions

## Section 2: Getting Started with Colab

### Prerequisites

Before starting, you'll need:
- A Google account
- Access to Google Colab
- Basic understanding of Python (helpful but not required)

### Step-by-Step Walkthrough

1. **Open `learning/colab_intro.ipynb`**

2. **Follow Section 1: Creating and Opening Notebooks**
   - Learn how to create new notebooks
   - Understand how to open existing notebooks from Drive
   - Practice renaming and saving notebooks

3. **Follow Section 2: Connecting to Google Drive**
   - Mount your Google Drive (essential for accessing project files)
   - Navigate to your project directory
   - Learn how to save files back to Drive

4. **Follow Section 3: Importing from GitHub** (Optional)
   - Useful if you need to clone repositories or import code

5. **Follow Section 4: Changing Runtime Environments**
   - Switch to GPU runtime for LSTM training (important!)
   - Verify GPU availability

6. **Follow Section 5: Importing Datasets**
   - Learn to load data from Drive (you'll use this for the weather data)
   - Understand local upload and URL methods

7. **Follow Section 6: Installing Packages**
   - Install required packages using pip
   - Understand requirements.txt files

8. **Follow Section 7: Basic Notebook Operations**
   - Master keyboard shortcuts
   - Learn cell execution

### Common Issues and Solutions

**Issue**: "Drive not mounting"
- **Solution**: Make sure you're signed into the correct Google account, and allow permissions when prompted

**Issue**: "GPU not available"
- **Solution**: Go to Runtime → Change runtime type → Select GPU → Save. You may need to wait if GPU quota is exhausted.

**Issue**: "Files not found"
- **Solution**: Verify the file path is correct. Remember that after mounting Drive, paths start with `/content/drive/MyDrive/`

### Clone This Repository to Google Drive (for Colab)

Follow these steps once to clone the repo into your Google Drive so all notebooks and data persist across sessions.

1. Mount your Google Drive

```python
from google.colab import drive
drive.mount('/content/drive')
```

2. Install git (if needed) and clone the repo into `MyDrive`

```python
!apt-get update -y && apt-get install -y git
%cd /content/drive/MyDrive
!git clone https://github.com/HrudithL/SHADE-ML-Team.git || echo "Repo exists"
```

3. Change into the repo and pull latest changes (for future sessions)

```python
%cd /content/drive/MyDrive/SHADE-ML-Team
!git pull
```

4. Verify you are in the repo root

```python
import os
print(os.getcwd())  # should be /content/drive/MyDrive/SHADE-ML-Team
```

Once set up, open and run any notebooks directly from this path. The standardized notebooks assume the repo lives at `/content/drive/MyDrive/SHADE-ML-Team` and use relative paths (e.g., `data/processed/`, `teams/...`).

Reference: `https://github.com/HrudithL/SHADE-ML-Team`

## Section 3: Learning Basic ML

### Overview

`learning/simple_modeling.ipynb` covers fundamental machine learning concepts using synthetic data. This ensures you understand the basics before working with real weather data.

### Step-by-Step Walkthrough

1. **Open `learning/simple_modeling.ipynb`**

2. **Follow Section 1: Basic Data Manipulation**
   - Learn pandas basics (DataFrames, data inspection)
   - Practice data cleaning operations
   - Understand data types and transformations

3. **Follow Section 2: Simple Regression Example**
   - Understand what regression is (predicting continuous values)
   - Learn train/test split
   - See how to evaluate regression models (RMSE, MAE, R²)
   - Visualize predictions

4. **Follow Section 3: Simple Classification Example**
   - Understand what classification is (predicting categories)
   - Learn about evaluation metrics (Accuracy, Precision, Recall, F1)
   - Create and interpret confusion matrices

5. **Follow Section 4: Train/Test Split and Cross-Validation**
   - Understand why we split data
   - Learn about overfitting and underfitting
   - Practice cross-validation techniques

6. **Follow Section 5: Basic Evaluation Metrics**
   - Deep dive into regression metrics (RMSE, MAE, R²)
   - Deep dive into classification metrics (Accuracy, Precision, Recall, F1)
   - Learn when to use which metric

7. **Follow Section 6: Feature Engineering Basics**
   - Create new features from existing ones
   - Scale features (StandardScaler, MinMaxScaler)
   - Encode categorical variables (LabelEncoder, OneHotEncoder)

### Key Concepts to Master

- **Regression vs Classification**: Understanding the difference is crucial
- **Train/Test Split**: Always evaluate on unseen data
- **Evaluation Metrics**: Know which metrics to use for each problem type
- **Feature Engineering**: Creating good features improves model performance

## Section 4: Understanding the Models

### Overview

`learning/all_models_demo.ipynb` demonstrates how to use LSTM, Random Forest, and XGBoost/AdaBoost with completely unrelated mock data. This focuses on model usage patterns rather than domain-specific knowledge.

### When to Use Each Model

**LSTM (Long Short-Term Memory)**
- **Best for**: Time-series data, sequential patterns
- **Use case**: Predicting future heat index based on past weather patterns
- **Requirements**: Sequential data, GPU recommended for training
- **See**: Section 1 of `all_models_demo.ipynb`

**Random Forest**
- **Best for**: Tabular data, feature importance analysis
- **Use case**: Predicting heat risk using multiple weather features
- **Requirements**: Handles mixed data types well, interpretable
- **See**: Section 2 of `all_models_demo.ipynb`

**XGBoost/AdaBoost**
- **Best for**: Tabular data, competitive performance
- **Use case**: Boosting ensemble methods for improved predictions
- **Requirements**: Usually requires more tuning than Random Forest
- **See**: Section 3 of `all_models_demo.ipynb`

### Step-by-Step Walkthrough

1. **Open `learning/all_models_demo.ipynb`**

2. **Follow Section 1: LSTM Demo**
   - Understand sequence preparation (critical for LSTM!)
   - See LSTM architecture design
   - Learn time-series specific considerations (don't shuffle!)
   - Practice scaling and inverse scaling

3. **Follow Section 2: Random Forest Demo**
   - See regression and classification examples
   - Learn feature importance analysis
   - Understand hyperparameters (n_estimators, max_depth, etc.)

4. **Follow Section 3: XGBoost/AdaBoost Demo**
   - Compare XGBoost vs AdaBoost performance
   - Understand boosting concepts
   - See feature importance for XGBoost

5. **Follow Section 4: Common Patterns**
   - Review data preprocessing patterns
   - Learn model saving/loading
   - Understand prediction patterns
   - Review evaluation patterns

### Linking Model Concepts to Demos

- **LSTM**: Focus on sequence creation and temporal order preservation
- **Random Forest**: Focus on feature importance and hyperparameter tuning
- **XGBoost/AdaBoost**: Focus on boosting parameters and comparison

## Section 5: Setting Up Your Environment

### Required Packages

Install the following packages in Google Colab:

```python
!pip install pandas numpy matplotlib seaborn scikit-learn tensorflow xgboost
```

### Installation Instructions

1. Create a new Colab notebook or open an existing one
2. In the first cell, run:

```python
!pip install pandas numpy matplotlib seaborn scikit-learn tensorflow xgboost
```

3. Wait for installation to complete

### Verification Steps

Run the following to verify installations:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn import __version__ as sklearn_version
import tensorflow as tf
import xgboost as xgb

print(f"Pandas: {pd.__version__}")
print(f"NumPy: {np.__version__}")
print(f"Scikit-learn: {sklearn_version}")
print(f"TensorFlow: {tf.__version__}")
print(f"XGBoost: {xgb.__version__}")
print(f"GPU Available: {tf.config.list_physical_devices('GPU')}")
```

All packages should import without errors.

## Section 6: Navigating the Project

### File Structure Explanation

```
ML-Team/
├── data/
│   ├── raw/              # Raw weather data location
│   └── processed/        # Processed/cleaned data location
│
├── notebooks/           # Working notebooks with TODOs
│   ├── data_preprocessing.ipynb
│   ├── target_creation.ipynb
│   ├── lstm_model.ipynb
│   ├── random_forest_model.ipynb
│   ├── xgboost_adaboost_model.ipynb
│   ├── ensemble.ipynb
│   └── accuracy.ipynb
│
├── teams/               # Team submissions
│   ├── lstm/
│   ├── random_forest/
│   └── xgboost_adaboost/
│
└── learning/           # Complete learning resources
    ├── colab_intro.ipynb
    ├── simple_modeling.ipynb
    ├── all_models_demo.ipynb
    ├── intro_setup_README.md (this file)
    └── other_resources_README.md
```

### Where to Find What

- **Learning Resources**: All in `learning/` directory
- **Working Notebooks**: All in `notebooks/` directory
- **Data Files**: `data/raw/` for input, `data/processed/` for output
- **Team Submissions**: `teams/[your_team]/` directory

### Next Steps After Learning

1. **Complete all learning notebooks** in order:
   - `colab_intro.ipynb`
   - `simple_modeling.ipynb`
   - `all_models_demo.ipynb`

2. **Read the project documentation**:
   - `data/raw/README.md` - Understand the data format
   - `data/processed/README.md` - Understand expected outputs
   - `notebooks/README.md` - Understand the workflow

3. **Start working on notebooks**:
   - Begin with `notebooks/data_preprocessing.ipynb`
   - Follow the TODO sections
   - Refer back to learning notebooks as needed

4. **Join your team**:
   - LSTM team: Work on `notebooks/lstm_model.ipynb`
   - Random Forest team: Work on `notebooks/random_forest_model.ipynb`
   - XGBoost/AdaBoost team: Work on `notebooks/xgboost_adaboost_model.ipynb`

5. **Submit your work**:
   - Save trained models to `teams/[your_team]/`
   - Follow submission guidelines in `teams/[your_team]/README.md`

## Additional Resources

- See `learning/other_resources_README.md` for comprehensive resource links
- Official documentation links for all libraries
- Tutorial videos and online courses
- Troubleshooting guides

## Getting Help

If you encounter issues:

1. Check `learning/other_resources_README.md` troubleshooting section
2. Review relevant sections in learning notebooks
3. Check `notebooks/README.md` for workflow-specific issues
4. Consult with your team members
5. Review official documentation for specific libraries

Good luck with your learning journey!




