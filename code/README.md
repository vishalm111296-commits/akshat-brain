# code/ — Python Scripts

## Structure

```
code/
├── latest.py                        ← Always the most recent working script
├── 01_data_pipeline.py              ← Module 1: Download OHLCV data
├── 02_rs_ranker.py                  ← Module 2: Compute RS scores + ranks
├── 03_three_slap_scanner.py         ← Module 3: Detect 3-slap patterns
├── 04_regime_filter.py              ← Module 4: Market regime detection
├── 05_backtester.py                 ← Module 5: Backtest engine
├── 06_telegram_bot.py               ← Module 6: Send Telegram signals
├── 07_sheets_reporter.py            ← Module 7: Push to Google Sheets
└── YYYY-MM-DD-description.py        ← Versioned snapshots
```

## Rules

- `latest.py` = always overwrite with newest working script
- Every script starts with: `# Generated: YYYY-MM-DD [Claude] Step [N]`
- Save both `latest.py` AND a dated snapshot every session
- Never commit code that has not been tested in Google Colab

## Module Build Order

Build in this order — each module depends on the previous:
1. Data Pipeline (foundation)
2. RS Ranker (needs data)
3. Regime Filter (needs data)
4. 3-Slap Scanner (needs RS ranks)
5. Backtester (needs signals + data)
6. Telegram Bot (needs signals)
7. Google Sheets (needs backtest results)
