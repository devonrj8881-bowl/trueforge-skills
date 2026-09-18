---
name: graphify
description: Locate PropEdge symbols via the graphify CLI. Not an MCP server. Use before grepping. Cap output with --budget.
---

# Graphify

Binary: `graphify` (`~/.local/bin/graphify`). Graph: `graphify-out/graph.json` (already built). Do not rebuild. Do not start `graphify --mcp`.

```bash
GRAPH=/Users/devonjohnson/Developer/PropEdge/graphify-out/graph.json
graphify explain "fetchProps()" --graph "$GRAPH"
graphify path "PicksScreen()" "fetchProps()" --graph "$GRAPH"
graphify query "featured pick load" --graph "$GRAPH" --budget 800
```

Rules:
- One command per step. `--budget` 800 (max 1500).
- Keep only cited `file:line`. Read ≤120 lines there.
- Never paste NODE lists back into the next turn.
- GitHub work uses `gh`, not GitHub MCP.
