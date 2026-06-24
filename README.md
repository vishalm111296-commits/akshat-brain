# Akshat Brain — AI-Powered Stock Scanner

> Akshat AI System rebuilt on the **ai-brain-os** operating structure
> so that **free Claude AI** can build and maintain it forever.

---

## What This System Does

| Module | Function | Status |
|---|---|---|
| 1. Data Pipeline | Downloads NSE + Nasdaq OHLCV daily | 🔲 TODO |
| 2. RS Ranker | Ranks stocks by Relative Strength | 🔲 TODO |
| 3. 3-Slap Scanner | Detects entry pattern on top RS stocks | 🔲 TODO |
| 4. Regime Filter | UPTREND / SIDEWAYS / DOWNTREND detection | 🔲 TODO |
| 5. Backtester | Tests strategies with real costs | 🔲 TODO |
| 6. Telegram Bot | Sends daily signals to your phone | 🔲 TODO |
| 7. Sheets Dashboard | Tracks results in Google Sheets | 🔲 TODO |

---

## How to Use With Free Claude AI

### Step 1 — Start a New Session
Copy the contents of [`prompts/startup.md`](prompts/startup.md) and paste into [claude.ai](https://claude.ai)

### Step 2 — Confirm Understanding
Claude reads 4 files and outputs an UNDERSTANDING CHECK. Type `confirmed`.

### Step 3 — Work Step by Step
Claude does ONE step. Outputs 4 blocks (Step Complete, Patch, Asset, Checkpoint).

### Step 4 — Commit Every Step
Apply the PATCH to the file. Commit to GitHub. Type `committed`. Claude moves to next step.

### Step 5 — Resume Any Time
New session? Copy [`prompts/resume.md`](prompts/resume.md) into a fresh Claude chat. Continue instantly.

---

## Repository Structure

```
akshat-brain/
├── MASTER_PROMPT.md    ← AI rules (Claude reads this first)
├── PROJECT_BRIEF.md    ← What we are building + success criteria
├── BRAIN.md            ← Live state (overwrite each session)
├── CHECKPOINT.md       ← Exact stop point + resume prompt
├── SPEC.md             ← Technical architecture
├── ASSETS.md           ← Reusable formulas + frameworks
├── RESULTS.csv         ← Backtest log
├── prompts/            ← Copy-paste prompts for Claude
├── code/               ← Python scripts
├── data/               ← OHLCV data (gitignored)
└── output/             ← Daily scan outputs (gitignored)
```

---

## Source Repos

- Brain OS structure: [ai-brain-os](https://github.com/vishalm111296-commits/ai-brain-os)
- Original system: [Akshat-AI-System](https://github.com/vishalm111296-commits/Akshat-AI-System)

---

## Current Status

Phase: **Building — Module 1 next**
Last updated: 2026-06-24
