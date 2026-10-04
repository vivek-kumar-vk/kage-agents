# Teams

CTO is the head. Each team gets a lead agent that reports to the CTO. Build one team at a time. Prove each agent on a small read-only task before adding the next.

| Order | Team | Job | Notes |
|---|---|---|---|
| 1 | CTO | Main contact for the owner. Plans, delegates, reviews. | Built. See `agents/cto/`. |
| 2 | HR / Onboarding | Check that a new agent is ready before it works: config valid, permissions minimal, budget set, instructions complete, test task passed. | Needs a checklist file: `teams/hr/ONBOARDING-CHECKLIST.md`. |
| 3 | Engineering | Build and fix code. Every change is reviewed by a second agent. | Lead plus a reviewer. |
| 4 | Productivity | Notes, planning, summaries, reminders. | Read-mostly. |
| 5+ | More teams | The owner adds them here. | Add one row per team. |

## Rules for every agent
- `dangerouslySkipPermissions` stays `false`.
- Each agent has a monthly budget and a turn cap.
- Only managers may create agents. HR must approve a new agent before it gets work.
- No secrets in this repo. No local paths, no tokens, no IDs from the live system.
