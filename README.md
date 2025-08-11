# Power Load Forecasting

**Objective**  
Short-term and daily electricity demand forecasting using statistical and machine learning models, designed for grid operation and energy market applications.

## Dataset
- **Source**: [Name of dataset + link or note if synthetic]
- **Coverage**: e.g., Hourly data, Jan 2020 – Dec 2024
- **Features**: Load, temperature, calendar variables
- **Size**: ~X,XXX records
- **Missing Values**: [handling method]

## Methodology
1. Data preprocessing & feature engineering (lags, seasonality, weather)
2. Baseline: Naive seasonal persistence
3. Models:
   - SARIMAX / Prophet
   - Gradient Boosting (LightGBM, XGBoost)
4. Evaluation: Rolling-origin cross-validation (MAE, RMSE, SMAPE)

## Results
| Model            | MAE   | RMSE  | SMAPE  |
|------------------|-------|-------|--------|
| Naive Seasonal   | X.XX  | X.XX  | XX.X%  |
| LightGBM         | X.XX  | X.XX  | XX.X%  |

**Sample Forecast Plot**  
![forecast](results/sample_forecast.png)

## How to Run
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python src/main.py
