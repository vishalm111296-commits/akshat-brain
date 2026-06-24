# DECISIONS.md — Key Decisions

<!--
Log every major architectural or strategic decision here.
Future AI sessions read this to understand why things are built the way they are.
-->

---

## DEC-001 — Use Claude Free (No API)
Date: 2026-06-24
Decision: Use Claude free tier at claude.ai — no Anthropic API key
Reason: Zero cost. brain-os structure means Claude resumes any session by reading 4 files.
Trade-off: Limited context window per session — work in small steps.
Status: ACTIVE

## DEC-002 — Repository Is the Only Memory
Date: 2026-06-24
Decision: GitHub repo files are the only memory. No reliance on conversation history.
Reason: Free Claude has no persistent memory. Repo = permanent brain.
Trade-off: Must commit after every step or work is lost.
Status: ACTIVE

## DEC-003 — Python for All Code
Date: 2026-06-24
Decision: Python 3.10+ for all scripts
Reason: yfinance, pandas, NSE libraries all Python-native. Google Colab is Python.
Trade-off: Slower than compiled but fast enough for daily scans on 500 stocks.
Status: ACTIVE

## DEC-004 — Telegram for Signal Delivery
Date: 2026-06-24
Decision: Telegram bot for daily signals
Reason: Free. Mobile-first. Works on Android without any app installation.
Trade-off: Requires one-time bot token setup.
Status: ACTIVE

## DEC-005 — Composite RS Score
Date: 2026-06-24
Decision: Composite RS = 0.6 × RS_252 + 0.4 × RS_126
Reason: Weights long-term trend more but still captures medium-term acceleration.
Trade-off: Adds complexity vs pure 52-week RS — needs backtest validation.
Status: HYPOTHESIS — to be tested in EXP-001

## DEC-006 — 8% Hard Stop Loss
Date: 2026-06-24
Decision: Exit any position that falls 8% below entry
Reason: Standard CANSLIM / growth stock rule. Limits catastrophic losses.
Trade-off: May trigger on volatile stocks with legitimate pullbacks.
Status: ACTIVE
