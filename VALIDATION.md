# VALIDATION.md — Checklists Before Running Anything

---

## Before Every Backtest

- [ ] Data has no gaps in target date range
- [ ] Universe is defined and saved to a file
- [ ] Transaction costs = 0.1% per leg (0.2% round trip)
- [ ] In-sample period is clearly separated from out-of-sample (last 20%)
- [ ] Regime filter applied — no trades in DOWNTREND
- [ ] Stop loss = 8% below entry is coded
- [ ] All 8 required metrics will be output (see ASSET-005)
- [ ] Results row will be written to RESULTS.csv

## Before Every Scanner Run

- [ ] Data is fresh (fetched today or within 24 hours)
- [ ] Regime is UPTREND before generating signals
- [ ] RS rank > 70 threshold is applied
- [ ] Pattern confirmation (volume > 1.5x avg) is applied
- [ ] Output CSV is saved to `output/signals_YYYYMMDD.csv`

## Before Every Code Commit

- [ ] Script runs without errors in Google Colab
- [ ] Script includes transaction costs
- [ ] Script header: `# Generated: [date] [Claude] Step [N]`
- [ ] Saved as `code/latest.py` AND `code/YYYY-MM-DD-[description].py`

## Before Every New Claude Session

- [ ] BRAIN.md is up to date (from last session)
- [ ] CHECKPOINT.md has correct next step
- [ ] All changes from last session are committed to GitHub
- [ ] Use startup prompt from `prompts/startup.md`
