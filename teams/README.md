# Teams

Kage CTO is the chief of staff. Each team has a lead that reports to the CTO. Build one team at a time. Prove each agent on a small read-only task before adding the next.

| Order | Team | Job | Lead | Adapter | Status |
|---|---|---|---|---|---|
| 1 | CTO | Main contact for owner. Plans, delegates, reviews. | Kage CTO | claude_local | Built: `agents/cto/` |
| 2 | HR | Agent lifecycle: syntactic → semantic → final validation | Kage HR Head | claude_local | **In progress**: `agents/hr-head/`, `hr-onboarding/`, `hr-training/`, `hr-manager/` |
| 3 | Engineering | Code, review, deploy. Mega project + small projects. | Kage Eng Director | claude_local | Planned |
| 4 | Learning | Full learning lifecycle: curriculum → resources → practice → progress | Kage Learning Head | claude_local | Planned |
| 5 | Finance | Budget, salary allocation, investment analysis (advisory only) | Kage Finance Head | claude_local | Planned |
| 6 | Job Search | Job discovery, resume building, application tracking | Kage Job Search Head | claude_local | Planned |
| 7 | Daily Ops | Calendar, email, todos, office tasks | Kage Ops Head | hermes_local | Planned |
| 8 | Platform SME | Hermes, Paperclip, GitHub expertise; daily updates; teach & suggest features | Kage Platform SME Head | hermes_local | **New**: `agents/platform-sme-head/`, `hermes-sme/`, `paperclip-sme/`, `github-sme/` |

## Adapter Policy

- **claude_local**: Stable, well-defined workflows. `dangerouslySkipPermissions: false`.
- **hermes_local**: Self-improving, writes skills. `dangerouslySkipPermissions: true`, `canCreateSkills: true`. Use for: Engineering Leads, Resource Curator, Job Scout, Ops Head, Email Triage, Office Task Handler, **Platform SMEs (all)**.

## Rules for Every Agent

- `dangerouslySkipPermissions` is `false` for claude_local, `true` for hermes_local.
- Each agent has a monthly budget (cents) and turn cap (maxTurnsPerRun).
- Only managers/directors may create agents (`canCreateAgents: true`).
- Only hermes_local agents may create skills (`canCreateSkills: true`).
- HR must approve a new agent before it gets work (three-stage checklist).
- No secrets in this repo. No local paths, no tokens, no live IDs.

## Token Optimization Standards

- Subagent isolation: specialists get fresh context via child issues.
- Structured handoffs: JSON reports (agentstate-compatible) not prose.
- Pydantic output schemas on all validators.
- Prompt caching: stable prefixes first (system prompt → skills → dynamic).
- Tiered thinking budgets: simple=0, moderate=1–2K, complex=5–16K.
- Rolling context window with 10-turn summarization for long sessions.

## Cross-Team Communication

- Primary: Paperclip issue comments, @-mentions, structured interactions.
- Delegation: child issues with `parentId`, `goalId`, `blockedByIssueIds`.
- Shared knowledge: Obsidian vault + Librarian MCP / agentcairn.
- Routines: scheduled heartbeats for daily planning, weekly review, monthly finance sync.