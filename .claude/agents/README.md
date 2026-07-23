# Builder Agents

A small crew of specialized Claude Code subagents for building websites and web apps —
plus a `/build` command and a loop to run them on repeat.

## The agents

| Agent | Use it for | Model |
|-------|-----------|-------|
| **product-planner** | Turn an idea into a scoped MVP + numbered build roadmap. Start here for new projects. | sonnet |
| **web-app-builder** | Build/extend the actual app — scaffold, add features, pages, components, wire up data. | sonnet |
| **ui-designer** | Make it look good — styling, responsive layout, color/type system, dark mode, a11y. | sonnet |
| **code-reviewer** | Review the diff for bugs, security, and quality before you ship. Read-only. | sonnet |

## How to use them

**Invoke one directly** — just name it:
- "Use the product-planner to plan a habit-tracker app."
- "Use the web-app-builder to add a leaderboard page to SnapCount."
- "Have the ui-designer polish the scoreboard and add dark mode."
- "Run the code-reviewer over my last change."

**Run a full cycle** with the `/build` command (plan → build → polish → review):
```
/build a mobile-friendly scorekeeping app for pickup basketball
```
or, against the current repo with no argument:
```
/build
```

## The loop

To keep building automatically on an interval, wrap `/build` in the `/loop` skill:
```
/loop 30m /build
```
This runs one build cycle every 30 minutes — each cycle picks the next item off the
roadmap, builds it, polishes it, reviews it, and commits. Stop it anytime by ending
the loop.

> Tip: give the loop a concrete target and a roadmap first (run `/build <idea>` once so
> the planner creates `ROADMAP.md`), so each iteration has a clear next task instead of
> guessing.

## Editing the crew

Each agent is a plain Markdown file in this folder with YAML frontmatter
(`name`, `description`, `tools`, `model`) and a system-prompt body. Tweak the prompts,
swap models, or add new agents (e.g. a `backend-builder` or `test-writer`) by copying
the same format.
