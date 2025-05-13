
# S&P 500 Portfolio Optimization using Clustering and Efficient Frontier

This project implements a momentum-based equity portfolio strategy for the S&P 500 universe by combining technical indicators, factor models, unsupervised clustering, and Sharpe ratio-based portfolio optimization. The strategy builds a buy-only portfolio, rebalanced monthly, based on feature-driven asset grouping and controlled allocation mechanics.

## Project Overview
- A momentum-based long-only strategy that selects stocks from the S&P 500 and rebalances monthly.
- Assets are grouped into clusters based on financial and technical features using unsupervised learning.
- A selected cluster—based on predefined momentum or feature logic—is used to form the buy universe.
- Portfolio construction is based on maximizing the Sharpe ratio using efficient frontier optimization.
- Investors can customize which cluster to invest in and control min/max allocation per stock.

## Feature Engineering
- Technical indicators include RSI, ATR, MACD, Bollinger Bands, and dollar volume (for liquidity filtering).
- Only the top 150 most liquid stocks are retained monthly based on dollar volume.
- Monthly returns are calculated using a 12-month lookback to capture price momentum.
- Fama-French 5-factor model is used to estimate rolling betas for MKT, SMB, HML, RMW, and CMA.
- These combined features form the input to clustering, helping define stock characteristics each month.

## Clustering Methodology
- K-means clustering with K = 4 is applied monthly to group similar stocks by feature profile.
- Predefined centroids are used to enforce consistent cluster structure across time periods.
- Cluster assignment is rule-based—e.g., stocks with RSI > 70 are consistently mapped to Cluster 3.
- Users can choose which cluster(s) to invest in for any given month, based on their preferences.
- This approach blends unsupervised learning with domain-informed feature thresholds for reliability.

## Portfolio Optimization
- Stocks selected from the target cluster are passed to a Sharpe-maximizing portfolio optimizer.
- Portfolio optimization uses the Efficient Frontier, subject to long-only and full-investment constraints.
- Users can define maximum and minimum capital allocation per stock to control diversification.
- Optimization is performed monthly, reflecting updated features, returns, and clusters.
- The result is a dynamic momentum-based portfolio that adapts to changing market signals.

## Performance Evaluation
- Monthly portfolio returns are computed and aggregated to track cumulative growth.
- Strategy performance is benchmarked against the S&P 500 Index over the same time period.
- Visualization includes portfolio vs benchmark returns, drawdowns, and rolling Sharpe ratios.
- Key performance metrics (e.g., volatility, CAGR, Sharpe) are reported to assess robustness.
- Evaluation highlights the impact of cluster-based selection and weight optimization.

## Limitation
- Uses the current list of S&P 500 stocks, leading to potential survivorship bias in backtesting.
- Stocks that were delisted or not part of the index historically are still included retroactively.
- Bias may inflate returns compared to realistic, point-in-time index constituents.
- Accurate evaluation would require historical membership data, which is not included here.
- Survivorship-free data is necessary for institution-grade backtesting and real-world deployment.
