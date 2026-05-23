# Integrations

Optional layers that make the echosystem smarter. Each one is independent — install what you need, skip what you don't.

---

## Available integrations

| Integration | What it does | When to use it |
|-------------|-------------|----------------|
| `context-mode/` | Compresses tool output by 98% — keeps context window lean across long sessions | Always. Install this first. |
| `cortex/` | Persistent memory layer — Claude arrives informed every session, not blank | When your brain is populated enough to benefit from automatic retrieval |

---

## Toggle

Each integration has its own `setup.md` with install and uninstall instructions. Nothing is installed automatically — you choose what runs.

To see what's active: run `/ctx-stats` in Claude Code for context-mode, or check `cortex/status.md` for Cortex.

---

## Install order

1. context-mode first — reduces context pressure immediately
2. Cortex second — once your brain has enough content to retrieve meaningfully
