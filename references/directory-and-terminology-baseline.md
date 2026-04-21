# Directory And Terminology Baseline

This page is the single baseline for output directories, terminology, and central-knowledge-repository import wording in this repository.

If any other document conflicts with this page, this page wins and the conflicting document should be updated.

## 1. Unified Directory Baseline

Skill outputs should use this unified layout:

```text
mydocs/
  codemap/
  services/
  domains/
  routermap/
  diagrams/
  context/
  specs/
  validation/
  index/
```

Directory meanings:

- `mydocs/codemap/`: index layer for service landscapes, project maps, feature maps, and route indexes
- `mydocs/services/`: stable knowledge layer for single-service deep-dive pages
- `mydocs/domains/`: stable knowledge layer for domain-level knowledge pages
- `mydocs/routermap/`: index layer for cross-service communication routes, interface chains, and message chains
- `mydocs/diagrams/`: index layer for Markdown-embedded Mermaid architecture maps, call graphs, dependency graphs, and sequence diagrams
- `mydocs/context/`: process layer for context packs, supporting material, and family-context pages
- `mydocs/specs/`: process layer for research / plan / review and supplemental rule pages
- `mydocs/validation/`: process layer for validation pages, unresolved lists, and quality checks
- `mydocs/index/`: stable knowledge layer for top-level indexes, navigation pages, and scope-classification pages

## 2. Default Output Locations For The Four Core Commands

- `create_codemap` -> `mydocs/codemap/`
- `service_deep_dive` -> `mydocs/services/<service>/`
- `build_domain_map` -> `mydocs/domains/<domain>/`
- `crate_router_map` -> `mydocs/routermap/`

Diagram outputs should use:

- `mydocs/diagrams/architecture/`
- `mydocs/diagrams/call-graph/`
- `mydocs/diagrams/upstream-downstream/`
- `mydocs/diagrams/sequence/`

## 3. Unified Terminology Baseline

Repository documentation should consistently use these three terms:

### 3.1 Index Layer

Use this for:

- service maps
- overview maps
- route indexes
- route maps
- navigation-oriented intermediate pages

Default directories:

- `mydocs/codemap/`
- `mydocs/routermap/`
- `mydocs/diagrams/`

### 3.2 Stable Knowledge Layer

Use this for:

- single-service knowledge pages
- business-domain knowledge pages
- top-level index pages
- reusable pages that should keep stable naming across runs

Default directories:

- `mydocs/services/`
- `mydocs/domains/`
- `mydocs/index/`

### 3.3 Process Layer

Use this for:

- research / plan / review
- validation
- context
- round-specific supporting material

Default directories:

- `mydocs/context/`
- `mydocs/specs/`
- `mydocs/validation/`

## 4. Deprecated Old Directory Wording

The following should no longer be used as default skill-output directories:

- `project/services/`
- `project/domains/`
- `project/index/`
- `mydocs/domain/`

If these appear again in skill docs, README files, templates, or quick references, treat them as wording bugs to be corrected.

## 5. Unified Wording For Central Knowledge Repository Import

Default skill outputs should still live in `mydocs/`.

If content needs to be imported into a central knowledge repository, prefer neutral intake-layer wording such as:

```text
sources/codemap-import/<batch>/
architecture/
standards/
openspec/specs/
```

Do not describe central-repository intake paths as if they were the default skill-output directories.

## 6. Documentation Maintenance Rule

When updating the following documents, check them against this page first:

- root `README.md` / `README.zh-CN.md`
- `backend-service-spec-skill/README.md`
- `backend-service-spec-skill/README.zh-CN.md`
- `backend-service-spec-skill/references/command-output-map*`
- `backend-service-spec-skill/references/command-output-scenario-quickref*`
- `backend-service-spec-skill/references/output-templates.md`
- `references/mydocs-to-central-knowledge-repo*`

Any new document that mentions output directories, template destinations, or central knowledge repository import wording should also follow this baseline.

## 7. Diagram Artifact Baseline

To keep diagrams reliably reusable by AI, diagram outputs should default to `Markdown + Mermaid`, not image-only files.

Recommended rules:

- use `.md` as the default diagram file format
- embed Mermaid inside fenced code blocks
- add a short note below the diagram explaining node meaning, edge meaning, evidence sources, and unresolved gaps
- PNG / SVG exports may be generated as derived artifacts, but should not replace the `.md` source file

Placement rule:

- diagrams should be embedded in the corresponding document by default
- use `mydocs/diagrams/` only when the diagram needs cross-document reuse, independent frequent updates, centralized export/management, or when the user explicitly asks for diagram/text separation
- if a diagram is split into `mydocs/diagrams/`, the corresponding document should keep a short inline note plus a direct link to that diagram so AI and human readers can still follow the context

Recommended examples:

```text
mydocs/diagrams/architecture/<scope>-architecture.md
mydocs/diagrams/call-graph/<scope>-call-graph.md
mydocs/diagrams/upstream-downstream/<service>-dependencies.md
mydocs/diagrams/sequence/<flow>-sequence.md
```
