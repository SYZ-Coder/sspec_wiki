# 目录与术语统一基准

本文是本仓库关于产物目录、术语口径、中央知识库导入说明的统一基准页。

如果其他文档与本文不一致，以本文为准，并回改冲突文档。

## 1. 统一目录基线

技能默认产物统一放在：

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

各目录含义：

- `mydocs/codemap/`：索引层，放服务总图、项目总图、功能地图、链路索引
- `mydocs/services/`：稳定知识层，放单服务纵切知识页
- `mydocs/domains/`：稳定知识层，放业务域上卷知识页
- `mydocs/routermap/`：索引层，放跨服务通信链路、接口链路、消息链路
- `mydocs/diagrams/`：索引层，放 Markdown 内嵌 Mermaid 的架构图、调用关系图、上下游依赖图、时序图
- `mydocs/context/`：过程层，放上下文包、补充材料、家族上下文页
- `mydocs/specs/`：过程层，放 research / plan / review / 规则型补充页
- `mydocs/validation/`：过程层，放验证页、未闭环清单、质量检查页
- `mydocs/index/`：稳定知识层，放总索引、导航页、范围识别页

## 2. 四个核心命令的默认落点

- `create_codemap` -> `mydocs/codemap/`
- `service_deep_dive` -> `mydocs/services/<service>/`
- `build_domain_map` -> `mydocs/domains/<domain>/`
- `crate_router_map` -> `mydocs/routermap/`

图类产物统一落在：

- `mydocs/diagrams/architecture/`
- `mydocs/diagrams/call-graph/`
- `mydocs/diagrams/upstream-downstream/`
- `mydocs/diagrams/sequence/`

## 3. 统一术语基线

全仓文档统一使用下面三类术语：

### 3.1 索引层

用于表达：

- 服务地图
- 总图
- 链路索引
- 路由图
- 用于导航和定位的中间页

默认对应目录：

- `mydocs/codemap/`
- `mydocs/routermap/`
- `mydocs/diagrams/`

### 3.2 稳定知识层

用于表达：

- 单服务知识页
- 业务域知识页
- 总索引页
- 跨轮次可复用、应保持稳定命名的正文页

默认对应目录：

- `mydocs/services/`
- `mydocs/domains/`
- `mydocs/index/`

### 3.3 过程层

用于表达：

- research / plan / review
- validation
- context
- 本轮过程性补充材料

默认对应目录：

- `mydocs/context/`
- `mydocs/specs/`
- `mydocs/validation/`

## 4. 禁止再使用的旧口径

以下目录口径不再作为技能默认产物规则使用：

- `project/services/`
- `project/domains/`
- `project/index/`
- `mydocs/domain/`

如果这些路径再次出现在技能说明、README、模板、速查表中，应视为待修正文案。

## 5. 中央知识库导入说明的统一口径

技能默认输出仍然统一放在 `mydocs/`。

如果需要导入中央知识库，推荐使用中性接收层表述：

```text
sources/codemap-import/<batch>/
architecture/
standards/
openspec/specs/
```

不要再把中央知识库接收层写成技能默认产物目录。

## 6. 文档维护规则

后续修改以下文档时，都应先对照本文：

- 根目录 `README.md` / `README.zh-CN.md`
- `backend-service-spec-skill/README.md`
- `backend-service-spec-skill/README.zh-CN.md`
- `backend-service-spec-skill/references/command-output-map*`
- `backend-service-spec-skill/references/command-output-scenario-quickref*`
- `backend-service-spec-skill/references/output-templates.md`
- `references/mydocs-to-central-knowledge-repo*`

如果新增文档涉及产物目录、模板落点、中央知识库导入说明，也应引用本文规则。

## 7. 图产物基线

为了让 AI 稳定复用图信息，图类产物默认使用 `Markdown + Mermaid`，而不是只输出图片。

推荐规则：

- 图文件默认使用 `.md`
- 图内容使用 fenced code block 包裹 Mermaid
- 图下方补一段文字说明节点含义、边含义、证据来源与未闭环项
- 如需导出 PNG / SVG，可作为派生结果，但不应替代 `.md` 源文件

放置规则：

- 默认应把图直接内嵌到对应正文文档
- 只有在图需要跨文档复用、需要独立高频更新、需要集中导出或管理，或用户明确要求图文分离时，才使用 `mydocs/diagrams/`
- 如果图拆分到了 `mydocs/diagrams/`，对应正文中仍应保留简短说明，并附上该图的直接链接，保证 AI 和人工阅读时上下文不断裂

推荐文件示例：

```text
mydocs/diagrams/architecture/<scope>-architecture.md
mydocs/diagrams/call-graph/<scope>-call-graph.md
mydocs/diagrams/upstream-downstream/<service>-dependencies.md
mydocs/diagrams/sequence/<flow>-sequence.md
```
