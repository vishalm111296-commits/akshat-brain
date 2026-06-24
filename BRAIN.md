# BRAIN.md — Current Reality

<!--
INSTRUCTIONS FOR AI:
- OVERWRITE this entire file at end of every session
- Keep total content under 300 words
- Read this FIRST after MASTER_PROMPT.md and PROJECT_BRIEF.md
-->

Last updated: 2026-06-24
Account used: vishalm111296-commits
Model used: Claude (free)

---

## Current Reality

Goal: Build Module 1 — Data Pipeline (download OHLCV for NSE + Nasdaq universe)
Blocker: none — repo just initialized, ready to start
Confidence: High

---

## Current State

Phase: Building
Active experiment: none
Next action: Write code/01_data_pipeline.py — download Nifty 500 + top 200 Nasdaq OHLCV using yfinance

---

## Key Facts (confirmed)

- FACT: ai-brain-os structure allows any Claude free session to resume with zero context loss
- FACT: yfinance works for both NSE (.NS suffix) and Nasdaq symbols
- FACT: GitHub Actions free = 2000 minutes/month — enough for daily scans
- FACT: Telegram bot API is free with no rate limits for personal use

---

## Current Best Hypothesis

Relative strength momentum on Nifty 500 with a regime filter and 0.2% round-trip costs will produce Sharpe > 1.0 on out-of-sample 2020–2024 data.

---

## Biggest Current Risk

NSE data via yfinance can have gaps and delisted tickers — data validation must run before any scan.

---

## Last Session Summary

What we did: Initialized full akshat-brain repository with all brain-os files
What we found: Structure is clean, all prompts updated with correct URLs
Next session starts with: Step 1 — Write Module 1 data pipeline code
