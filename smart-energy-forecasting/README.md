# Smart energy forecasting  
Forecasting hourly electricity load using classical time series methods and machine learning models.

---

## Project overview

This project aims to forecast hourly electricity load in France using real historical data from 2015 to 2020. It combines:

- classical time-series models (SARIMA, Prophet),
- feature-based machine learning models (Ridge Regression, Random Forest, XGBoost),
- extensive exploratory analysis and feature engineering.

The ultimate goal is to compare model families and highlight which approaches are most effective for short-term electricity load forecasting.

---

## Dataset

**Source**: ENTSO-E Transparency Platform  
**Frequency**: Hourly  
**Period**: 2015-01-01 → 2020-09-30  
**Target variable**: `load_mw` (electricity load in MW)

### Key characteristics

- Very strong **daily seasonality**
- Strong **weekly seasonality**
- Annual seasonality with varying amplitude
- Large fluctuations driven by weather, temperature, and industrial patterns
- Occasional missing timestamps (interpolated)

---

## 1. Exploratory time series analysis

### Key findings
- Load exhibits a **clear daily cycle** with morning and evening peaks.
- Weekends have significantly lower demand.
- Summer exhibits lower load than winter due to heating.
- Special days (holidays) show atypical shapes.
- The series is **non-stationary** with multiple overlapping seasonalities.

Plots include:
- Daily, weekly, monthly patterns  
- Rolling averages  
- Seasonal decomposition (trend, daily seasonality)

---

## 2. Feature engineering

To improve machine-learning performance, the following features were created:

### Time-based features  
- `hour`, `dayofweek`, `month`, `is_weekend`
- Sine/cosine encodings for cyclical variables

### Lag and rolling features  
- Lag 1h, 24h, 168h (one week)
- 24h rolling mean / std
- 168h rolling mean / std

### Holiday features  
- French public holidays (using `holidays` library)

---