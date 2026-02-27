Pairs Trading Algorithim

This project performs a statistical arbitrage strategy between General Dynamics (GD) and Lockheed Martin (LMT). It identifies divergences in the historical relationship between these two defense stocks. When the price spread deviates greatly from its moving average, the algorithim enters a position, betting on mean reversion. 

Logic
1. GD/LMT are highly correlated stocks so we can bet on mean reversion.
2. The spread is calculated using a rolling OLS regression to determine a hedge ratio.
3. The signals enter at $\pm 2.75$ standard deviations from the mean and exit at $\pm 0.05$ standard deviations from the mean. 

Key Features
1. Rolling Hedge Ratio
This algorithim uses a 252-day rolling window to calculate the hedge ratio. This accounts for any strucutral shifts in the correlation between the stocks and ensures the spread remains stationary.

Spread = Price of GD - Beta * Price of LMT

2. ADF(Augmented Dickey-Fuller) Test

The ADF test is used to verify stationarity, to check whether two stocks possess mean reverting properties. To check this, we can create a null and alternative hypothesis.

Ho: The two stocks are non-stationary and follow a random walk pattern (not mean reverting).

Ha: The two stocks are stationary and do not follow a random walk pattern (mean reverting).

We run the ADF on the residuals(spreads) of the two stocks and not prices(prices are non-stationary and follow a random walk pattern). By running the test in python using statsmodels.tsa.stattools, the test yielded the following:
    
ADF Statistic: -3.45

p-value: 0.008

Interpretation:

ADF Statistic - Significantly negative so we can strongly reject the null hypothesis. The typical critical value for for a 99% confidence interval is -3.43 and the ADF Statistic clears that. 
p-value: <0.05 - This gives us 99% confidence that the pair is stationary and mean reverting, making the two a viable pair. 

3. Z-score Spread Visualization: 


<img width="383" height="206" alt="image" src="https://github.com/user-attachments/assets/f553c128-c76b-4e44-948d-d757d27aa409" />

The following trading opportunities can be visualized with a graph of the z-score spread. When the line goes above $\pm 2.75$ we short the spread by selling GD and buying LMT. Similarly, when the line goes below -$\pm 2.75$ we long the spread by buying GD and selling LMT. When the spread reverts to +/- $\pm 0.05$ the position is exited. 


4. Performance Metrics
This strategy was taken from June 2021 to January 2026.
Sharpe Ratio: 2.11
Risk-Free Rate: 4.18%

Future Improvements:

Log Prices - Change the spread moving from raw prices to log prices to improve risk management
Stop Loss - If the spread goes above $\pm 4$, it might signal a structural break that the stocks aren't cointegrated. This calls for an exit in the position.


Libraries:
yfinance
pandas
numpy
matplotlib
statsmodels.tsa.stattools

Getting Started
1. Clone the repository
2. Run the script to fetch live data from yfinance
3. View Z-score plot to see trading opportunities
4. Analyze cumulative returns plot to evalulate strategy viability
