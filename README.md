# Portfolio Market Risk & Value-at-Risk Analysis

## Historical, Parametric and Gaussian Monte Carlo VaR with Out-of-Sample Backtesting

A quantitative analysis of market risk in a Brazilian equity portfolio using real historical market data.

The project investigates whether Value-at-Risk (VaR) can provide a useful statistical estimate of future portfolio losses and evaluates its performance through out-of-sample backtesting.

---

## Project Overview

Value-at-Risk (VaR) is one of the most widely used measures of financial market risk.

This project applies three VaR methodologies to a Brazilian equity portfolio:

- Historical VaR
- Parametric VaR
- Gaussian Monte Carlo VaR

The analysis goes beyond calculating VaR by examining portfolio diversification, volatility, correlations, return distributions and tail risk.

The model is then evaluated using an out-of-sample backtest and statistical coverage tests.

### Main question

> Can Value-at-Risk calibrated on historical data provide a reliable estimate of future losses when market conditions change?

The COVID-19 market crash provides a natural stress period to investigate this question.

---

## Portfolio

The study uses a portfolio of Brazilian listed companies based on the original case-study allocation.

Historical ticker symbols are used where necessary to preserve the economic composition of the portfolio during the study period.

The analysis covers the period surrounding the COVID-19 market shock.

---

## Methodology

### 1. Data Collection

Historical market prices are obtained using Yahoo Finance through the `yfinance` Python library.

The analysis includes:

- Historical price data
- Daily returns
- Data cleaning
- Historical ticker identification
- Corporate-action considerations

---

### 2. Exploratory Data Analysis

The project investigates:

- Asset price performance
- Portfolio performance
- Daily returns
- Volatility
- Correlation between assets
- Pre- and post-COVID market behaviour

Asset volatility is measured using the standard deviation of daily returns.

---

### 3. Portfolio Construction

The portfolio return is calculated as the weighted combination of individual asset returns.

Portfolio volatility is then compared with the volatility of individual assets and the weighted average volatility.

This allows the diversification effect to be quantified.

---

### 4. Return Distribution

The project evaluates whether portfolio returns are approximately Normally distributed.

A Shapiro-Wilk test is used to assess the normality assumption.

This is important because the Parametric and Gaussian Monte Carlo VaR approaches rely on a Normal distribution assumption.

---

## Value-at-Risk Models

### Historical VaR

Historical VaR uses the empirical distribution of observed portfolio returns.

At the 95% confidence level:

> Historical VaR corresponds to the 5th percentile of the return distribution.

No parametric distribution is imposed on the returns.

---

### Parametric VaR

Parametric VaR assumes that returns follow a Normal distribution.

The model uses:

- Mean return
- Standard deviation
- 95% confidence level

This provides a useful benchmark for comparison with Historical VaR.

---

### Gaussian Monte Carlo VaR

A Monte Carlo simulation is performed by generating a large number of hypothetical returns from a fitted Normal distribution.

The simulation is used to estimate the 5th percentile of the simulated return distribution.

The model is explicitly described as **Gaussian Monte Carlo** because it inherits the Normal-distribution assumption of the parametric approach.

---

## Tail-Risk Analysis

VaR only identifies the threshold at which the worst 5% of outcomes begins.

Therefore, the project also evaluates:

### Expected Shortfall

Expected Shortfall measures the average loss beyond the VaR threshold.

This provides additional information about the severity of losses in the tail.

### Maximum Drawdown

Maximum drawdown measures the largest peak-to-trough decline experienced during the analysis period.

### Rolling VaR

A rolling VaR framework is used to examine how the estimated risk changes through time and across different market regimes.

---

## Model Validation

Calculating VaR is only the first step.

The model is evaluated using out-of-sample backtesting.

A VaR model at the 95% confidence level should theoretically experience losses exceeding the VaR threshold on approximately 5% of observations.

The project therefore compares:

- Expected exception rate
- Observed exception rate
- Timing of exceptions

Two statistical tests are also applied:

### Kupiec Proportion of Failures Test

Evaluates whether the observed exception frequency is statistically consistent with the expected VaR confidence level.

### Christoffersen Independence Test

Evaluates whether VaR exceptions occur independently or tend to cluster during periods of market stress.

---

## Key Insights

The analysis highlights several important characteristics of market risk models:

- Portfolio diversification can reduce volatility compared with individual assets.
- Asset correlations can change during periods of market stress.
- Financial returns may deviate substantially from a Normal distribution.
- Parametric approaches can underestimate tail risk when distributional assumptions fail.
- VaR models calibrated during relatively calm periods can experience significantly more exceptions during regime changes.
- VaR should therefore be complemented with additional tail-risk measures and stress analysis.

The purpose of the project is not to demonstrate that VaR is useless, but to evaluate where the methodology is informative and where its assumptions become problematic.

---

## Technologies

**Python**

- pandas
- NumPy
- SciPy
- Matplotlib
- yfinance

**Financial Risk**

- Value-at-Risk
- Expected Shortfall
- Portfolio volatility
- Correlation analysis
- Maximum Drawdown
- Monte Carlo simulation
- VaR backtesting
- Kupiec test
- Christoffersen test

---

## Repository Structure

```text
portfolio-market-risk-var/
│
├── README.md
├── VaR_Portfolio_B3_Analysis2.ipynb
├── requirements.txt
├── data/
├── images/
└── LICENSE