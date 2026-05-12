---
description: Perform a vertical deep dive for one high-value service, module, app, worker, or package.
argument-hint: "scope=<service-or-module> goal=<goal>"
---

Use the backend service spec skill as the primary workflow.

Read the skill source from the first available location:

- `.claude/skills/backend-service-spec-skill/SKILL.md`
- `skills/backend-service-spec-skill/SKILL.md`
- `ai-skill-lib/backend-service-spec-skill/SKILL.md`
- `backend-service-spec-skill/SKILL.md`

If the target is mobile, H5, frontend, Python, or mixed-stack, also read the cross-tech-stack extension from the first available location:

- `.claude/skills/cross-tech-stack-spec-skill/SKILL.md`
- `skills/cross-tech-stack-spec-skill/SKILL.md`
- `ai-skill-lib/cross-tech-stack-spec-skill/SKILL.md`
- `cross-tech-stack-spec-skill/SKILL.md`

Then execute the `service_deep_dive` workflow for:

```text
$ARGUMENTS
```

Generate service or module artifacts under `mydocs/services/` or `mydocs/modules/` unless the user gives another path. Include entrypoints, dependencies, API or contract facts, MQ/events if present, runtime config, and risk hotspots as evidence allows.
