# Echosystem

## What this is

A brain-inspired operating environment for Claude. One agent. One brain. Every project compounds on the last.

The model arrives informed — not blank. You populate the brain. Projects build on it. Over time the gap between what you need and what Claude predicts shrinks.

---

## Path anchor

All paths are relative to this file's location. The echosystem root is wherever you cloned this repo.

If this moves to a new machine, update this one line. Everything else resolves from here.

---

## Brain location

`./brain/`

Contains: voice, skills, constraints, knowledge, quality criteria, anti-patterns.
Populated by you. Referenced by every project.

---

## Project registry

| Name | Trigger words | Path | Load order |
|------|--------------|------|------------|
| Learning Loop | corrections, learning, log, protocol, pattern, brain update, conclude, session log, constraints, delta, pending | `./projects/learning-loop/` | CLAUDE.md → PROTOCOL.md → discussions/pending.md |

To add a project: add a row to this table.

## Active run pointer

Read `./ACTIVE.md` at session start for any Tier 3 request. It contains the current active run for each project. Use it to go directly to the right output folder — do not navigate by date.

---

## How Claude operates here

### Tier 1 — Answer directly
No loading required. Applies when the request has no relation to a client, project, pipeline, or brain content.

### Tier 2 — Load brain only
Load the relevant brain file before answering. Applies when the request is about how the system works, voice, skills, or quality standards — but no specific project is referenced.
Load only what is relevant — not everything.

### Tier 3 — Load brain + project
Load relevant brain files first. Then load the project.

Steps:
1. Match the request to a project using trigger words in the registry
2. Load relevant brain files
3. Read the project CLAUDE.md
4. Proceed

### Tier 4 — New project detected
If the user describes something new they want to build — and it does not match any existing project — treat this as a new project signal.

Steps:
1. Load `_template/CLAUDE.md` — read the decision guide
2. Confirm in one line what you understood them to want to build
3. Ask one question if something critical is unclear — otherwise proceed
4. Build only what the decision guide says to build

---

## When no project is named

If the request is clearly Tier 3 but no project is specified:
- If only one project exists: load it
- If multiple projects exist: list them in one line and ask which one — one word answer expected

---

## When the request is ambiguous

Default to Tier 1. Do not load unnecessarily.

---

## What Claude never does here

- Does not ask clarifying questions when the tier is clear
- Does not load project context for general questions
- Does not load the entire brain when only one file is relevant
- Does not explain the routing process — just executes it
- Does not wait to be told "create a new project" — detects the signal and acts
