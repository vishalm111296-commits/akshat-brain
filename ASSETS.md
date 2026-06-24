# ASSETS.md — Reusable Assets (Importance 8–10 Only)

<!--
Only items scored importance 8, 9, or 10 are stored here.
Claude checks this file for reusable components before writing new code.
-->

---

## ASSET-001 — Claude Free Session Starter Prompt

```
Type: Prompt
Importance: 10
Applies To: Every Claude session in this project
Reusable: Yes

Content:
Read these 4 files in order:
1. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/MASTER_PROMPT.md
2. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/PROJECT_BRIEF.md
3. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/BRAIN.md
4. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/CHECKPOINT.md

After reading all 4, output the UNDERSTANDING CHECK.
Do not do any work until I say confirmed.
Today's goal: [CHANGE THIS LINE — describe what you want to do today]
```

---

## ASSET-002 — Relative Strength Formula (Mansfield / IBD-style)

```
Type: Framework
Importance: 9
Applies To: RS Ranker Module
Reusable: Yes

Content:
# Step 1: Raw RS
RS_252 = (close_today / close_252_days_ago) - 1
RS_126 = (close_today / close_126_days_ago) - 1

# Step 2: Rank within universe (percentile 1–100)
RS_rank_252 = percentileofscore(universe_RS_252, stock_RS_252)
RS_rank_126 = percentileofscore(universe_RS_126, stock_RS_126)

# Step 3: Composite
RS_composite = 0.6 * RS_rank_252 + 0.4 * RS_rank_126

# Step 4: Mansfield RS (relative to market)
Mansfield_RS = RS_composite - 50  # Positive = outperforming market average
```

---

## ASSET-003 — Regime Filter Logic

```
Type: Framework
Importance: 9
Applies To: Regime Filter Module
Reusable: Yes

Content:
def get_regime(index_close_series):
    sma_200 = index_close_series.rolling(200).mean()
    latest_close = index_close_series.iloc[-1]
    latest_sma = sma_200.iloc[-1]
    if latest_close > latest_sma:
        return "UPTREND"
    elif latest_close < latest_sma * 0.98:
        return "DOWNTREND"
    else:
        return "SIDEWAYS"

# India: pass Nifty 50 (^NSEI) close series
# US: pass SPY close series
# Only generate BUY signals when regime == "UPTREND"
```

---

## ASSET-004 — Transaction Cost Rule

```
Type: Checklist
Importance: 9
Applies To: All backtests
Reusable: Yes

Content:
- Entry cost: 0.1% of trade value
- Exit cost: 0.1% of trade value
- Total round-trip cost: 0.2%
- Slippage: already embedded in 0.1% assumption
- NEVER run a backtest without this applied
- Results without costs are fiction
```

---

## ASSET-005 — Backtest Metrics Required

```
Type: Checklist
Importance: 8
Applies To: All backtests
Reusable: Yes

Content:
Every backtest MUST report ALL of these:
1. Sharpe Ratio (annualized)
2. CAGR (%)
3. Max Drawdown (%)
4. Win Rate (%)
5. Avg Hold Period (days)
6. Number of Trades
7. OOS Sharpe (last 20% of date range)
8. OOS CAGR

If any metric is missing — the backtest is incomplete. Run again.
```
