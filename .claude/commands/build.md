---
description: Drive one full build cycle for a website/app using the builder agents (plan → build → polish → review).
---

Run one complete build cycle for the project described in the arguments (or, if no argument, for the project in the current repo). Use the specialized builder agents in `.claude/agents/` to do the work.

Target / instruction for this cycle: $ARGUMENTS

Steps:

1. **Plan (only if there's no existing plan or backlog).** If this is a fresh idea with no roadmap yet, use the `product-planner` agent to produce an MVP scope and a numbered milestone roadmap. Save the roadmap where the next cycle can find it (e.g. a `ROADMAP.md`). If a roadmap already exists, skip planning and pick the next unchecked item.

2. **Build.** Use the `web-app-builder` agent to implement the next item — a new feature, page, component, or the requested change. It should leave the project in a runnable state.

3. **Polish.** Use the `ui-designer` agent to make the new/changed UI look clean, consistent, and responsive (light + dark, mobile + desktop). Skip only if the change was purely non-visual.

4. **Review.** Use the `code-reviewer` agent on the diff. If it flags critical or high-severity issues, fix them (via `web-app-builder`) before finishing the cycle.

5. **Report & mark progress.** Summarize what got built this cycle, check off the roadmap item, and note what the next cycle should tackle. Commit the work with a clear message.

Keep each cycle focused on ONE meaningful increment so it stays reviewable and the loop makes steady, visible progress.

To run this on a recurring interval, use the `/loop` skill, e.g. `/loop 30m /build`.
