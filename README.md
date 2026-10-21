# Agentalk for Claude Code

Hear Claude out loud when it finishes a task or needs your approval. This plugin connects Claude Code to [Agentalk](https://apps.apple.com/app/agentalk), a Mac menu bar app that speaks short reports on your Mac, in your language.

## Install

1. Install and open **Agentalk** from the Mac App Store.
2. In Claude Code:

   ```
   /plugin marketplace add iltekin/agentalk-plugin
   /plugin install agentalk@agentalk
   ```

3. Restart Claude Code. Send a test from the Agentalk menu bar icon to check your voice.
4. The first time Claude calls `speak_report`, Claude Code asks for permission: choose to always allow it.

## What the plugin adds

- **Session start hook:** when a session starts, resumes, is cleared or compacted, Agentalk answers with short instructions that Claude Code adds to Claude's context: call `speak_report` at the end of every turn, in your chosen language and length (Agentalk, Settings, General). This keeps Claude writing the spoken summary itself.
- **Hooks** (`hooks/hooks.json`): `Stop`, `SubagentStop` and permission `Notification` events go to Agentalk at `http://127.0.0.1:2026/hook/claude`. If Agentalk is not running, the hooks fail silently and Claude carries on.
- **MCP server** (`.mcp.json`): the `speak_report` tool at `http://127.0.0.1:2026/mcp`, so Claude can write its own spoken summary.
- **Skill** (`skills/spoken-reports`): tells Claude to call `speak_report` once at the end of a task, before waiting for your approval, or when blocked, in one to three plain sentences without code.

When Claude reports through the tool, Agentalk silences the Stop hook of the same turn, so you never hear a turn twice. If Claude forgets the tool, the Stop hook still delivers its final message and Agentalk summarizes it on your Mac (Apple Intelligence).

Agentalk always listens on port 2026, the port the plugin uses.

## Other agents

Codex, Cursor and Gemini CLI connect with a hook snippet you copy from Agentalk, Settings, Connections. Any script can send a report:

```bash
curl -X POST http://127.0.0.1:2026/speak -H 'Content-Type: application/json' \
  -d '{"agent": "My script", "project": "my-app", "text": "The deploy finished."}'
```

## Privacy

Everything stays on your Mac. See [PRIVACY.md](PRIVACY.md).

## License

MIT
