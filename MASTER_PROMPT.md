# MASTER_PROMPT.md — How Every AI Must Behave

<!--
INSTRUCTIONS FOR EVERY AI:
- Read THIS file FIRST before any other file
- These rules OVERRIDE all default AI behavior
- This is the Akshat AI System running on ai-brain-os operating structure
- Designed for FREE Claude AI at claude.ai (no API key needed)
-->

---

## The One Rule That Overrides Everything

The chat is temporary. The repository is permanent.
The AI is disposable. The files are not.
Every response must leave the repository in a state where
any new AI, any new account, any new model can continue
without ever seeing this conversation.

---

## What This Project Is

Project: **Akshat AI System**
Purpose: Indian + US stock market scanner, relative strength ranker, 3-slap pattern detector, backtester, regime filter, Telegram signal bot
Owner: Vishal (Jammu, Jammu & Kashmir, India)
AI Engine: Claude free tier (claude.ai — no paid API)
Language: Python 3.10+
Platforms: GitHub Actions, Google Colab, Google Sheets, Telegram
Repo: https://github.com/vishalm111296-commits/akshat-brain

---

## Confirmation Gate — Do This Before ANY Work

Before starting any task, output this block EXACTLY:

```
--- UNDERSTANDING CHECK ---
Project: Akshat AI System — stock scanner + RS ranker + backtester
Current state: [where we are right now — from BRAIN.md]
Completed so far: [from CHECKPOINT.md — list or none]
Next action I will take: [exact first step only]
Files I read: MASTER_PROMPT.md, PROJECT_BRIEF.md, BRAIN.md, CHECKPOINT.md
Awaiting confirmation: yes
--- END CHECK ---
```

Wait for user to say **confirmed** or **correct**.
If corrected — update and output the check again.
Never skip this. Never assume understanding is correct.

---

## Core Behavior Rules

- Work ONE step at a time. Never jump ahead.
- After every step: output ALL 4 blocks defined below.
- Wait for the word **committed** before moving to the next step.
- Never assume missing facts. Stop and ask using MISSING INFO block.
- Never repeat completed steps.
- Use project files as the ONLY source of truth.
- End EVERY response with a RESUME BLOCK.
- Assume user is on a mobile phone. Keep every output minimal.
- Never output a full file unless the user explicitly asks.

---

## The 4 Required Blocks After Every Step

Output these 4 blocks in this EXACT order after every completed step.

---

### Block 1 — Step Complete

```
---STEP COMPLETE---
Step: [N — name]
Result: [one sentence summary of what was done]
---END STEP---
```

---

### Block 2 — File Patches

Never say "update BRAIN.md".
Always show EXACT old text and EXACT new text.
Never output full files unless user asks.
One patch block per changed section.

```
---PATCH---
FILE: [filename]

OLD:
[exact text currently in the file]

NEW:
[exact replacement text]
---END PATCH---
```

---

### Block 3 — Treasure Detector

Silently score everything produced in this step.
- Importance 1–7: drop silently. Output nothing. Do not mention it.
- Importance 8–10 ONLY: output one ASSET block.

```
---ASSET---
Name: [short name]
Type: Prompt / Framework / Checklist / Code / Decision Tree / Discovery
Summary: [2–3 sentences — what this is, why it matters]
Reusable: Yes / Partially
Applies To: [all projects / Akshat system only]
Importance: [8 / 9 / 10]
Content:
[paste actual reusable content here]
Save to: ASSETS.md
---END ASSET---
```

If nothing scores 8+: output nothing for Block 3. No placeholder text.

---

### Block 4 — Checkpoint + Resume

```
---CHECKPOINT---
Completed: [Step N — name]
Next: [Step N+1 — name]
Commit message: [short git commit message]
---END CHECKPOINT---

RESUME: To continue, paste prompts/startup.md into a new Claude chat.
Brain: https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/BRAIN.md
Checkpoint: https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/CHECKPOINT.md
```

---

## RESULTS.csv Rule

Every backtest that produces numbers must output this row:

```
---RESULTS ROW---
exp_id,date,description,universe,lookback_days,hold_days,rs_threshold,sharpe,cagr,max_dd,trades,oos_sharpe,status,notes
EXP001,YYYY-MM-DD,[description],[universe],[v],[v],[v],[v],[v],[v],[v],[v],[PASS/FAIL/REVIEW],[notes]
---END RESULTS---
```

User appends this row to RESULTS.csv.

---

## DO_NOT_REPEAT.md Rule

When any idea is rejected or fails:

```
---DO NOT REPEAT---
| [YYYY-MM-DD] | [rejected idea, one line] | [specific reason it failed] | [DEC-ref or EXP-ref] |
---END---
```

---

## Code Output Rule

- Every script must start with: `# Generated: [YYYY-MM-DD] [Claude] Step [N]`
- Output FULL working code — never fragments
- Always include transaction costs: 0.1% entry + 0.1% exit = 0.2% round trip
- Always test on out-of-sample data (last 20% of date range)
- User saves file as: `code/latest.py` AND `code/YYYY-MM-DD-[description].py`

---

## Missing Information Rule

```
---MISSING INFO---
I need: [specific fact]
Why: [why this is required before proceeding]
Please provide this before I continue.
---END---
```

---

## Instruction Priority Order

1. User's current message
2. BRAIN.md (current project state)
3. PROJECT_BRIEF.md (scope and rules)
4. This MASTER_PROMPT.md
5. Default AI behavior

When in doubt: output the conflict and ask.

---

## The Lazy Person Test

Before outputting ANYTHING, ask:
> Can the user copy this and paste it directly into GitHub with zero thinking?

If no — reformat until yes.
