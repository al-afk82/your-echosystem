# Your Echosystem

A brain-inspired operating environment for Claude. One agent. One brain. Every project compounds on the last.

The model arrives informed — not blank. You populate the brain with your voice, your standards, your knowledge. Projects build on it. Over time the gap between what you need and what Claude predicts shrinks.

---

## The principle

**Files own the truth. The brain owns the connections.**

Your notes, decisions, and outputs stay in plain markdown — readable, editable, git-friendly. The brain indexes them and makes them retrievable by meaning, not by path.

---

## How to set it up

**1. Clone this repo**
```bash
git clone https://github.com/al-afk82/your-echosystem.git
cd your-echosystem
```

**2. Open it in Claude Code**
```bash
claude .
```

**3. Populate your brain**

Start with voice. Open `brain/voice/` and create `voice_guide.md`. Answer three questions:
- How do you write?
- What do you never write?
- What does good output look like for you?

Then add anti-patterns, quality criteria, and constraints as they emerge from real work — not upfront.

**4. Add your first project**

Read `_template/CLAUDE.md`. It tells you exactly what to build and what to skip.

**5. Start working**

The learning loop is already running. At the end of every unit of work, Claude asks one question. Answer it honestly. The brain gets richer from there.

---

## What's included

| What | Where | Purpose |
|------|-------|---------|
| Brain structure | `brain/` | Empty — you populate it |
| Learning loop | `projects/learning-loop/` | Captures deltas, feeds brain |
| Project template | `_template/` | Blueprint for new projects |
| Active run pointer | `ACTIVE.md` | Current run tracker |
| Routing instructions | `CLAUDE.md` | How Claude operates here |

---

## How the brain grows

You don't fill the brain upfront. You work. At the end of each unit of work, Claude surfaces what it got wrong and why. You validate it. It gets logged. When a pattern appears three times across three sessions, it gets proposed for the brain. You approve it. The brain gets richer. Claude gets closer.

That's the loop. It runs itself.

---

## Adding a new project

Read `_template/CLAUDE.md`. Follow the decision guide. Add a row to the project registry in `CLAUDE.md`. Start building.

---

## The learning loop

Already running. No setup required. Read `projects/learning-loop/CLAUDE.md` to understand how it works.

---

## Integrations

Two optional layers that make the echosystem smarter. Both are toggleable — install what you need.

| Integration | What it does |
|-------------|-------------|
| [Context Mode](integrations/context-mode/setup.md) | Compresses tool output by 98% — keeps sessions lean |
| [Cortex](integrations/cortex/setup.md) | Persistent memory — Claude arrives informed, not blank |

Install context-mode first. Install Cortex once your brain has real content.

---

## The principle

Files own the truth. The brain owns the connections.
