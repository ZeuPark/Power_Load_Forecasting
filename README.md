# Power Load Forecasting

**Objective**  
Short-term and daily electricity demand forecasting using statistical and machine learning models for grid operation and energy market applications.

## Dataset
- **Source**: [Dataset name or link] (or note if synthetic)
- **Coverage**: [e.g., Hourly data, Jan 2020 – Dec 2024]
- **Features**: Load, temperature, calendar variables
- **Size**: ~X,XXX records
- **Missing Values**: [Describe handling]

## Methodology
1. Data preprocessing & feature engineering:
   - Lag features
   - Seasonal indicators
   - Weather integration (if available)
2. Baseline Model:
   - Naive seasonal persistence
3. Advanced Models:
   - SARIMAX / Prophet for statistical forecasting
   - Gradient Boosting (LightGBM, XGBoost) for ML-based forecasting
4. Evaluation:
   - Rolling-origin cross-validation
   - Metrics: MAE, RMSE, SMAPE

## Results
| Model            | MAE   | RMSE  | SMAPE  |
|------------------|-------|-------|--------|
| Naive Seasonal   | X.XX  | X.XX  | XX.X%  |
| LightGBM         | X.XX  | X.XX  | XX.X%  |

**Sample Forecast Plot**  
![forecast](results/sample_forecast.png)

## How to Run
```bash
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python src/main.py
Repository Structure
bash
Copy
Edit
power_load_forecasting/
│
├── data/               # Raw and processed datasets
├── notebooks/          # Exploratory data analysis and experiments
├── src/                # Main source code
├── results/            # Forecast plots and evaluation metrics
├── configs/            # Model and training configurations
├── requirements.txt    # Python dependencies
└── README.md           # Project documentation
Future Work
Integrate probabilistic forecasting

Extend to real-time data pipelines

Combine with price prediction for dispatch optimization

yaml
Copy
Edit

---

If you follow this and **commit/push it now**, your `power_load_forecasting` repo will already look like a professional, finished project skeleton — even before the actual models are added.  

I can also **write your `src/main.py` skeleton** so it:
- Loads a sample dataset
- Creates a simple naive forecast
- Saves a sample plot  
… so that recruiters can **clone → run → see output** in less than a minute.  

Do you want me to make that `main.py` next so the repo is runnable from day one?