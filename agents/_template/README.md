# Agent template

Copy this folder to `agents/<name>/` and fill in both files. Use `agents/cto/` as the worked example.

## agent.json
Same shape as `agents/cto/agent.json`. Set:
- `name`, `role`, `reportsTo` (the manager's name, e.g. "Kage CTO")
- `adapterType`: `claude_local` (runs the local Claude Code CLI on the owner's subscription)
- `adapterConfig.model`: use the cheapest model that can do the job. `maxTurnsPerRun`: 30 unless there is a reason.
- `dangerouslySkipPermissions`: always `false`
- `budgetMonthlyCents`: set a real cap
- `permissions`: `canCreateAgents` only for managers

## AGENTS.md (the instructions)
Sections, in this order:
1. **Role**: one paragraph. Who you are, who you report to.
2. **Scope**: what you do, and what you must never do.
3. **Inputs and outputs**: what a task looks like when it arrives, and what you hand back.
4. **Definition of done**: a short list that someone else could check.
5. **Chat hygiene**: terse, answer first, simple English (close to ASD-STE100), do not narrate tool calls.
