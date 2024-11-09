# Dividend Capture Strategy Analysis

## Overview
This project explores the Dividend Capture Strategy, examining the returns of buying stocks before their ex-dividend date, collecting the dividend, and selling afterward. Using a dataset of stock dividend events and market data, the project assesses if this strategy yields positive, risk-adjusted returns, especially after accounting for transaction costs and market risks.

## Data Sources
- CRSP Dividend Data: Contains information on dividend payments and relevant stock prices.
- ^IRX Data: Provides risk-free rate data using Treasury Bill yields.
- Yearly Betas: Historical beta values for adjusting returns by market risk.

## Key Steps

### Data Cleaning & Preprocessing:

- Filtered out observations with zero trade volume or dividend amounts under $0.01.
- Computed prior closing prices and calculated market capitalization.
- Adjusted negative stock prices and removed events with insufficient liquidity.

### Dividend Capture Analysis:

- Computed price change relative to dividends, stock yield, and spread.
- Assessed the relationship between price drop and dividend amount, checking if the price drop is typically less than the dividend.
- Calculated close-to-close returns after receiving dividends, comparing them to the risk-free rate.

#### Market Risk Adjustment:

- Merged beta values and calculated CAPM-adjusted abnormal returns.
- Evaluated the impact of market risk by adjusting event returns for expected market returns, isolating the impact of dividends.

#### Alternative Strategy (Prior Close to Open):

- Calculated returns by buying at the prior day’s close and selling at the next open, capturing only overnight returns.
- Examined whether this approach yielded comparable or better returns than close-to-close trading.

#### Transaction Cost Impact:

- Adjusted returns by subtracting transaction costs based on the bid-ask spread.
- Analyzed how spreads affected the profitability of the strategy, particularly for high-yield and small-cap stocks.

#### Factor Ranking Analysis:

- Ranked stocks by metrics like market capitalization, yield, beta, and spread.
- Evaluated decile-based returns, spread, and after-cost returns to identify the characteristics of stocks that may improve dividend capture profitability.

## Results and Findings

### Dividend Capture Return (Close-to-Close):

- Achieved an annualized return of 60.9% with an annualized standard deviation of 35.8%.
- T-stat of 60.6 and event-based Sharpe Ratio of 1.61, suggesting promising profitability before adjusting for costs.

### CAPM-Adjusted Returns:

- Abnormal returns remained significant with an annualized return of 48% and a Sharpe Ratio of 1.37, even after removing market drift.
- Average beta close to 1 indicated market exposure, but still showed a robust strategy.

### Prior Close to Open Return:

- Generated an annualized return of 39.5% with lower volatility.
- T-stat of 44.7 and Sharpe Ratio of 1.67, providing a viable alternative to the full-day capture approach.

### Transaction Costs:

- After adjusting for the bid-ask spread, returns decreased significantly, with some deciles showing negative returns.
- Small-cap stocks, although showing higher pre-cost returns, exhibited high spreads, resulting in negative after-cost returns, aligning with Kalay's theory on transaction costs.

### Factor Analysis (Decile Rankings):

- Stocks with higher yields and smaller market caps showed higher raw returns but faced significant transaction cost barriers.
- Sorting by spread revealed that the most liquid stocks in the lowest spread decile had an annualized return of 32% with a Sharpe Ratio of 1.09 after costs, suggesting profitability in the most liquid segment.

## Insights and Best Practices

- Liquidity Matters: High transaction costs significantly impact profitability; focusing on liquid stocks with low spreads is crucial.
- Risk Adjustment: CAPM adjustments help isolate dividend effects from market trends, providing a clearer picture of strategy profitability.
- Factor Analysis: Yield, market cap, and spread rankings help in identifying stock characteristics favorable for dividend capture.
- Alternative Timeframes: Prior-close to open trading may reduce transaction costs while retaining significant returns.

## Files Included
- CRSP_Dividends.csv: Stock dividends and event data.
- ^IRX.csv: Risk-free rate data from Treasury Bill yields.
- Yearly Betas.csv: Stock beta values for market risk adjustment.

## Future Improvements
- Incorporate alternative risk models to refine abnormal return estimates.
- Explore out-of-sample tests using newer data to validate findings.
- Consider strategies that dynamically adjust to liquidity changes and evolving market conditions.

This analysis offers valuable insights into the potential and limitations of dividend capture strategies, highlighting the importance of adjusting for transaction costs, market risk, and liquidity when seeking to capture predictable returns from dividend events.
