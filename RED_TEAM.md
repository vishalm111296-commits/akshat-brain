# RED_TEAM.md — What Could Go Wrong

<!--
Every assumption that could be wrong.
Read this at the start of every new build phase.
Update every Sunday using prompts/red-team.md
-->

---

## Data Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| yfinance returns stale/incorrect data for NSE | Medium | High | Validate: cross-check 5 random symbols against NSE website |
| NSE symbols change / delistings break pipeline | High | Medium | Log failed symbols to `data/failed_symbols.txt`, skip gracefully |
| Survivorship bias in Nifty 500 historical data | High | High | Use point-in-time universe — note this in every backtest |
| Weekend/holiday gaps causing false RS signals | Medium | Low | Forward-fill max 3 days, then mark as missing |

---

## Model Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| RS momentum stops working in bear market | High | High | Regime filter blocks signals in DOWNTREND |
| 3-slap pattern too rare — not enough signals | Medium | High | Check signal frequency in EXP-001 — need >5 signals/month |
| Overfitting parameters to historical data | High | High | Always test on last 20% of data (OOS split) |
| Composite RS weights (0.6/0.4) not optimal | Medium | Medium | Test 0.5/0.5 and 0.7/0.3 as alternatives in later experiments |

---

## Infrastructure Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| GitHub Actions free tier exceeded | Low | High | Monitor monthly usage — 2000 min/month limit |
| Telegram bot rate limited | Low | Low | Add 1s delay between messages |
| Google Sheets API quota exceeded | Low | Low | Batch pushes, not individual row writes |

---

## AI Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Claude hallucinates code | Medium | High | Run every script in Colab before committing |
| Claude reads stale file (not latest commit) | Low | Medium | Always commit before giving Claude a raw URL |
| Context window exceeded mid-task | High | Low | Step-by-step workflow — one step = one Claude response |
