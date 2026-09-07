# market-risk-var-model

## Overview
This project presents a Python risk framework for a multi-asset portfolio, implementing Value at Risk (VaR), Expected Shortfall, VaR calibration, historical stress testing, scenario stress testing, and portfolio risk decomposition. The analysis makes use of multiple VaR methodologies (historical, parametric, and Monte Carlo), and compares the portfolio's individually weighted assets with their accompanying portfolio risk contributions.

## Portfolio
The portfolio is purely hypothetical with a value of $1M and consists of the following individual assets:
|Asset|Weight|
|:----|----:|
|SPY|40%|
|QQQ|25%|
|TLT|15%|
|GLD|10%|
|IWM|10%|

Historical asset data used in analysis were obtained using yfinance.

## Methodology

# Value at Risk (VaR)
Three VaR methodologies were implemented at 90%, 95%, and 99% confidence levels:
1. Historical VaR - Estimates tail losses using historical portfolio return data.
2. Parametric (variance-covariance) VaR - Estimates tail losses by assuming returns are normally distributed.
3. Monte Carlo VaR - Estimates tail losses by simulating returns under a normal return distribution assumption.

# Expected Shortfall
Historical Expected Shortfall is calculated by taking the average of returns that breach the VaR threshold, providing vital information about the severity of tail losses beyond the VaR threshold.

# VaR Calibration
The historical VaR model is calibrated using the following methods:
1. Comparison of observed and expected breach rates
2. Kupiec Proportion of Failures test
3. Breach independence testing
4. Conditional-Coverage testing

Historical VaR was calculating using the same historical sample that was used for this evaluation. This is not a forecast test outside the sample, but rather a calibration check.

## Historical Stress Testing

## Scenario Stress Testing

## Risk Decomposition

## Results

## Tools and Libraries

## How to Run
