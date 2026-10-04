# Skills Manifest

All custom skills referenced in agent `desiredSkills` that must be created in Paperclip Skill Studio before agents can run.

---

## Paperclip Built-in Skills (Already Available)

| Skill Key | Purpose |
|-----------|---------|
| `paperclipai/paperclip/paperclip` | Core Paperclip orchestration |
| `paperclipai/paperclip/paperclip-board` | Board/task management |
| `paperclipai/paperclip/paperclip-converting-plans-to-tasks` | Plan → task decomposition |
| `paperclipai/paperclip/paperclip-create-agent` | Dynamic agent creation (used by Small PM) |
| `paperclipai/paperclip/para-memory-files` | Long-term memory |
| `paperclipai/paperclip/first-task` | First task onboarding |

---

## Custom Skills Required (Grouped by Domain)

### HR Domain
| Skill Key | Referenced By | Description |
|-----------|---------------|-------------|
| `hr-policy-validator` | HR Head, HR Onboarding, HR Training, HR Manager | Validates agent configs against HR policies |
| `skill-matching-engine` | HR Training | Three-stage skill matching (keyword → embedding → LLM) |

### Engineering Domain
| Skill Key | Referenced By | Description |
|-----------|---------------|-------------|
| `github-pr-workflow` | Eng Director, Mega PM, Mega DevOps, Small PM | GitHub PR creation, review, merge workflow |
| `task-planning` | Eng Director, Mega PM, Small PM | Epic → task decomposition |
| `issue-triage` | Mega PM, Small PM | Issue categorization, priority assignment |
| `ci-cd-pipeline` | Mega DevOps | CI/CD pipeline management |
| `infrastructure-as-code` | Mega DevOps | Terraform, Kubernetes, Docker management |
| `code-review` | Mega Lead (implicit) | Automated code review assistance |
| `qa-acceptance` | Mega Lead (implicit) | QA acceptance criteria validation |

### Learning Domain
| Skill Key | Referenced By | Description |
|-----------|---------------|-------------|
| `curriculum-planning` | Learning Head, Curriculum Designer | Structured curriculum design |
| `skill-gap-analysis` | Curriculum Designer | Identify missing skills for goals |
| `resource-discovery` | Resource Curator (implicit) | Find learning resources across sources |
| `exercise-generation` | Practice Coach | Create practice exercises, quizzes, projects |
| `progress-tracking` | Learning Head, Practice Coach | Track mastery, streaks, milestones |

### Finance Domain
| Skill Key | Referenced By | Description |
|-----------|---------------|-------------|
| `ynab-budgeting` | Finance Head, Budget Tracker | YNAB API integration, budget sync |
| `expense-categorization` | Budget Tracker | Auto-categorize transactions |
| `goal-projection` | Budget Tracker | Cash flow projections, goal tracking |
| `investment-research` | Finance Head, Investment Advisor | Market research, opportunity analysis |
| `portfolio-analysis` | Investment Advisor | Portfolio health, diversification |
| `risk-assessment` | Investment Advisor | Risk scoring, stress testing |

### Job Search Domain
| Skill Key | Referenced By | Description |
|-----------|---------------|-------------|
| `job-search-multi-source` | Job Search Head, Job Scout | Search LinkedIn, Indeed, 8 ATS sources |
| `application-tracking` | Job Search Head, App Tracker | Track application lifecycle |
| `resume-optimization` | Resume Builder | Tailor resume to job description |
| `cover-letter-generation` | Resume Builder | Generate company-specific cover letters |
| `ats-optimization` | Resume Builder | ATS keyword optimization |
| `interview-prep` | App Tracker | Interview preparation materials |
| `follow-up-automation` | App Tracker | Automated follow-up emails |

### Daily Ops Domain
| Skill Key | Referenced By | Description |
|-----------|---------------|-------------|
| `calendar-optimization` | Calendar Manager | Time-blocking, meeting scheduling |
| `meeting-scheduling` | Calendar Manager | Find optimal slots, send invites |
| `time-blocking` | Calendar Manager | Deep work blocks, energy matching |
| `email-triage` | Email Triage (implicit) | Categorize, draft responses, extract tasks |
| `todo-management` | Todo Manager | Master task list, prioritization |
| `task-prioritization` | Todo Manager | Eisenhower matrix, energy matching |
| `habit-tracking` | Todo Manager | Daily/weekly habits, streaks |
| `office-automation` | Office Handler (implicit) | Expenses, travel, vendor research, docs |

---

## Skill Creation Priority

### Phase 1 (Core - needed for HR onboarding to work)
1. `hr-policy-validator` — Validates agent configs
2. `skill-matching-engine` — Matches skills to roles

### Phase 2 (Engineering - needed for Mega Project)
3. `github-pr-workflow` — PR workflow
4. `task-planning` — Epic decomposition
5. `issue-triage` — Issue management
6. `ci-cd-pipeline` — CI/CD
7. `infrastructure-as-code` — Infra as code

### Phase 3 (Learning)
8. `curriculum-planning`
9. `skill-gap-analysis`
10. `exercise-generation`
11. `progress-tracking`

### Phase 4 (Finance)
12. `ynab-budgeting`
13. `expense-categorization`
14. `goal-projection`
15. `investment-research`
16. `portfolio-analysis`
17. `risk-assessment`

### Phase 5 (Job Search)
18. `job-search-multi-source`
19. `application-tracking`
20. `resume-optimization`
21. `cover-letter-generation`
22. `ats-optimization`
23. `interview-prep`
24. `follow-up-automation`

### Phase 6 (Daily Ops)
25. `calendar-optimization`
26. `meeting-scheduling`
27. `time-blocking`
28. `email-triage`
29. `todo-management`
30. `task-prioritization`
31. `habit-tracking`
32. `office-automation`

---

## Skill Structure (SKILL.md)

Each skill must follow the SKILL.md format:

```
skill-folder/
├── SKILL.md          # YAML frontmatter + markdown instructions
├── references/       # Optional reference docs
├── scripts/          # Optional executable scripts
└── assets/           # Optional assets
```

**SKILL.md frontmatter:**
```yaml
name: "Skill Name"
description: >
  Use when: [specific trigger conditions]
  Don't use when: [exclusions]
  Returns: [what the skill produces]
```

---

## MCP Servers Required (Per Domain)

| Domain | MCP Servers |
|--------|-------------|
| Engineering | GitHub, GitLab, Playwright, mcp-atlassian |
| Learning | YouTube, Coursera, ArXiv, Playwright |
| Finance | YNAB (primary), CoinMarket |
| Job Search | servation/job-search-mcp, Indeed, LinkedIn |
| Daily Ops | Google Workspace (Gmail+Calendar), Outlook, Playwright |
| HR | Paperclip built-in |

---

## Notes

- Skills are installed in Paperclip Skill Studio (web UI) or via CLI
- Custom skills can reference MCP servers in their scripts
- Skill descriptions should be routing logic: "Use when X, Don't use when Y"
- Hermes agents (Mega Lead, Mega Backend, Mega Frontend, Resource Curator, Job Scout, Ops Head, Email Triage, Office Handler, Small Lead, Small Engineer) will create skills dynamically — review in Skill Studio