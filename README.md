# ADEase Time Series Forecasting

## 📌 Project Overview

This project focuses on forecasting daily Wikipedia page views across multiple language editions using classical time-series forecasting techniques.

The objective is to analyze historical traffic patterns, identify seasonality and trends, build forecasting models, and predict future page views with high accuracy.

The project evaluates and compares multiple forecasting algorithms including:

* ARIMA
* SARIMA
* SARIMAX
* Facebook Prophet

The final model selection is based on forecasting accuracy measured using MAPE (Mean Absolute Percentage Error).

---

# 🎯 Problem Statement

Wikipedia page traffic exhibits:

* Long-term trends
* Weekly seasonality
* Irregular fluctuations
* Language-specific behavior

The goal is to forecast future page views for multiple languages:

* English
* German
* French
* Spanish
* Russian
* Japanese
* Chinese

using historical traffic data.

---

# 📊 Dataset Description

The dataset contains daily Wikipedia page view statistics.

### Features

| Feature             | Description                         |
| ------------------- | ----------------------------------- |
| Date                | Observation Date                    |
| Language            | Wikipedia Language                  |
| Page Views          | Daily Traffic Count                 |
| Exogenous Variables | External predictors used in SARIMAX |

---

# 🛠 Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Statsmodels
* Prophet
* Scikit-Learn
* Jupyter Notebook

---

# 📂 Project Workflow

## 1. Data Collection

Load historical page view data.

---

## 2. Data Cleaning

* Missing value handling
* Datetime conversion
* Index creation
* Frequency alignment

---

## 3. Exploratory Data Analysis

Performed analysis on:

* Trend behavior
* Weekly seasonality
* Traffic spikes
* Language-wise comparison
* Rolling statistics

Visualizations include:

* Time series plots
* Moving averages
* Seasonal decomposition
* Forecast comparison charts

---

# 🔍 Statistical Analysis

## Stationarity Analysis

Time-series stationarity was examined before model building.

Methods used:

### Augmented Dickey-Fuller (ADF) Test

Used to determine whether:

* differencing is required
* trend exists
* series is stationary

---

## Seasonal Analysis

Weekly seasonality was identified across language datasets.

Seasonal period used:

```text
7 days
```

This weekly pattern was incorporated into SARIMA and SARIMAX models.

---

# 🤖 Forecasting Algorithms Used

---

## 1. ARIMA

### AutoRegressive Integrated Moving Average

Model Components:

* AR(p) → Autoregressive term
* I(d) → Differencing term
* MA(q) → Moving average term

Model form:

```text
ARIMA(p,d,q)
```

Example configuration:

```python
ARIMA(3,1,3)
```

Used as a baseline forecasting model for all language series.

---

## 2. SARIMA

### Seasonal ARIMA

Captures:

* Trend
* Seasonality
* Autocorrelation

Model form:

```text
SARIMA(p,d,q)(P,D,Q,s)
```

where:

```text
s = 7
```

for weekly seasonality.

Example:

```python
SARIMA(3,1,3)(1,1,1,7)
```

SARIMA was built for:

* German
* English
* Spanish
* French
* Japanese
* Russian
* Chinese

language traffic series.

---

## 3. SARIMAX

### Seasonal ARIMA with Exogenous Variables

SARIMAX extends SARIMA by incorporating external predictors.

Advantages:

* Uses additional explanatory variables
* Better captures external influences
* Often improves forecasting accuracy

Example:

```python
SARIMAX(
    order=(3,1,3),
    seasonal_order=(1,1,1,7),
    exog=external_features
)
```

English series forecasting achieved lower MAPE using SARIMAX compared to SARIMA, making it the preferred model.

---

## 4. Facebook Prophet

Prophet was implemented as an additional forecasting framework.

Key capabilities:

* Automatic trend detection
* Seasonality modeling
* Holiday effect modeling
* Robust forecasting

Libraries used:

```python
prophet
cmdstanpy
```

for model training and prediction.

---

# 📈 Model Evaluation

## Performance Metric

### Mean Absolute Percentage Error (MAPE)

Formula:

```text
MAPE = (1/n) Σ |(Actual - Forecast)/Actual| × 100
```

Lower MAPE indicates better forecasting performance.

---

# 📊 Sample Forecasting Results

| Language | Model   | Approx. MAPE |
| -------- | ------- | ------------ |
| English  | SARIMAX | 0.063        |
| German   | SARIMA  | 0.072        |
| French   | SARIMA  | 0.068        |
| Japanese | SARIMA  | 0.078        |
| Chinese  | SARIMA  | 0.035        |
| Russian  | SARIMA  | 0.095        |

## Model selection was based on the lowest forecasting error observed during validation.

# 📉 Visualizations

The project includes:

* Historical Traffic Trends
* Forecast Curves
* Actual vs Predicted Comparison
* Seasonal Patterns
* Rolling Mean Analysis
* Language-wise Forecast Evaluation

---

# 📁 Project Structure

```text
ADEase-Time-Series-Forecasting/
│
├── ADEase_Time_Series_Forecasting.ipynb
├── ADEase_Time_Series_Forecasting.pdf
├── datasets/
│   ├── train.csv
│   ├── test.csv
│   └── exogenous_features.csv
│
├── images/
│   ├── trend_analysis.png
│   ├── seasonal_decomposition.png
│   ├── arima_forecast.png
│   ├── sarima_forecast.png
│   └── prophet_forecast.png
│
├── requirements.txt
└── README.md
```

---

---

# 📋 Key Methods Used

### Time Series Analysis

* Trend Analysis
* Seasonal Analysis
* Rolling Statistics
* Stationarity Testing

### Statistical Forecasting

* ARIMA
* SARIMA
* SARIMAX

### Machine Learning Forecasting

* Facebook Prophet

### Model Evaluation

* Train/Test Split
* Forecast Validation
* MAPE Calculation

---

# 🔑 Key Findings

* Strong weekly seasonality exists across language traffic series.
* Seasonal models outperform simple ARIMA models.
* SARIMAX improves forecasting when exogenous variables are available.
* Chinese and English series achieved the lowest forecasting errors.
* Prophet provides a robust alternative for long-term forecasting.

---

# 📚 Conclusion

This project demonstrates a complete end-to-end time-series forecasting pipeline using classical statistical forecasting techniques and Prophet. Through trend analysis, seasonality modeling, and rigorous evaluation, accurate forecasts were generated for multiple Wikipedia language traffic series.

The project highlights the effectiveness of SARIMA/SARIMAX models in capturing weekly seasonal patterns and provides a strong foundation for advanced forecasting applications.
