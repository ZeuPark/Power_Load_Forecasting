# Power Load Forecasting

Short-term and day-ahead electricity load forecasting project.  
This repository includes a reproducible pipeline for data preprocessing, feature engineering, model training, evaluation, and optional API deployment.

---

## 1. Objective
- Forecast electricity demand **15 minutes to 24 hours ahead**.
- Primary metric: **SMAPE**, secondary: MAE, RMSE.
- Provide both research results (notebooks) and a deployable inference API.

---

## 2. Project Structure
```
power-load-forecasting/
├─ data/
│   ├─ raw/                  # Original data (before preprocessing)
│   └─ processed/            # Cleaned & feature-engineered data
├─ notebooks/                # Jupyter notebooks for EDA & modeling
├─ src/                      # Python modules
│   ├─ data_prep.py
│   ├─ features.py
│   ├─ train.py
│   ├─ evaluate.py
│   └─ service/api.py
├─ experiments/              # Model artifacts & metrics
├─ requirements.txt
└─ README.md
```

---

## 3. Data
Expected columns in `data/raw/*.csv`:
- **timestamp**: DateTime in `YYYY-MM-DD HH:MM:SS` format
- **load**: Electricity consumption (kW or MW)
- Optional: temperature, humidity, is_weekend, is_holiday, etc.

Example:
| timestamp           | load  | temperature | is_weekend |
|---------------------|-------|-------------|------------|
| 2025-08-01 00:00:00 | 412.5 | 19.2        | false      |
| 2025-08-01 00:15:00 | 405.8 | 18.9        | false      |

---

## 4. Pipeline Overview
1. **Data Preparation** (`src/data_prep.py`)  
   - Handle missing values, fix timezone, resample to uniform frequency.
2. **Feature Engineering** (`src/features.py`)  
   - Calendar features, lags, rolling statistics, weather joins.
3. **Model Training** (`src/train.py`)  
   - Baselines: Naive, Seasonal Naive
   - Models: LightGBM, XGBoost, CatBoost
4. **Evaluation** (`src/evaluate.py`)  
   - SMAPE, MAE, RMSE, breakdown by horizon & time-of-day.
5. **API Service** (`src/service/api.py`)  
   - Optional FastAPI endpoint `/predict`.

---

## 5. How to Run
### Create virtual environment
```bash
python -m venv .venv
.venv\Scripts\activate    # Windows
source .venv/bin/activate # Mac/Linux
```

### Install dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Preprocess data
```bash
python -m src.data_prep --config config/default.yaml
```

### Feature engineering
```bash
python -m src.features --config config/default.yaml
```

### Train model
```bash
python -m src.train --config config/default.yaml
```

### Evaluate
```bash
python -m src.evaluate --run_dir experiments/runs/<your_run>
```

---

## 6. Example Output
```
SMAPE: 8.21%
MAE: 21.5 kW
RMSE: 30.2 kW
```
*Figure 1: Actual vs Forecasted load plot*

---

## 7. Roadmap
- Add renewable generation & price signals as exogenous features.
- Try deep learning baselines (LSTM, TFT).
- Deploy API with Docker on Oracle Cloud.
- Build a small dashboard (Vercel) to visualize forecasts.

---

## 8. License
MIT License
