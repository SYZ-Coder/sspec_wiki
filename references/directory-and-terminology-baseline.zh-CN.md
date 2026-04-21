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
- `mydocs/context/`：过程层，放上下文包、补充材料、家族上下文页
- `mydocs/specs/`：过程层，放 research / plan / review / 规则型补充页
- `mydocs/validation/`：过程层，放验证页、未闭环清单、质量检查页
- `mydocs/index/`：稳定知识层，放总索引、导航页、范围识别页

## 2. 四个核心命令的默认落点

- `create_codemap` -> `mydocs/codemap/`
- `service_deep_dive` -> `mydocs/services/<service>/`
- `build_domain_map` -> `mydocs/domains/<domain>/`
- `crate_router_map` -> `mydocs/routermap/`

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
