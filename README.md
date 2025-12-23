Pairs Trading Algorithim
This project implements a statistical arbitrage strategy using Boeing (BA) and Airbus (AIR.PA). 

Overview
Portfolio Optimization: Using historical price data, we calculate expected returns and covariance to construct a minimum volatility portfolio with constrained weights.

Principal Component Analysis (PCA): We reduce the dimensionality of stock return data to identify dominant patterns (factors) explaining the majority of variance.

Factor Interpretation: We compute PCA factor returns and correlate them with sector ETFs to interpret each factor’s economic meaning.



Libraries:

yfinance
pandas
numpy
matplotlib
statsmodels.api

Main Logic: 

Step 1: Data Collection
Daily closing prices downloaded from 2010-present

Step 2: Rolling Hedge Ratio
Uses 252-day rolling OLS regression
Boeing regressed on Airbus

Step 3: 

Interpretation and Limitations
Based on the heatmap correlations:

PC1: Likely a broad market factor (general market movements).
PC2: Likely represents the tech sector.
PC3: Likely corresponds to the energy sector.
Note on nonlinearities:
This PCA and correlation analysis assumes linear relationships between returns and factors. Nonlinear dependencies are not captured, and thus the heatmap interpretation might miss complex interactions. Handling nonlinearities requires more advanced methods and is beyond this project’s scope.

How to Run
Clone this repository.
Install required packages.
Change your portfolio/metric you're optimizing from the full code
Run the script.
Analyze visual outputs and interpretation text.
References
PyPortfolioOpt documentation
scikit-learn PCA
Yahoo Finance (yfinance)
Seaborn heatmap
