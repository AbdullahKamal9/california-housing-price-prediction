# california-housing-price-prediction
Regression pipeline for California housing prices using sklearn, Random Forest, and stratified cross-validation.
# California Housing Price Prediction

This repository contains a simple machine learning pipeline for predicting California housing prices using a structured dataset.

## Project Overview

- Dataset: `housing.csv`
- Goal: predict `median_house_value`
- Features used:
  - `longitude`
  - `latitude`
  - `housing_median_age`
  - `total_rooms`
  - `total_bedrooms`
  - `population`
  - `households`
  - `median_income`
  - `ocean_proximity`
- Models trained:
  - `LinearRegression`
  - `DecisionTreeRegressor`
  - `RandomForestRegressor`

## What the code does

### `main.py`
- Loads `housing.csv`
- Creates a stratified train/test split based on income category
- Builds a preprocessing pipeline:
  - median imputation for numeric features
  - standard scaling for numeric features
  - one-hot encoding for `ocean_proximity`
- Trains and evaluates three regression models
- Prints cross-validation RMSE statistics

### `main_old.py`
- If `model.pkl` is missing, it trains a Random Forest model and saves `model.pkl` and `pipeline.pkl`
- If `model.pkl` exists, it loads the saved model and pipeline
- Reads `input.csv`, transforms the data, predicts prices, and writes `output.csv`

## Environment

This project uses a Python virtual environment stored in `.venv`.

## Install dependencies

Activate your virtual environment and install packages:

```powershell
cd "C:\Users\ABDULLAH\Desktop\data science course\ml housing model"
.\.venv\Scripts\Activate.ps1
python -m pip install numpy pandas scikit-learn joblib
```

## Run the project

### Train and evaluate models

```powershell
python .\main.py
```

This command trains Linear Regression, Decision Tree, and Random Forest models, then prints evaluation metrics.

### Generate predictions and save `output.csv`

```powershell
python .\main_old.py
```

The first run of `main_old.py` trains the model and saves `model.pkl` and `pipeline.pkl`. The second run performs inference on `input.csv` and creates `output.csv`.

## Performance

From the current implementation, the reported cross-validation results show:
- Linear Regression RMSE ≈ 69,000
- Decision Tree RMSE ≈ 69,000
- Random Forest RMSE ≈ 49,000

The Random Forest model performs best and is the most reliable option in this repository.

## Notes

- `main.py` is focused on training and evaluation.
- `main_old.py` includes the inference pipeline for saving predictions.
- Make sure `output.csv` is not open in another application when running inference.

## Included sample data

- `sample_input.csv`: a small subset of the dataset for quick testing and demonstration. Use this file if you don't want to include the full `housing.csv` in the repository.

If you need the full `housing.csv`, host it externally (Google Drive, Kaggle, etc.) and add a download link here instead of committing the full dataset.

