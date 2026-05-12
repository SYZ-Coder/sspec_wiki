---
description: Roll service or module facts up into stable business-domain knowledge pages.
argument-hint: "scope=<system-or-domain> goal=<goal>"
---

Use the backend service spec skill as the primary workflow.

Read the skill source from the first available location:

- `.claude/skills/backend-service-spec-skill/SKILL.md`
- `skills/backend-service-spec-skill/SKILL.md`
- `ai-skill-lib/backend-service-spec-skill/SKILL.md`
- `backend-service-spec-skill/SKILL.md`

If the domain spans frontend, mobile, Python, task, bridge, callback, or mixed-stack layers, also read the cross-tech-stack extension from the first available location:

- `.claude/skills/cross-tech-stack-spec-skill/SKILL.md`
- `skills/cross-tech-stack-spec-skill/SKILL.md`
- `ai-skill-lib/cross-tech-stack-spec-skill/SKILL.md`
- `cross-tech-stack-spec-skill/SKILL.md`

Then execute the `build_domain_map` workflow for:

```text
$ARGUMENTS
```

Generate domain artifacts under `mydocs/domains/` unless the user gives another path. Only roll up lower-level facts; do not invent domain definitions without service, module, route, contract, or configuration evidence.
