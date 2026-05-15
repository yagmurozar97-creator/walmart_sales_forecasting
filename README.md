# Walmart Weekly Sales Forecasting with XGBoost

This project forecasts Walmart's total weekly sales using machine learning and time series feature engineering techniques. The analysis combines exploratory data analysis (EDA), seasonal trend detection, lag-based feature creation, and XGBoost regression to generate accurate sales forecasts and support data-driven retail planning.

---

## Business Objective

Retail companies depend on accurate sales forecasts to optimize inventory, staffing, budgeting, and promotional strategies.

The objective of this project is to:

- Analyze historical weekly sales patterns
- Identify seasonality and holiday effects
- Engineer lag and rolling statistical features
- Build a machine learning model to forecast future sales
- Generate a one-step-ahead prediction for the next week

---

## Dataset Information

The dataset contains weekly Walmart sales data from 45 stores covering the period from **February 5, 2010 to October 26, 2012**.

### Variables

| Variable | Description |
|-----------|-------------|
| Store | Store identifier |
| Date | Week ending date |
| Weekly_Sales | Weekly sales revenue |
| Holiday_Flag | Indicates whether the week includes a holiday |
| Temperature | Regional air temperature |
| Fuel_Price | Regional fuel price |
| CPI | Consumer Price Index |
| Unemployment | Regional unemployment rate |

---

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- XGBoost
- Jupyter Notebook

---

## Exploratory Data Analysis

Key findings from the exploratory analysis:

- The dataset contains 6,435 weekly observations.
- Average weekly sales are approximately **$1.05 million per store**.
- Significant performance differences exist across stores.
- Weekly sales exhibit clear seasonal patterns.
- Holiday weeks generate moderately higher sales compared to non-holiday periods.
- Sales fluctuations increase during major shopping seasons.

---

## Feature Engineering

To improve forecasting performance, multiple time series features were created.

### Temporal Features
- Year
- Month
- Week
- Quarter

### Lag Features
- Lag_1
- Lag_2
- Lag_4
- Lag_8
- Lag_12

### Rolling Statistics
- Rolling_Mean_2
- Rolling_Mean_4
- Rolling_Std_4

Rows containing missing values introduced by lag and rolling calculations were removed before model training.

---

## Feature Importance Analysis

Feature importance analysis identified the most influential predictors of future sales:

1. Week
2. Rolling_Mean_2
3. Lag_1
4. Rolling_Std_4
5. Lag_8
6. Lag_2

These findings indicate that seasonality, recent sales history, and short-term sales volatility are the strongest drivers of future sales performance.

---

## Model Development

An XGBoost Regressor was used to forecast total weekly sales.

### Final Model Features

- Week
- Rolling_Mean_2
- Lag_1
- Rolling_Std_4
- Lag_8
- Lag_2

### Model Parameters

- n_estimators = 200
- learning_rate = 0.05
- max_depth = 6
- random_state = 42

The dataset was split chronologically using an 80/20 ratio to preserve temporal order and evaluate performance on future observations.

---

## Model Performance

| Metric | Value |
|--------|--------:|
| MAE | ~44,000 |
| RMSE | ~63,000 |

Considering that total weekly sales across all stores are approximately **$45 million**, the model demonstrates strong forecasting accuracy with relatively low prediction error.

---

## Forecast Validation

A validation table was created to compare:

- Actual sales values
- Predicted sales values
- Forecast errors
- Absolute forecast errors

The predicted values closely followed the actual sales trends, indicating that the model successfully captured overall sales dynamics and short-term fluctuations.

---

## Future Weekly Sales Forecast

The final model was used to generate a one-step-ahead forecast for the following week.

> **Next Week Forecast: $44,890,072**

This forecast was generated using recent lag values, rolling averages, and short-term volatility indicators derived from historical sales behavior.

---

## Key Insights

- Weekly sales exhibit strong seasonal behavior.
- Recent sales patterns are highly predictive of future sales.
- Short-term rolling averages significantly improve forecasting performance.
- Sales volatility also contributes to future demand estimation.
- XGBoost effectively captures nonlinear relationships in retail time series data.
- Machine learning can provide accurate and actionable forecasts for retail planning.

---

## Business Applications

This forecasting approach can support:

- Inventory optimization
- Workforce planning
- Promotional scheduling
- Revenue forecasting
- Budget preparation
- Demand planning

---

## Project Structure

```text
Walmart-Sales-Forecasting-XGBoost/
│
├── walmart_sales_forecast.ipynb
├── Walmart.csv
└── README.md

````

## Conclusion

This project demonstrated how time series feature engineering and XGBoost regression can be combined to build an effective retail sales forecasting model.

By incorporating lag variables, rolling statistics, and seasonal indicators, the model successfully captured short-term sales dynamics and recurring seasonal patterns. The final model achieved strong alignment between actual and predicted sales values while also generating a realistic one-step-ahead forecast for future weekly sales.

Overall, the project highlights the practical value of machine learning techniques in retail analytics, demand forecasting, and operational planning.
