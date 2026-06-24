# SPEC.md — Technical Specification

<!--
Defines HOW the system is built.
Claude reads this to understand architecture rules.
-->

---

## Architecture Overview

```
akshat-brain/
├── MASTER_PROMPT.md      ← AI behavior rules (read first)
├── PROJECT_BRIEF.md      ← What we are building
├── BRAIN.md              ← Live project state (overwrite each session)
├── CHECKPOINT.md         ← Exact stop point (overwrite each session)
├── SPEC.md               ← This file — technical rules
├── FACTS.md              ← Confirmed observations
├── DECISIONS.md          ← Key choices + reasoning
├── ASSETS.md             ← Reusable prompts + frameworks (importance 8+)
├── DISCOVERIES.md        ← Important findings
├── DO_NOT_REPEAT.md      ← Rejected ideas
├── RED_TEAM.md           ← Risks and mitigations
├── VALIDATION.md         ← Checklists before running anything
├── RESULTS.csv           ← Backtest results log
├── WEEKLY_SUMMARY.md     ← Weekly digest
├── code/                 ← Python scripts
├── data/                 ← Downloaded OHLCV data (gitignored)
├── prompts/              ← Copy-paste prompts for Claude sessions
└── sessions/             ← Session logs
```

---

## Module Specs

### Module 1 — Data Pipeline (`code/01_data_pipeline.py`)
- Source: yfinance
- India: Nifty 500 symbols with `.NS` suffix (e.g. `RELIANCE.NS`)
- US: Top 200 Nasdaq + ETFs: QQQ, SPY, IWM, XLK, XLF, SOXX, SMH
- Output: CSV files in `data/india/` and `data/us/`
- Columns: Date, Open, High, Low, Close, Volume (adjusted close)
- Update: incremental — only fetch missing dates
- Error handling: skip delisted, log failures to `data/failed_symbols.txt`

### Module 2 — RS Ranker (`code/02_rs_ranker.py`)
- RS_raw = (close_today / close_N_days_ago) - 1
- RS_rank = percentile rank within universe (1 = weakest, 100 = strongest)
- Compute for 252-day (52-week) AND 126-day (26-week) lookbacks
- Composite RS = 0.6 × RS_252 + 0.4 × RS_126
- Output: `output/rs_ranks_YYYYMMDD.csv`

### Module 3 — 3-Slap Scanner (`code/03_three_slap_scanner.py`)
- Only scan stocks where RS_rank > 70
- 3-Slap pattern: 3 consecutive closes touching/near a resistance level, then breakout
- Volume confirmation: breakout day volume > 1.5x 20-day average volume
- Output: `output/signals_YYYYMMDD.csv`

### Module 4 — Regime Filter (`code/04_regime_filter.py`)
- India regime: Nifty 50 (^NSEI) close vs 200-day SMA
- US regime: SPY close vs 200-day SMA
- UPTREND: close > SMA_200
- DOWNTREND: close < SMA_200 × 0.98
- SIDEWAYS: between the two
- Only generate BUY signals when regime = UPTREND
- Output: `output/regime_YYYYMMDD.txt`

### Module 5 — Backtester (`code/05_backtester.py`)
- Input: signal CSV + OHLCV data
- Entry: next open after signal date
- Exit: after hold_days OR stop_loss hit (whichever first)
- Stop loss: 8% below entry price
- Costs: 0.1% entry + 0.1% exit
- Metrics: Sharpe, CAGR, MaxDD, win_rate, avg_hold, num_trades
- OOS split: last 20% of date range
- Output: `output/backtest_EXP001_YYYYMMDD.csv` + row for RESULTS.csv

### Module 6 — Telegram Bot (`code/06_telegram_bot.py`)
- Send daily scan summary to Telegram channel
- Message format:
  ```
  📊 AKSHAT SCAN — [DATE]
  Regime: [UPTREND/SIDEWAYS/DOWNTREND]
  Signals: [N] stocks
  Top picks: [SYMBOL] RS:[rank] | [SYMBOL] RS:[rank]
  ```
- Only send if regime = UPTREND
- Send time: 9:15 AM IST (GitHub Actions cron)

### Module 7 — Google Sheets Dashboard (`code/07_sheets_reporter.py`)
- Push RESULTS.csv rows to Google Sheet
- Sheet: "Backtest Log" tab
- Push daily signal summary to "Signals" tab
- Auth: Google Service Account JSON (stored as GitHub Secret)

---

## GitHub Actions Workflow

File: `.github/workflows/daily_scan.yml`
Schedule: `30 3 * * 1-5` (9:00 AM IST = 03:30 UTC, weekdays only)
Steps: fetch data → compute RS → run scanner → check regime → send Telegram

---

## Data Storage Rules

- `data/` folder is gitignored (too large for GitHub)
- Data lives in Google Drive or local (mounted in Colab)
- On GitHub Actions: data fetched fresh each run via yfinance
