# Onboarding Checklist

Used by Kage HR Head to orchestrate three specialists. Each specialist runs their assigned items.

---

## Stage 1: Syntactic Validation (Kage HR Onboarding)
*Deterministic, schema-based checks. All must PASS.*

1. **agent.json exists and is valid JSON** — File present at agents/<name>/agent.json and parses without error.
2. **Required fields present** — name, role, reportsTo, adapterType, adapterConfig, runtimeConfig, budgetMonthlyCents, permissions all exist.
3. **name matches folder** — agent.json "name" equals the folder name convention (e.g., "Kage Engineering Lead" for agents/engineering-lead/).
4. **reportsTo points to an existing manager** — Value matches a manager agent's name (e.g., "Kage CTO", "Kage HR Head", "Kage Eng Director").
5. **adapterType is claude_local or hermes_local** — Only supported adapters for this org.
6. **model is set and reasonable** — adapterConfig.model uses a known model (e.g., claude-sonnet-4-6, claude-haiku-4-6).
7. **effort is set** — adapterConfig.effort is low, medium, or high.
8. **maxTurnsPerRun is set and > 0** — adapterConfig.maxTurnsPerRun is a positive integer (default 30 for claude_local, 50 for hermes_local).
9. **dangerouslySkipPermissions is false for claude_local** — If adapterType is claude_local, must be false. If hermes_local, true is allowed.
10. **instructionsEntryFile is AGENTS.md** — adapterConfig.instructionsEntryFile === "AGENTS.md".
11. **instructionsBundleMode is managed** — adapterConfig.instructionsBundleMode === "managed".
12. **paperclipSkillSync.desiredSkills is an array** — May be empty or list valid skill keys.
13. **runtimeConfig.heartbeat exists** — heartbeat config present with enabled, intervalSec, maxConcurrentRuns.
14. **budgetMonthlyCents is set and > 0** — budgetMonthlyCents is a positive integer (cents per month).
15. **permissions.canCreateAgents matches role** — true only for managers/directors (CTO, HR Head, Eng Director, team leads).
16. **permissions.canCreateSkills matches adapter** — true only for hermes_local agents.

---

## Stage 2: Semantic Validation (Kage HR Training)
*LLM-judged checks. All must PASS.*

17. **AGENTS.md exists** — File present at agents/<name>/AGENTS.md.
18. **AGENTS.md has all 5 sections in order** — Role, Scope, Inputs and outputs, Definition of done, Chat hygiene.
19. **Role section names the agent and its manager** — One paragraph, clear who they are and who they report to.
20. **Scope section lists what the agent does and never does** — Clear boundaries, no vague statements.
21. **Inputs and outputs section describes task format and deliverable** — Someone else could hand off a task.
22. **Definition of done is a checkable list** — Another person could verify completion.
23. **Chat hygiene section matches org standard** — Terse, answer first, simple English, no tool narration.
24. **No secrets in either file** — No API keys, tokens, .env refs, local paths, or live IDs.
25. **Skill matching: desiredSkills align with role** — Three-stage match (keyword → embedding → LLM) against company skill library. At least 80% of requested skills match relevant descriptors.
26. **Test task defined and read-only** — Proposed first task is small, read-only, and verifiable (e.g., "list files in X", "summarize Y").
27. **Test task relevance** — Test task exercises the agent's declared role and skills.

---

## Stage 3: Final Compliance Review (Kage HR Manager)
*Policy gates. All must PASS for approval.*

28. **Both specialist reports overall=PASS** — Onboarding and Training stages have no FAIL items.
29. **Budget approved** — budgetMonthlyCents within team limits (specialist ≤2000, manager ≤5000, director ≤10000).
30. **Permissions policy compliant** — canCreateAgents/canCreateSkills match role and adapter type.
31. **Audit trail complete** — Both specialist reports include timestamps, tokens_used, and check details.
32. **No policy violations** — Agent config doesn't violate org rules (e.g., no external API calls without MCP, no secret refs in files).
33. **Re-review path defined** — If BLOCKED, blocking_issues list specific fixes for re-submission.

---

## Scoring

| Stage | Items | Pass Threshold |
|-------|-------|----------------|
| 1: Syntactic | 1–16 | 16/16 PASS |
| 2: Semantic | 17–27 | 11/11 PASS |
| 3: Compliance | 28–33 | 6/6 PASS |

**Final Decision:** APPROVED only if all three stages PASS. BLOCKED if any item FAILS.