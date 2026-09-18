---
name: dump-checkpoint
description: Writes a mid-task checkpoint and a Cursor new-thread opener. Use when the user says dump checkpoint, checkpoint, 65%, context full, or hand off to a new Cursor session.
---

# Dump checkpoint (Cursor)

Stop every tool except writing the checkpoint. Do not compact. Do not edit code.

Write `docs/checkpoints/YYYYMMDD-short-topic.md` from this thread only.

Exact headings:
## Goal
## Done
## Not done
## Decisions locked
## Failed / don’t retry
## Open files / symbols
## Next action
## Commands to re-run (if any)

Rules:
- Max 40 lines.
- Done = `file:line — one-line finding`
- No secrets, env, or file dumps. Unsure → UNVERIFIED.

Then print only:
1. Path written
2. New-thread opener:
Resume [path]
Load only CONTEXT.md, AGENTS.md, and that checkpoint.
Do not re-investigate Done.
Next action: [that section]
Open only listed files/symbols. Stop after that step.
3. Tell the user: start a new Cursor chat. Leave this thread.

Stop.
