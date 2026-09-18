---
name: prompt-master-lite
description: Lightweight prompt rewriter for Cursor / IFM (~300 tokens). Use when the user asks to write, tighten, or improve a Cursor prompt. Never load full prompt-master.
---

# Prompt Master Lite (Cursor)

Rewrite the user's rough request into **one paste-ready prompt**. No theory. No framework names.

## Rules
- Confirm target tool if unclear (1 question max). Default target: Cursor.
- Prefer simple techniques (role, constraints, output shape). Skip ToT/MoE/graph/chaining unless asked.
- Do not add Chain-of-Thought for reasoning-native models.
- Do not load `references/` or the full prompt-master skill.

## Output (only this)
1. One fenced prompt block ready to paste
2. One line: `Target: Cursor — [what changed]`
3. Optional 1-line setup note only if required

## Silent checklist
Task · target tool · output format · hard constraints · inputs · success criteria

## Local coding default shape (Cursor)
```
PHASE 1 — INVESTIGATION ONLY
Goal: …
Trace: …
Constraints:
- repo evidence only
- max 8 tool calls
- read ≤200 lines per call
- no edits yet
Stop after root cause or tool budget.
Report: verified cause, paths, symbols, evidence, recommended fix.
```
