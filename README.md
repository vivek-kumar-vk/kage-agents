# kage-agents

Public spec for a small company of AI agents, run in [Paperclip](https://github.com/paperclipai/paperclip) using Claude Code (`claude_local` adapter).

## For PromptQL / any builder
Goal: build every agent below the CTO, end to end.

1. Read `agents/cto/agent.json` and `agents/cto/AGENTS.md`. They are the working reference.
2. Read `teams/README.md` for the team plan, order and shared rules.
3. For each new agent, copy `agents/_template/` and follow its README.
4. Each agent gets two files: `agent.json` and `AGENTS.md`. Open a pull request per agent. Do not push to `main`.

## What is not here
No secrets, local paths or live IDs. Keep it that way: never add API keys, tokens, `.env` files, or company/agent IDs.
