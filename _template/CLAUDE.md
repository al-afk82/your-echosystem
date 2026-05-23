# Project Template

This is the reference architecture for any new project in the echosystem.
Read this before creating a new project. It tells you what to build and what to skip.

---

## The principle

Unix style. Each project does one thing well. Clear inputs, clear outputs, clean interface.
A project that tries to do three things is three projects that haven't been separated yet.

---

## Decision guide — what to build

### Always include

| File | Purpose |
|------|---------|
| `CLAUDE.md` | What this project is, how it works, what I load and in what order |
| `README.md` | What it does, how to set it up, how to run it |
| `.gitignore` | Standard — always |

### Include if the project has hard rules that override everything

| File | Purpose |
|------|---------|
| `CHARTER.md` | Constitutional rules. Human-writable only. Overrides CLAUDE.md and all stage files. |

Use CHARTER.md when: the project has rules that must never be overridden by a prompt or a stage instruction — ethical constraints, scope limits, human-in-the-loop requirements.

Skip it when: the project is simple enough that CLAUDE.md rules are sufficient.

### Include if the project has secrets

| File | Purpose |
|------|---------|
| `.env` | Actual secrets — never committed |
| `.env.example` | All variable names, no values — always committed |

### Include if the project has reusable reference material

| Folder | Purpose |
|--------|---------|
| `_core/` | Project-specific skills, domain knowledge, voice rules, quality criteria |

Use `_core/` when: the project has reference material that is specific to this project and not universal enough for the brain. Voice rules for a specific client. Domain knowledge for a specific market. Skills for a specific type of task.

Skip it when: everything the project needs either lives in the brain or is simple enough to put in CLAUDE.md.

### Include if the project is a pipeline with multiple stages

| Folder | Purpose |
|--------|---------|
| `00_[stage-name]/` | First stage — one job, one output |
| `01_[stage-name]/` | Second stage — takes previous stage output |
| `[n]_[stage-name]/STAGE.md` | Stage instructions — scope, input, process, output, stop condition |
| `[n]_[stage-name]/MEMORY.md` | Cross-run learning for this stage only |

Use numbered stages when: the work has a natural sequence where each step has a distinct job and produces a distinct output that a human reviews before the next step begins.

Skip numbered stages when: the work is a single-pass task, a tool, or a service — not a pipeline.

### Include if the project produces client or run outputs

| Folder | Purpose |
|--------|---------|
| `projects/[client-name]/[YYYY-MM-DD]/` | All outputs for a client run, organised by date |

Use this when: the project produces outputs for multiple clients or multiple runs that need to be kept separate and auditable.

Skip it when: the project is a tool or internal system with no external client outputs.

### Include if the project has code

| What | When |
|------|------|
| `src/` | Source code |
| `requirements.txt` or `package.json` | Dependencies |
| `run.py` or equivalent | Entry point |
| `venv/` | Python virtual environment — never committed |

---

## What a minimal project looks like

A project with no pipeline, no secrets, no code:

```
project-name/
├── CLAUDE.md
└── README.md
```

A project with a pipeline, secrets, and reference material:

```
project-name/
├── CHARTER.md
├── CLAUDE.md
├── README.md
├── ACTIVE.md          ← current active run pointer (optional, for multi-run projects)
├── .env
├── .env.example
├── .gitignore
├── _core/
│   ├── skills/
│   └── domain_knowledge.md
├── 00_[stage]/
│   ├── STAGE.md
│   └── MEMORY.md
├── 01_[stage]/
│   ├── STAGE.md
│   └── MEMORY.md
└── projects/
    └── [client-name]/
        └── [YYYY-MM-DD]/
            └── 00_output.md
```

---

## Rules for every project

**CLAUDE.md must answer these four questions:**
1. What does this project do?
2. What does it not do?
3. What do I load and in what order?
4. Where do outputs go?

**Every stage must have a stop condition.**
A stage that doesn't know when to stop will bleed into the next one.

**Every output must be a plain markdown file.**
No JSON as the source of truth. No database as the handoff. A human must be able to read and edit every output in a text editor.

**Reference the brain.**
Every project loads the relevant brain files before doing any work. The brain is the authority on voice, anti-patterns, quality, and constraints. Do not duplicate brain content in `_core/`.

**Feedback flows back.**
At the end of any stage that produces a reusable insight, propose it for the brain. Universal rules belong to everyone — not just the project that discovered them.

---

## Adding a new project to the echosystem

1. Create the project folder at `~/Documents/alecs-echosystem/projects/[project-name]/`
2. Build only what the decision guide says to build — nothing more
3. Add a row to the project registry in `~/Documents/alecs-echosystem/CLAUDE.md`
4. Add a row to `~/Documents/alecs-echosystem/ACTIVE.md` when the first run starts
5. Commit
