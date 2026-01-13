Pairs Trading Algorithim
This project performs a statistical arbitrage strategy between General Dynamics (GD) and Lockheed Martin (LMT). It uses a rolling hedge ratio calculated with a rolling OLS regression and executes trades based on Z-score mean reversion.

Overview
1. Dynamic hedging - Uses a rolling OLS(Ordinary Least Squares Regression) to calculate the hedge ratio.
2. Stationarity Testing - Uses the ADF(Augmented Dickey-Fuller) test to determine if the following assets having mean-reverting properties.
3. Signal Generation - Developed signals that execute a buy or sell if the z-score of the spread goes above or below a certain point.
   Short spread: Enter when Z > 2.75 (GD is overvalued relative to LMT)
   Long spread: Enter when Z < -2.75 (GD is undervalued to LMT)
   Exit: Close positions when the Z-score returns to a neutral zone (between -0.05 and 0.05)

Key Features
1. Rolling Beta Calculation:
This script recalculates the hedge ratio over a 252-day rolling window which accounts for shifts in the market.

3. Risk Metrics Calculates:
Cumulative Returns: Growth of capital over the testing period
Sharpe Ratio: Risk-adjusted return
Z-score visualization: Tracking of entry and exit points

Libraries:
yfinance
pandas
numpy
matplotlib
statsmodels.api

Getting Started
1. Clone the repository
2. Run the script to fetch live data from yfinance
3. View Z-score plot to see trading opportunities
4. Analyze cumulative returns plot to evalulate strategy viability
