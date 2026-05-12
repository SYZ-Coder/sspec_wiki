---
description: Generate a code knowledge map for a project, service family, feature, or service chain.
argument-hint: "mode=<service_landscape|project|feature|service_chain> scope=<target> goal=<goal>"
---

Use the backend service spec skill as the primary workflow.

Read the skill source from the first available location:

- `.claude/skills/backend-service-spec-skill/SKILL.md`
- `skills/backend-service-spec-skill/SKILL.md`
- `ai-skill-lib/backend-service-spec-skill/SKILL.md`
- `backend-service-spec-skill/SKILL.md`

Then execute the `create_codemap` workflow for:

```text
$ARGUMENTS
```

Before deep scanning, classify the workspace as `single-system`, `service-family`, or `multi-system-workspace`.

Generate Markdown artifacts under `mydocs/codemap/` unless the user gives another path. Keep conclusions grounded in code evidence and mark unresolved items as clue-level or partial evidence.
