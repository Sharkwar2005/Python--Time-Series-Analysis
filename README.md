# Time Series Analysis and Forecasting of Daily Minimum Temperatures

## ✦ Project Overview
This project involves a comprehensive time series analysis of daily minimum temperatures to forecast future values. The analysis explores the characteristics of the time series dataset, identifies its components and temporal dependencies, and applies advanced smoothing and decomposition techniques to build a robust predictive model. 

## ✦ Problem Statement
Mathematical time series models, such as ARIMA and exponential smoothing, strictly require continuous, numeric, and uniform sequences of data. Leaving anomalous entries or extreme physiological outliers in the dataset can cause type errors, skew rolling statistics, manipulate ACF/PACF plots, and artificially inflate the error metrics of forecasting models. The challenge is to effectively clean the data, identify underlying seasonal patterns, and accurately model the temporal structure to predict future temperature fluctuations.

## ✦ Goals
* **Data Preparation & Cleaning:** Parse datetime objects, check for duplicate dates, identify missing timestamps, and use regular expressions to strip non-numeric characters from anomalous entries (e.g., `?0.2`).
* **Outlier Detection & Treatment:** Utilize the Interquartile Range (IQR) method to identify extreme temperature values and clip them to calculated bounds to limit their impact while preserving structural continuity.
* **Exploratory Data Analysis:** Plot the original time series and overlay yearly data to visually confirm consistent seasonal cycles across different years.
* **Modeling & Forecasting:** Build and evaluate an ARIMA or SARIMA model, analyze decomposition residuals to determine if they behave like white noise, and evaluate out-of-sample forecasting performance using appropriate metrics.

## ✦ Key Insights from the Data Analysis
* **Data Quality & Anomalies:** A continuity check generated against expected timestamps revealed two missing dates: 1984-12-31 and 1988-12-31. Additionally, anomalous string entries required regex cleaning to successfully cast the entire target column to a `float64` data type.
* **Outlier Impact:** The IQR analysis flagged 28 extreme outliers, representing approximately 0.76% of the dataset. These values were safely clipped to an acceptable lower bound of 0.3°C and an upper bound of 21.9°C to maintain the time series' continuity without creating additional gaps.
* **Seasonal Patterns:** Visualizing the data broken down by individual years across a shared 365-day axis revealed highly predictable seasonal cycles. The data showed consistent temperature dips during the middle of the year (winter) and peaks at the beginning and end of the year (summer).

## ✦ Tools & Technologies
* **Language:** Python
* **Data Manipulation & Math:** NumPy, Pandas, SciPy
* **Time Series Modeling:** Statsmodels (ARIMA, Exponential Smoothing, Holt-Winters, Seasonal Decompose, KPSS, Ljung-Box)
* **Machine Learning & Evaluation:** Scikit-learn (train-test split, mean squared error, mean absolute percentage error)
* **Visualization:** Matplotlib, ACF/PACF plots

## ✦ Conclusion
By applying rigorous data quality checks, regular expressions for anomaly cleaning, and IQR-based outlier clipping, the raw temperature data was successfully transformed into a reliable, continuous time series. This robust preprocessing pipeline ensured that the subsequent ARIMA/SARIMA models could accurately capture temporal dependencies, effectively evaluate residual white noise, and provide highly reliable forecasts for out-of-sample temperature observations.
