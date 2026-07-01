# MVRV Dashboard

Single-file Bitcoin MVRV analytics dashboard. Opens on mobile, loads its own data, no install.

## What it does

Pulls 840k+ data points (sub-minute MVRV since 2010) from a GitHub-hosted JSON and builds 12 analysis tabs:

| Tab | What you get |
|---|---|
| Overview | Current MVRV, Z-score, all-time peak/bottom, halving timeline with cycle progress |
| Z-Score | Rolling 365-day Z-score with Accumulate / Caution / Sell signals |
| Momentum | Rate-of-change — how fast MVRV is moving |
| Cycle Overlay | All cycles aligned to their halving date, overlaid |
| Drawdown | Peak-to-trough per cycle |
| MA Crossovers | MVRV vs MA20 / MA50 / MA200 crossover history |
| Zone Days | Days spent above/below key MVRV thresholds per cycle |
| Cycle Extremes | Volatility compression — peak-to-trough range shrinks each cycle |
| Price Peaks | Confirmed ATH dates and MVRV at each peak |
| Price Bottoms | Bear market floors: price, MVRV, duration |
| Projections | 4 ceiling models + 4 floor models with IQR consensus |
| Backtest | Each model re-run with only data available at cycle start — no hindsight |

## Usage

```
open index.html in a browser
```

Data loads automatically. If it fails (CORS, offline), use the manual upload button — export `mvrv.json` from [blockchain.com/explorer/charts/mvrv](https://www.blockchain.com/explorer/charts/mvrv).

## Projection models

**Ceiling** — MVRV Upside · Halving Multiplier · ATH Multiplier · MVRV × Realized Cap  
**Floor** — MVRV Downside · Halving Floor Ratio · Bottom Multiplier · MVRV Trough × RC

All decay as power laws across cycles. Consensus = IQR midpoint after excluding outliers.

## Backtest note

Completed cycles (C2, C3) are re-projected using only data that existed at the start of that cycle. C4 is ongoing. Error = `(predicted − actual) / actual × 100`.

## Stack

Vanilla JS · Chart.js 4.4 · chartjs-plugin-annotation · JetBrains Mono · no framework · no build step · 168 KB

## Data sources

- MVRV: `raw.githubusercontent.com/0xtrvkc/dynamic-btc-analytics-dashboard/main/mvrv.json`
- BTC price: `raw.githubusercontent.com/0xtrvkc/dynamic-btc-analytics-dashboard/main/btc_daily_price.json`

Price data is optional — all MVRV analysis works without it.
