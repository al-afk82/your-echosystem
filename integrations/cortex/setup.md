# Cortex

A persistent memory layer between your brain files and Claude. Claude arrives informed every session — not blank. No more re-explaining yourself from scratch.

**What it does:** Indexes your brain files using vector embeddings. At session start, injects the most relevant context automatically. Memories decay if unused, strengthen if accessed often. Fire together, wire together.

**The principle:** Files own the truth. The brain owns the connections.

---

## When to install

Install Cortex after your brain has real content — at least voice, anti-patterns, and quality criteria populated. An empty brain gives Cortex nothing to retrieve. Wait until the brain is working before adding the retrieval layer.

---

## Requirements

- Python 3.10+
- UV package manager

---

## Install UV

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Install Python 3.11 via UV

```bash
uv python install 3.11
```

UV manages its own Python — your system Python is untouched.

## Install CortexGraph

```bash
uv tool install cortexgraph
```

---

## Configure

Point Cortex at your brain files. Edit `~/.config/cortexgraph/.env`:

```
MEMORY_DIR=~/Documents/your-echosystem/brain
STM_HALF_LIFE_DAYS=3
DECAY_MODEL=exponential
```

Adjust `MEMORY_DIR` to wherever your echosystem lives.

---

## Wire into Claude Code

Add to your Claude Code MCP config (`~/.claude/settings.json`):

```json
{
  "mcpServers": {
    "cortexgraph": {
      "command": "cortexgraph",
      "args": []
    }
  }
}
```

Restart Claude Code after adding.

---

## Verify

Ask Claude in a new session:

> "What do you know about me from memory?"

If Cortex is running, Claude surfaces what it retrieved from your brain files without being told to load anything.

---

## Toggle off

Remove the `cortexgraph` entry from `~/.claude/settings.json` and restart Claude Code. Your brain files are untouched — the index is derived, always rebuildable.

To rebuild the index from scratch:

```bash
cortexgraph rebuild
```

---

## What Cortex stores

- **Short-term memory:** JSONL files — session-level, decays over days
- **Long-term memory:** Markdown files — your brain/ folder, durable

Delete the index anytime. Rebuild from your files with one command. You never lose the source of truth.

---

Source: [github.com/prefrontal-systems/cortexgraph](https://github.com/prefrontal-systems/cortexgraph) — inspired by [aris-space.com/documents/memory/cortex](https://www.aris-space.com/documents/memory/cortex)
