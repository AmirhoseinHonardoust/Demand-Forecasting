# Demand Forecasting (Time-Series)
End-to-end demand forecasting with Python using synthetic time-series sales data. Includes data generation, cleaning, ARIMA/SARIMA model selection by AIC, evaluation with RMSE and MAPE, and 90-day forecasts with confidence intervals. Reproducible scripts and visualizations for portfolio showcase.

Forecast daily sales with ARIMA/SARIMA on synthetic data. Includes generation, cleaning, train/validation split, AIC-based model search, evaluation (RMSE/MAPE), and 90-day forecast with confidence intervals. Production-ready scripts and charts for portfolio showcase.
 
---

## Features
- Synthetic daily sales generator (trend + weekly + annual seasonality + noise)
- Train/validation split
- ARIMA/SARIMA model search by AIC (weekly seasonality)
- Metrics: RMSE, MAPE
- 90-day forecast with confidence intervals
- Plots: history vs. forecast, residual diagnostics
- Deterministic seeding for reproducibility

---

## Project Structure
```
demand-forecasting/
├─ README.md
├─ LICENSE
├─ requirements.txt
├─ data/
│  └─ generate_timeseries.py
├─ src/
│  ├─ forecast_arima.py
│  └─ metrics.py
└─ outputs/
   └─ figures & reports
```

---

## Setup
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
```

---

## Generate Synthetic Data
```bash
python data/generate_timeseries.py --start 2023-01-01 --end 2024-12-31 --seed 42 --out data/daily_sales.csv
```

---

## Run Forecast
```bash
python src/forecast_arima.py --input data/daily_sales.csv --horizon 90 --val_days 60 --outdir outputs
```

**Outputs**
- `outputs/metrics.json` – RMSE & MAPE (validation)
- `outputs/forecast.csv` – point forecast + confidence intervals
- `outputs/fig_history_forecast.png`
- `outputs/fig_residuals.png`

---

## Sample Results

### Forecast vs History
<img width="1920" height="640" alt="fig_history_forecast" src="https://github.com/user-attachments/assets/89f34f31-bba2-4225-a6f0-c5c55fe09f79" />

### Residual Diagnostics
<img width="1920" height="640" alt="fig_residuals" src="https://github.com/user-attachments/assets/983d4cbd-5162-45c3-9b73-b839049987e2" />

### Key Metrics
| Metric | Value |
|--------|-------|
| RMSE   | **2.11** |
| MAPE   | **2.77%** |
| ARIMA Order | (2,1,2) |
| Seasonal Order | (0,1,1,7) |
| AIC | 2836.7 |

---

## Data Schema
| column | description       |
|--------|-------------------|
| date   | daily timestamp   |
| sales  | units sold (int)  |
