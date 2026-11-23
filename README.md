# Markowitz Efficient Portfolio — Python Notebooks

Modular Python notebooks for **U.S. equity screening, Markowitz efficient frontier construction, capital allocation (`CAL(P)`), tail-risk stress testing, and out-of-sample validation** (`2021–2023` estimation; `2024–2025` out-of-sample), plus an Indonesian IDX market comparison.

Every notebook uses **top-level editable parameters in Cell 1** (`rf`, `MAX_VOL`, `MIN_MEAN`, `MAX_MEAN`, `MIN_ACTIVE_WT`, `A`, `MONTHLY_USD`, `DRAWDOWN_LIMIT`) so changing any input at the top dynamically rebuilds all accepted tickers, weights, tables, and charts below.

## Python Requirements

* Python `3.9` or newer
* Internet connection (for live Yahoo Finance `2021–2025` daily adjusted close price requests)
* Required packages:
  * `numpy`
  * `pandas`
  * `scipy`
  * `matplotlib`
  * `ipython`
  * `jupyter` or `notebook`

### Setup & Run

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install numpy pandas scipy matplotlib ipython jupyter
jupyter notebook
```

Open any notebook below and click **Run All**.

## Notebooks

| Module | Notebook | Scope |
|---|---|---|
| Universe screening | `universe_screening/us_universe_screening.ipynb` | Loads `stock_universe.csv` (59 U.S. equities), compares unscreened baseline (`rf_base = 3.00%`), applies top-level screening thresholds (`59 → 49 → 34 → 18 → 8`), cross-sector correlation pairs, and subset ablation checks |
| Markowitz frontier | `markowitz_optimizer/markowitz_frontier_allocation.ipynb` | Estimation vs. out-of-sample correlation heatmaps, covariance matrix & equal-weight identity, efficient frontier, `G`, `P`, complete portfolio `C` (`4.34%` 3M T-Bills), `CAL(P)`, utility tangency, and Separation Property |
| Risk & backtest | `risk_and_backtest/tail_risk_and_oos_backtest.ipynb` | Diversification floor (`sqrt(avg_cov)`), 99% VaR & Expected Shortfall (parametric, historical, 10,000-draw bootstrap), risk pooling, 1–25 year horizon scaling, `2024–2025` OOS backtest, and `$100/month` contribution tracker |
| IDX market test | `idx_market_test/idx_portfolio_test.ipynb` | 8 Indonesian IDX stocks (`rf = 6.25%`), bank concentration, and `-39.38%` out-of-sample max drawdown comparison |
