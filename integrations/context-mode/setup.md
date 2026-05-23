# Context Mode

Sits between Claude Code and tool outputs. Compresses raw output by up to 98% — a 315KB session becomes 5KB. Keeps the context window lean across long sessions so Claude doesn't lose the thread.

**What it does:** Intercepts Bash, Read, Grep, WebFetch, and Task tool calls. Sandboxes the output. Returns only what's relevant. You never see the difference — Claude just works longer without degrading.

---

## Install

Requires Claude Code v1.0.33+. Run both commands inside Claude Code:

```
/plugin marketplace add mksglu/claude-context-mode
/plugin install context-mode@claude-context-mode
```

Restart Claude Code after installing.

---

## Verify

Run inside Claude Code:

```
/ctx-stats
```

Shows compression stats for the current session. If it returns data, it's running.

---

## Toggle off

To disable without uninstalling:

```
/plugin disable context-mode
```

To re-enable:

```
/plugin enable context-mode
```

To uninstall completely:

```
/plugin remove context-mode
```

---

## Why install this first

Context-mode has no dependencies and immediate benefit. Every session from the moment it's installed runs leaner. The longer the session, the more it helps. Install it before Cortex — Cortex retrieves more efficiently when the context window isn't already bloated.

---

Source: [github.com/mksglu/context-mode](https://github.com/mksglu/context-mode)
