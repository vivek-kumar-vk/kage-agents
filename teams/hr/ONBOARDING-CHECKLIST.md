# Onboarding Checklist

Use this list for every new agent. Check each item as PASS or FAIL with a one-line reason. All must PASS for approval.

1. **agent.json exists and is valid JSON** — File present at agents/<name>/agent.json and parses without error.
2. **Required fields present** — name, role, reportsTo, adapterType, adapterConfig, runtimeConfig, budgetMonthlyCents, permissions all exist.
3. **name matches folder** — agent.json "name" equals the folder name convention (e.g., "Kage Engineering Lead" for agents/engineering-lead/).
4. **reportsTo points to an existing manager** — Value matches a manager agent's name (e.g., "Kage CTO").
5. **adapterType is claude_local** — Only supported adapter for this org.
6. **model is set and reasonable** — adapterConfig.model uses a known model (e.g., claude-sonnet-4-6, claude-haiku-4-6).
7. **effort is set** — adapterConfig.effort is low, medium, or high.
8. **maxTurnsPerRun is set and > 0** — adapterConfig.maxTurnsPerRun is a positive integer (default 30).
9. **dangerouslySkipPermissions is false** — adapterConfig.dangerouslySkipPermissions === false (never true).
10. **instructionsEntryFile is AGENTS.md** — adapterConfig.instructionsEntryFile === "AGENTS.md".
11. **instructionsBundleMode is managed** — adapterConfig.instructionsBundleMode === "managed".
12. **paperclipSkillSync.desiredSkills is an array** — May be empty or list valid Paperclip skill IDs.
13. **runtimeConfig.heartbeat exists** — heartbeat config present with enabled, intervalSec, maxConcurrentRuns.
14. **budgetMonthlyCents is set and > 0** — budgetMonthlyCents is a positive integer (cents per month).
15. **permissions.canCreateAgents is false** — Only managers (CTO, team leads) may have true.
16. **permissions.canCreateSkills is false** — Only managers may have true.
17. **AGENTS.md exists** — File present at agents/<name>/AGENTS.md.
18. **AGENTS.md has all 5 sections in order** — Role, Scope, Inputs and outputs, Definition of done, Chat hygiene.
19. **Role section names the agent and its manager** — One paragraph, clear who they are and who they report to.
20. **Scope section lists what the agent does and never does** — Clear boundaries, no vague statements.
21. **Inputs and outputs section describes task format and deliverable** — Someone else could hand off a task.
22. **Definition of done is a checkable list** — Another person could verify completion.
23. **Chat hygiene section matches org standard** — Terse, answer first, simple English, no tool narration.
24. **No secrets in either file** — No API keys, tokens, .env refs, local paths, or live IDs.
25. **Test task defined and read-only** — Proposed first task is small, read-only, and verifiable (e.g., "list files in X", "summarize Y").
26. **Test task passes when run manually** — You (HR) simulate or confirm the agent would produce the expected output without side effects.