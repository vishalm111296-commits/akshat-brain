# data/ — Downloaded OHLCV Data

This folder is gitignored. Data lives here locally or in Google Drive.

## Structure (created by Module 1)

```
data/
├── india/
│   ├── RELIANCE.NS.csv
│   ├── TCS.NS.csv
│   └── ... (all Nifty 500 symbols)
├── us/
│   ├── AAPL.csv
│   ├── QQQ.csv
│   └── ... (top 200 Nasdaq + ETFs)
├── index/
│   ├── NSEI.csv          ← Nifty 50 for regime filter
│   └── SPY.csv           ← SPY for US regime filter
└── failed_symbols.txt    ← Symbols that failed to download
```

## Column Format

Date, Open, High, Low, Close, Adj_Close, Volume

## Update Rule

Incremental — only fetch dates not already in file.
Never re-download full history unless corruption detected.
