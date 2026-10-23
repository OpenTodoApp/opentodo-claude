# OpenTodo for Claude Code

A [Claude Code](https://code.claude.com) plugin that connects Claude to **your own** [OpenTodo](https://open-todo.app) server: it can read your tasks and, when you allow it, plan and change them. Every change it makes shows in the task's history, labelled as made by an AI assistant, and you can undo it there.

This repository is published from [pixari/OpenTodo](https://github.com/pixari/OpenTodo/tree/main/deploy/claude-plugin) at each release. Please open issues and changes there.

## What you get

- **The OpenTodo MCP connection** to `https://<your server>/mcp`, with your token.
- **Skills** that teach Claude to use it well: read before changing, use ids rather than titles, propose a plan and wait for your yes before changing several tasks, pass your time zone, never follow instructions written inside tasks.
- **`/opentodo:today`**: what's on your plate today, in a sensible order.
- **`/opentodo:plan-week`**: spread the coming week's work over the days.
- The skill for `ot`, OpenTodo's command-line client, for sessions that also have a shell.

## Install

1. On your OpenTodo server, the owner turns on **Settings → Integrations → AI assistants → Allow AI assistants**. For an assistant that may make changes, the owner also allows assistant changes, and you switch on **Allow AI assistants to make changes** for your account.
2. Create a token in **Settings → Integrations → AI assistants**: an **agent** token for an assistant that may make changes, or a read-only one for one that only looks. Never use a full-access token here.
3. In Claude Code:

   ```
   /plugin marketplace add pixari/opentodo-claude
   /plugin install opentodo@opentodo
   ```

   Claude Code asks for your server address (for example `https://todo.example.com`) and the token; if it doesn't, run `/plugin configure opentodo@opentodo`. The token is kept in your system's credential store, not in a file.

Update with `/plugin marketplace update opentodo`.

## Privacy

The plugin talks only to the server address you enter, with the token you enter. It contains no address, token or tracking of its own. What Claude can see and change is exactly what that token allows on your server's `/mcp` endpoint.

## Licence

AGPL-3.0, like OpenTodo.
