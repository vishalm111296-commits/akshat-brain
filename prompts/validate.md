# validate.md — Use This Before Running Any Backtest

Paste this into Claude:

---

```
Read VALIDATION.md:
https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/VALIDATION.md

I am about to run backtest EXP-[NUMBER].
Parameters:
- Universe: [NSE Nifty 500 / Nasdaq top 200]
- Date range: [YYYY-MM-DD to YYYY-MM-DD]
- Hold days: [N]
- RS threshold: [N]
- Stop loss: [N%]

Check every item in the pre-backtest checklist.
Output: PASS or FAIL for each item.
If any FAIL: tell me exactly what to fix before running.
```
