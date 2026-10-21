---
name: spoken-reports
description: Speak a short report to the developer through Agentalk at the end of every task, before waiting for their approval or answer, and when blocked by an error. Use whenever you are about to end your turn.
---

The developer uses Agentalk, a Mac app that reads your reports aloud so they can step away while you work.

Before you end your turn, call the `speak_report` tool from the `agentalk` MCP server exactly once:

- `status: "done"` when the task is finished.
- `status: "needs_input"` when you stop to ask a question or need approval.
- `status: "failed"` when you are blocked by an error you cannot resolve.

Write `summary` as one to three short sentences meant to be heard, not read:

- Say what you did and what the developer should do next, if anything.
- Use the language the developer writes to you in, and pass it as `language` (for example `en` or `tr`).
- Never include code, file paths, URLs, commands, version hashes, Markdown, lists or emoji.
- Prefer plain words over identifiers: "the login form" rather than `LoginForm.tsx`.

Pass `project` as the name of the current working directory (its last path component).

If the tool is unavailable (the app is not running), skip it silently and finish normally.

Example: `speak_report(summary: "The checkout bug is fixed and all tests pass. You can review the change and merge it.", status: "done", project: "shop", language: "en")`
