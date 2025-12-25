# AurumForecast

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Time Series](https://img.shields.io/badge/Time--Series-Forecasting-orange.svg)
![Data Science](https://img.shields.io/badge/Data-Science-green.svg)

## Overview
**AurumForecast** is an end-to-end time-series forecasting system designed to predict gold prices over a 30-day horizon using statistical and econometric models.

The project focuses on understanding trend, seasonality, and temporal patterns in historical gold prices and selecting the most effective forecasting approach based on empirical evaluation.  
The solution is intended to support **gold exporting and importing companies** in planning revenue expectations and managing price risk.

---

## Business Objective
Gold prices are highly time-dependent and influenced by long-term trends and seasonal patterns.  
Accurate forecasting is critical for businesses involved in gold trade to:

- Anticipate short-term price movements  
- Improve revenue forecasting and planning  
- Make informed procurement and pricing decisions  

**Goal:**  
Develop a reliable forecasting model that predicts gold prices for the next 30 days using historical data.

---

## Dataset Description
- **Time Range:** January 2016 – December 2021  
- **Frequency:** Daily  
- **Features:**
  - `Date`
  - `Gold Price`

The dataset represents a univariate time series, making it well-suited for classical and advanced forecasting techniques.

---

## Methodology & System Design

### 1. Exploratory Data Analysis (EDA)
- Visualized gold price distribution over time  
- Identified long-term trends and seasonal patterns  
- Used calendar-based plots to analyze:
  - Year-wise trends
  - Month-wise seasonality  

EDA was used to **validate the presence of trend and seasonality**, guiding model selection.

---

### 2. Feature Engineering & Transformation
- Converted date column to datetime format  
- Aggregated data to monthly frequency for seasonal analysis  
- Applied transformations to stabilize variance  

---

### 3. Regression-Based Forecasting
Initial baseline models were built using:
- Linear trend model  
- Exponential model  
- Quadratic trend model  
- Additive seasonality model  
- Multiplicative seasonality model  

Models were compared using **RMSE**, with the **linear model** performing best among regression approaches.

---

### 4. Data-Driven Forecasting (Exponential Smoothing)
Evaluated models from the Exponential Smoothing family:
- **Simple Exponential Smoothing** (Level)
- **Holt’s Method** (Level + Trend)
- **Holt-Winters Method** (Level + Trend + Seasonality)

**Simple Exponential Smoothing** achieved the lowest RMSE among data-driven approaches.

---

### 5. Stationarity & Model-Driven Forecasting
Before applying ARIMA-based models, stationarity was assessed:

- Conducted **ADF (Augmented Dickey-Fuller) test**
- Identified non-stationarity in the original series
- Applied:
  - Box-Cox transformation
  - Differencing
- Revalidated stationarity using ADF

ACF and PACF plots were analyzed to guide parameter selection.

---

### 6. ARIMA vs SARIMAX
- **ARIMA** captured trend but failed to model seasonality effectively  
- **SARIMAX** successfully captured both trend and seasonal components  

Final model selection was based on:
- RMSE comparison
- Ability to model observed seasonality
- Forecast stability

👉 **SARIMAX** achieved the lowest RMSE and best qualitative fit and was selected as the final model.

---

## Results & Insights
- Gold prices exhibit clear seasonal and trend components  
- SARIMAX outperformed regression, ETS, and ARIMA models  
- The final model provides stable and interpretable 30-day forecasts  

This makes AurumForecast suitable for **short-term financial planning and price monitoring**.

---

## Deployment
The finalized SARIMAX model was deployed using **Streamlit**, allowing users to:
- Specify the forecast horizon (number of days)
- Visualize historical prices alongside forecasts
- Interact with model outputs in real time

Deployment logic is implemented in:
GPP_app.py


This demonstrates **end-to-end ownership**, from modeling to a user-facing application.

---

## Tech Stack
- **Language:** Python  
- **Data Handling:** Pandas, NumPy  
- **Visualization:** Matplotlib, Seaborn  
- **Time Series Modeling:** Statsmodels  
- **Statistical Tests:** ADF Test  
- **Forecasting Models:**  
  - Regression-based models  
  - Exponential Smoothing (SES, Holt, Holt-Winters)  
  - ARIMA  
  - SARIMAX  
- **Evaluation Metric:** RMSE  
- **Deployment:** Streamlit  

---

## Repository Structure
```
aurum-forecast/
│
├── Gold_Price_Forecast.ipynb # Time-series analysis & model development
├── GPP_app.py # Streamlit deployment
├── requirements.txt # Dependencies
├── .gitignore # Ignored files
├── LICENSE # MIT License
└── README.md # Project documentation
```


---

## Key Engineering Decisions
- Evaluated multiple forecasting paradigms before finalizing the model  
- Ensured stationarity prior to ARIMA-based modeling  
- Prioritized interpretability and empirical performance over complexity  
- Selected SARIMAX to explicitly model seasonality  

---

## Learnings
- Importance of stationarity in time-series modeling  
- Trade-offs between regression, data-driven, and model-driven approaches  
- Practical application of ADF, ACF, and PACF diagnostics  
- Deploying forecasting models for real-world usability  

---

## Future Improvements
- Incorporate exogenous macroeconomic indicators  
- Extend forecasting horizon with uncertainty bounds  
- Add automated model retraining  
- Enhance Streamlit UI for business users  

---

## License
This project is licensed under the **MIT License**.

---

## Author
**Kumaran Elumalai**  
AI / ML Engineer | Data Scientist  

🔗 GitHub: https://github.com/Kumaran-Elumalai  
🔗 LinkedIn: https://linkedin.com/in/kumaran-elumalai
