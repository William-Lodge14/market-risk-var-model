# Portfolio Risk Model

# Overview
This project presents a Python risk framework for a multi-asset portfolio, implementing Value at Risk (VaR), Expected Shortfall, VaR calibration, historical stress testing, scenario stress testing, and portfolio risk decomposition. The analysis makes use of multiple VaR methodologies (historical, parametric, and Monte Carlo), and compares the portfolio's individually weighted assets with their respective portfolio risk contributions.

# Portfolio
The portfolio is purely hypothetical with a value of $1M and consists of the following individual assets:
|Asset|Weight|
|:----|----:|
|SPY|40%|
|QQQ|25%|
|TLT|15%|
|GLD|10%|
|IWM|10%|

Historical asset data used in analysis were obtained using yfinance.

# Methodology

## Value at Risk (VaR)
Three VaR methodologies were implemented at 90%, 95%, and 99% confidence levels:
1. Historical VaR - Estimates tail losses using historical portfolio return data.
2. Parametric (variance-covariance) VaR - Estimates tail losses by assuming returns are normally distributed.
3. Monte Carlo VaR - Estimates tail losses by simulating returns under a normal return distribution assumption.

## Expected Shortfall
Historical Expected Shortfall is calculated by taking the average of returns that breach the VaR threshold, providing information about the severity of tail losses beyond the VaR threshold.

## VaR Calibration
The historical VaR model is calibrated using the following methods:
1. Comparison of observed and expected breach rates
2. Kupiec Proportion of Failures test
3. Breach independence testing
4. Conditional-Coverage testing

Historical VaR was calculated using the same historical sample that was used for this calibration check. This is not a forecast test outside the sample, but rather an in-sample calibration check.

## Historical Stress Testing
The portfolio is evaluated during historical periods of extreme/adverse market conditions to observe the subsequent effects on the portfolio. These historical periods include both worst individual return days and stress periods spanning months.

## Scenario Stress Testing
Four hypothetical stress scenarios were devised and used to test the portfolio's vulnerability to adverse market conditions:
1. Equity Selloff
2. Equity + Bond Selloff
3. Cross-Asset Selloff + Gold
4. Concentration Stress

## Risk Decomposition
Portfolio risk was decomposed using:
1. Euler Risk Decomposition
2. Marginal Contribution to Risk (MCR)
3. Risk-Capital Ratio
4. Herfindahl-Hirschman Index (HHI)
5. Effective Risk Positions

These risk decomposition measures serve to examine the portfolio's individual assets to see which drive portfolio volatility, and to observe whether risk is concentrated relative to the weights of the individual assets.
# Results
- Equities make up 75% of portfolio capital, but are responsible for 93% of total portfolio volatility (risk)
- QQQ has the highest marginal contribution to risk and risk-capital ratio out of all the individual assets
- The portfolio has an effective number of risk positions of 2.90, indicating that effective diversification was lower than the five asset holdings would suggest.
- At a 95% confidence level, the Historical VaR is $14,887, and the historical Expected Shortfall is $21,442
- At the 99% confidence level, Historical VaR exceeds Parametric VaR, indicating that a normality assumption of the portfolio return distribution may underestimate tail losses.
- Hypothetical stress scenarios produce losses ranging from $92,500 to $167,500

# Tools and Libraries
- Python
- NumPy
- Pandas
- Matplotlib
- SciPy
- yfinance
# How to Run
1. Clone this repository
2. Install any required dependencies using: pip install -r requirements.txt
3. Open market_risk_var_model.ipynb on Jupyter Notebook
4. Run all cells of the notebook (beginning to end)

Note: The notebook uses the yfinance library to obtain historical market data, so no additional dataset is required 
