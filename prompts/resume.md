# resume.md — Use This When a Session Ends Early

If Claude runs out of tokens or session is interrupted:

1. Open a new Claude free chat
2. Paste the startup prompt below
3. Claude reads the 4 files and outputs UNDERSTANDING CHECK
4. Type: `confirmed`
5. Claude continues from exact step in CHECKPOINT.md

---

```
Read these 4 files in order:
1. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/MASTER_PROMPT.md
2. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/PROJECT_BRIEF.md
3. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/BRAIN.md
4. https://raw.githubusercontent.com/vishalm111296-commits/akshat-brain/main/CHECKPOINT.md

After reading all 4, output the UNDERSTANDING CHECK.
My previous session ended. Resume from where CHECKPOINT.md says to resume.
Wait for my confirmation before doing anything.
```
