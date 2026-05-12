---
description: Trace a real request, message, callback, gateway, or cross-service route.
argument-hint: "scope=<entry-or-flow> goal=<goal>"
---

Use the backend service spec skill as the primary workflow.

Read the skill source from the first available location:

- `.claude/skills/backend-service-spec-skill/SKILL.md`
- `skills/backend-service-spec-skill/SKILL.md`
- `ai-skill-lib/backend-service-spec-skill/SKILL.md`
- `backend-service-spec-skill/SKILL.md`

If the route crosses frontend, mobile, Python, task, bridge, callback, webhook, or mixed-stack boundaries, also read the cross-tech-stack extension from the first available location:

- `.claude/skills/cross-tech-stack-spec-skill/SKILL.md`
- `skills/cross-tech-stack-spec-skill/SKILL.md`
- `ai-skill-lib/cross-tech-stack-spec-skill/SKILL.md`
- `cross-tech-stack-spec-skill/SKILL.md`

Then execute the `crate_router_map` workflow for:

```text
$ARGUMENTS
```

Generate route artifacts under `mydocs/routermap/` unless the user gives another path. Split synchronous calls, asynchronous messages, scheduled or compensation links, and realtime channels. Mark each segment as `fact-closed`, `fact-send-side`, `fact-receive-side`, `contract-visible`, or `clue`.
