# output/ — Daily Scan Outputs

This folder stores daily scan results.

## Files Created by Each Module

```
output/
├── rs_ranks_YYYYMMDD.csv        ← Module 2 output
├── signals_YYYYMMDD.csv         ← Module 3 output
├── regime_YYYYMMDD.txt          ← Module 4 output
└── backtest_EXPXXX_YYYYMMDD.csv ← Module 5 output
```

## signals_YYYYMMDD.csv Format

Symbol, RS_rank, RS_composite, Pattern, Volume_ratio, Entry_price, Date

## Retention

Keep last 30 days of output files. Archive older files to Google Drive.
