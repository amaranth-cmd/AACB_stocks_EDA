##Project 2 – Exploratory Data 
Analysis of Financial Time Series

##Overview

This project performs an exploratory data analysis (EDA) on daily stock market data to understand its temporal structure, statistical properties, and suitability for time-series modeling. The analysis focuses on identifying trends, assessing stationarity, and exploring short-term dynamics using transformations and diagnostic models.
Rather than aiming for production-level forecasting or deployment, time-series models are used as exploratory tools to support insights about the data’s behavior.

##Objectives

The primary goals of this project are to:
1. Understand the shape and structure of daily stock price data
2. Identify temporal trends and non-stationarity
3. Transform prices into daily returns to improve stationarity
4. Explore whether returns exhibit autocorrelation
5. Compare naive and informed ARIMA models to assess whether model identification techniques improve adequacy
6. Communicate insights through clear, captioned visualizations

##Dataset Description
The dataset consists of daily stock market observations and includes:

-date: Trading date
-close: Daily closing price
-ticker: Asset identifier

The dataset is indexed by date to preserve chronological ordering and enable time-aware analysis.

##Initial Questions
Before analysis, the following exploratory questions were defined:

-Does the stock price series exhibit a long-term trend?
-Are daily returns stationary?
-Do returns behave like white noise, or is there evidence of autocorrelation?
-Does incorporating ACF/PACF-based model identification improve ARIMA model adequacy compared to naive specifications?

##Workflow
1. Data Preparation
Converted the date column to datetime
Set date as the index to specifically harness the temporal order of the set. 
Sorted observations chronologically
Verified monotonicity and absence of duplicate timestamps
3. Exploratory Visualization – Phase 1
Time-series plot of closing prices
Distribution of prices
Identification of non-stationary behavior
Sanity checks for expected patterns (trend presence)
4. Transformation to Returns
Computed daily returns using percentage change
Examined return series for mean stability and volatility
Visualized returns over time and through a linegraph
6. Stationarity Testing
Applied the Augmented Dickey–Fuller (ADF) test
Strong rejection of the unit-root hypothesis confirmed stationarity of returns
7. Time-Based Train–Test Split
Split the return series using an 80/20 chronological split
Avoided random shuffling to prevent data leakage
Visualized the split for verification
8. Exploratory Time-Series Modeling
ARIMA models were fitted for diagnostic purposes, not deployment.
Models evaluated:
ARIMA(0,0,0): White-noise baseline
ARIMA(1,1,1): Naively specified(though not included) 
ARIMA(2,0,1): ACF/PACF-informed model
9. Model Diagnostics
Compared models using Akaike Information Criterion (AIC)
Evaluated residuals using the Ljung–Box test
Assessed normality using Jarque–Bera statistics
Interpretation of Forecasts (Red Line)
The forecast line (red) represents expected future returns, not prices.

Key points:
Returns naturally fluctuate around zero
Forecasts appear flat because returns have low predictability
Lack of tight tracking is expected and does not indicate poor modeling
Performance is evaluated via residual diagnostics, not visual fit alone
A well-performing return model produces:
Near-zero mean forecasts
White-noise residuals
No systematic structure left unexplained

##Key Findings
Stock prices are non-stationary and trend upward over time
Daily returns are stationary and centered near zero
Returns exhibit weak but non-negligible autocorrelation
ACF/PACF-informed ARIMA models outperform naive specifications
ARIMA(2,0,1) produced the lowest AIC and passed residual diagnostics
Residual non-normality reflects heavy tails typical of financial data

##Limitations
Financial returns are inherently noisy and difficult to predict
ARIMA models capture only linear dependencies
No external variables (macroeconomic factors, volume) were included
The project focuses on exploration, and engineering not predictive optimization

##Conclusion(lessons) 

This exploratory analysis demonstrates the importance of transforming financial price data before time-series modeling. While raw prices are unsuitable for many statistical models due to non-stationarity or having trends, daily returns provide a stable basis for exploration. 
Diagnostic modeling shows that incorporating correlation structure improves statistical adequacy, though predictability remains limited.
Overall, the project highlights how exploratory data analysis and diagnostic modeling can be combined to reveal meaningful insights into financial time-series behavior.

##Tools & Libraries
Python
pandas
numpy
matplotlib
statsmodels
scikit-learn
Notes
This project was completed as part of Project 2: Exploratory Data Analysis.
No deployment or production system was required or implemented and the data set is included in the repository. 

##Author
Amaranth Sebeo Madise 
