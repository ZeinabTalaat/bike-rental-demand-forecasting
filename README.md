# Bike Rental Demand Forecasting & Model Interpretability

A time-series forecasting project that analyzes historical bike rental demand, predicts future rentals using SARIMAX, and interprets the impact of different features using SHAP.

## Project Overview

This project aims to forecast daily bike rental demand using historical data from the UCI Bike Sharing Dataset.

It combines:
- Time Series Analysis
- Seasonal Differencing
- SARIMAX Forecasting
- Model Evaluation
- SHAP-based Model Interpretability

## Dataset

**Source:** [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset)

- Dataset file: `day.csv`
- Records: 731 daily observations
- Target variable: `cnt` (Total daily bike rentals)
- Period: 2011–2012

## Project Workflow

1. **Data Understanding & Exploration**
   - Dataset inspection
   - Statistical summaries
   - Rental demand visualization

2. **Data Preprocessing**
   - Date handling
   - Missing values and duplicate checks
   - Time-series preparation

3. **Stationarity Analysis**
   - Augmented Dickey-Fuller (ADF) test
   - Weekly seasonal differencing (lag = 7)

4. **Time Series Forecasting**
   - SARIMAX model
   - Seasonal order: (1, 1, 1, 7)
   - Final 60 observations used as the test set

5. **Model Evaluation**
   - MAE
   - RMSE
   - MAPE
   - WAPE
   - sMAPE
   - Seasonal Naive baseline comparison

6. **Model Interpretability**
   - Random Forest as a supplementary model
   - SHAP feature importance analysis
   - Leakage-prone target-derived features excluded

## Technologies & Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Scikit-learn
- SHAP
- Jupyter Notebook

## Forecasting Results

| Metric | SARIMAX |
|---|---:|
| MAE | 1272.19 |
| RMSE | 1822.18 |
| MAPE | 70.56% |
| WAPE | 28.23% |
| sMAPE | 31.83% |

SARIMAX outperformed the Seasonal Naive baseline in both MAE and RMSE.

## SHAP Feature Importance

The supplementary Random Forest model identified the following influential features:

| Feature | Importance |
|---|---:|
| temp | 45.04% |
| yr | 25.08% |
| season | 9.41% |
| hum | 8.91% |
| mnth | 4.05% |

Temperature and year were the most influential features in the supplementary model's predictions.

**Note:** SHAP explains the Random Forest model, not the SARIMAX forecasting model. Feature importance indicates model contribution, not causation.

## Key Findings & Limitations

- Weekly seasonal differencing improved stationarity.
- SARIMAX performed better than the seasonal naive baseline on MAE and RMSE.
- Remaining residual autocorrelation indicates that the forecasting model can still be improved.
- MAPE is sensitive to observations with small actual rental counts.
- SHAP analysis provides additional interpretability through a separate Random Forest model.

## Project Structure

```text
Bike-Rental-Demand-Forecasting/
│
├── Bike_Rental_Forecasting.ipynb
├── outputs/
│   ├── forecast_results.csv
│   ├── model_metrics.csv
│   └── shap_feature_importance.csv
│
├── Bike_Rental_Forecasting_Whitepaper_Final.pdf
└── README.md
```

## Author

Data Science Student | Aspiring Data Analyst

## Acknowledgment

Dataset provided by the UCI Machine Learning Repository.
