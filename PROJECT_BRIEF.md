# PROJECT_BRIEF.md — What We Are Building

---

## One-Line Description

A fully automated stock market system that scans NSE (India) and Nasdaq (US) stocks daily, ranks them by relative strength, detects 3-slap entry patterns, filters by market regime, backtests strategies, and sends signals to Telegram — all using free tools and free AI.

---

## The 7 Modules

| # | Module | Status | Output |
|---|---|---|---|
| 1 | Data Pipeline | TODO | Daily OHLCV CSV for full universe |
| 2 | Relative Strength Ranker | TODO | RS score + rank for every stock |
| 3 | 3-Slap Pattern Scanner | TODO | List of stocks with entry pattern |
| 4 | Regime Filter | TODO | UPTREND / SIDEWAYS / DOWNTREND |
| 5 | Backtester | TODO | Sharpe, CAGR, MaxDD, trades log |
| 6 | Telegram Signal Bot | TODO | Daily signal message on phone |
| 7 | Google Sheets Dashboard | TODO | Results + performance tracking |

---

## Universe

- **India:** NSE Nifty 500 stocks (expandable to Nifty 5000)
- **US:** Top 200 Nasdaq stocks + major ETFs (QQQ, SPY, IWM, XLK, XLF)

---

## Key Parameters (Starting Defaults)

| Parameter | Default Value | Reason |
|---|---|---|
| RS lookback | 252 trading days (52-week) | Standard Mansfield RS |
| RS secondary | 126 trading days (26-week) | Medium-term momentum |
| RS buy threshold | RS rank > 70 | Only scan top 30% performers |
| Hold period | 20 trading days (~1 month) | Default — test variable holds |
| Stop loss | 8% below entry | Standard growth stock rule |
| Transaction cost | 0.1% per leg | Realistic for Indian retail |
| Regime index (India) | Nifty 50 (^NSEI) | Market breadth proxy |
| Regime index (US) | SPY | Market breadth proxy |
| Regime SMA | 200-day SMA | Standard trend filter |

---

## Hard Constraints

- **Zero cost:** Everything must be free (yfinance, NSE tools, GitHub Actions, Telegram)
- **Mobile-first:** Owner uses Android phone primarily
- **No paid API:** Claude free tier only — no Anthropic API key
- **Commit everything:** No step is real until it is committed to GitHub

---

## Success Criteria

- Backtest Sharpe ratio > 1.0 on out-of-sample period
- CAGR > 20% on NSE universe
- Max drawdown < 25%
- Daily scan runs automatically via GitHub Actions
- Telegram message arrives every trading day by 9:30 AM IST
