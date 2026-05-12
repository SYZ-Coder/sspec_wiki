# 安装指南

这个仓库更适合作为 AI 开发工具的技能源与规则源来使用。

它支持两种接入方式：

1. 原生技能目录安装
2. 仓库规则 / 指令接入

## 1. 快速选择

先按工具类型选择：

- `Codex`：把技能目录复制到本地 Codex 技能目录
- `Claude Code / Claude`：通过 `CLAUDE.md` 或项目指令引用本仓库
- `Cursor`：通过 `.cursor/rules/` 引用本仓库
- `VS Code + AI 扩展`：通过项目规则、prompt 或文档引用本仓库
- 其他 AI 工具：使用文末的“通用接入模板”

## 2. Codex

把下面两个目录复制到 Codex 的技能目录：

- `backend-service-spec-skill`
- `cross-tech-stack-spec-skill`

常见技能目录：

- Windows：`%USERPROFILE%\\.codex\\skills\\`
- macOS：`~/.codex/skills/`
- Linux：`~/.codex/skills/`

建议步骤：

1. 克隆本仓库。
2. 把 `backend-service-spec-skill` 复制到 Codex 技能目录。
3. 把 `cross-tech-stack-spec-skill` 复制到 Codex 技能目录。
4. 重启 Codex 或开启新会话。

示例：

```text
请用 $backend-service-spec-skill 梳理这个后端微服务项目。
```

```text
请以 $backend-service-spec-skill 为主流程，并启用 $cross-tech-stack-spec-skill 做混合栈适配。
```

## 3. Claude Code / Claude

Claude Code 可以分三层接入。

### 3.1 基础方式：`CLAUDE.md`

适合只想让 Claude Code 理解这套规则，但不需要 slash command 的项目。

1. 把本仓库克隆到项目内或项目旁，例如 `ai-skill-lib/`。
2. 创建或更新 `CLAUDE.md`。
3. 引用这两个文件：
   - `./ai-skill-lib/backend-service-spec-skill/SKILL.md`
   - `./ai-skill-lib/cross-tech-stack-spec-skill/SKILL.md`

`CLAUDE.md` 示例：

```md
本项目分析时，使用以下仓库作为规则源：

- ./ai-skill-lib/backend-service-spec-skill/SKILL.md
- ./ai-skill-lib/cross-tech-stack-spec-skill/SKILL.md

要求：
- 严格按代码事实输出
- 区分已闭环、部分闭环、线索级
- 以 create_codemap、build_domain_map、crate_router_map、service_deep_dive 作为核心分析动作
```

这种方式下，`create_codemap`、`service_deep_dive`、`crate_router_map`、`build_domain_map` 是工作流意图，不是 `/create-codemap` 形式的原生命令。

### 3.2 原生技能目录：`.claude/skills/`

如果希望 Claude Code 按技能目录发现并使用这套能力，可以把两个技能目录复制到目标项目：

```text
<目标项目>/
  .claude/
    skills/
      backend-service-spec-skill/
        SKILL.md
      cross-tech-stack-spec-skill/
        SKILL.md
```

使用示例：

```text
/backend-service-spec-skill create_codemap: mode=service_landscape, scope=当前项目, goal=生成服务总图
```

```text
/cross-tech-stack-spec-skill 梳理登录链路，要求覆盖页面、后端、消息、callback 边界
```

也可以直接用自然语言请求，Claude Code 会根据 `SKILL.md` 的 `description` 自动判断是否启用对应技能。

### 3.3 可选命令化：`.claude/commands/`

如果希望用户可以输入 `/create-codemap` 这类命令，把本仓库提供的 `.claude/commands/` 复制到目标项目根目录：

```text
<目标项目>/
  .claude/
    commands/
      create-codemap.md
      service-deep-dive.md
      crate-router-map.md
      build-domain-map.md
    skills/
      backend-service-spec-skill/
        SKILL.md
      cross-tech-stack-spec-skill/
        SKILL.md
```

复制后可以在 Claude Code 中使用：

```text
/create-codemap mode=service_landscape scope=当前项目 goal=生成服务总图和关键链路索引
```

```text
/service-deep-dive scope=user-service goal=梳理接口、依赖、MQ 和风险热点
```

```text
/crate-router-map scope=登录链路 goal=拆分同步调用、异步消息和闭环状态
```

```text
/build-domain-map scope=订单域 goal=从已有服务事实上卷为业务域知识
```

注意：

- `.claude/commands/*.md` 是 Claude Code 的 slash command 模板，不需要 MCP Server。
- slash command 负责把用户输入转成稳定工作流；真正分析仍然依赖 `SKILL.md`、代码搜索、配置读取和必要的终端命令。
- 如果目标项目还有自定义脚本，可以在 command 模板中补充对应执行命令。
- 如果没有脚本，Claude Code 会按技能规则直接分析代码并生成 `mydocs/` 产物。

## 4. Cursor

推荐方式：

1. 把本仓库克隆到目标项目内，例如 `ai-skill-lib/`；或者把两个技能目录复制到目标项目的 `skills/` 目录。
2. 把本仓库提供的 `.cursor/rules/` 复制到目标项目根目录。
3. 在 Cursor 中打开目标项目。
4. 让 Cursor Agent 按命令意图执行，例如 `create_codemap`、`service_deep_dive`、`crate_router_map`、`build_domain_map`。

推荐目录结构：

```text
<目标项目>/
  .cursor/
    rules/
      backend-service-spec-skill.mdc
      cross-tech-stack-spec-skill.mdc
  ai-skill-lib/
    backend-service-spec-skill/
      SKILL.md
    cross-tech-stack-spec-skill/
      SKILL.md
```

也可以把技能放到：

```text
<目标项目>/
  skills/
    backend-service-spec-skill/
      SKILL.md
    cross-tech-stack-spec-skill/
      SKILL.md
```

Cursor 中可直接输入类似请求：

```text
create_codemap: mode=service_landscape, scope=当前项目, goal=先生成服务总图和关键链路索引
```

```text
service_deep_dive: scope=user-service, goal=梳理接口、依赖、MQ 和风险热点
```

```text
crate_router_map: scope=登录链路, goal=拆分同步调用、异步消息和闭环状态
```

注意：

- `.mdc` 是 Cursor 规则文件，不是原生插件、MCP tool 或 slash command。
- `create_codemap` 等名称在 Cursor 中表示“工作流意图”，由 Agent 按规则读取代码并生成产物。
- 如果目标项目提供了 `scripts/`、`bin/`、`tools/`、`package.json`、`Makefile` 等可执行入口，Cursor Agent 可以优先运行它们。
- 如果没有可执行脚本，Cursor Agent 会按规则手工搜索代码、读取配置并生成 `mydocs/` 文档。
- 跨技术栈规则只在移动端、H5、Python、混合栈或用户明确要求跨栈分析时启用。

## 5. VS Code

VS Code 通常通过 AI 扩展使用这套仓库，而不是直接原生安装技能。

推荐方式：

1. 把本仓库克隆到工作区内或旁边，例如 `ai-skill-lib/`。
2. 增加项目说明文件，例如 `docs/ai-analysis-guide.md`。
3. 在说明文件中引用两个 `SKILL.md`。
4. 如果扩展支持项目规则，再把扩展指向这些文件。

示例说明内容：

```md
项目分析与知识梳理时，优先参考：

- ./ai-skill-lib/backend-service-spec-skill/SKILL.md
- ./ai-skill-lib/cross-tech-stack-spec-skill/SKILL.md

优先规则：
- 严格按代码事实
- 显式区分闭环状态
- 先 codemap，再做链路深挖
```

## 6. 通用接入模板

如果你的 AI 开发工具不在上面的列表里，可以通过规则文件、prompt 模板、自定义指令或 docs context 接入本仓库。

最小可迁移模板：

```md
本项目分析时，使用以下仓库作为规则源：

- ./backend-service-spec-skill/SKILL.md
- ./cross-tech-stack-spec-skill/SKILL.md

核心规则：
- 严格按代码事实输出
- 区分已闭环、部分闭环、线索级
- 以 create_codemap、build_domain_map、crate_router_map、service_deep_dive 作为核心分析动作
- 如果项目涉及移动端、H5、Python、前后端混合链路、callback、task、消息链路，则启用跨技术栈扩展规则
```

## 7. 一句话总结

对外可以把这个仓库理解为：

- 在 Codex 中作为原生技能安装
- 在 Claude、Cursor、VS Code 及其他类似工具中作为规则仓库接入

## 8. 生成的 `mydocs/` 产物如何落地

技能分析完成后，不建议把 `mydocs/` 直接当成团队知识的最终落点。

建议继续阅读：

- [从 `mydocs` 到项目中央知识库](./mydocs-to-central-knowledge-repo.zh-CN.md)
- [中央知识库与 OpenSpec 协同规则](./knowledge-repo-and-openspec-collaboration.zh-CN.md)

最短操作方式：

1. 先把项目仓里的 `mydocs/` 导入中央知识库来源层
2. 再从来源层按 `mydocs/services/`、`mydocs/domains/`、`mydocs/specs/` 的结构回收稳定内容

可直接复制的两步口令：

```text
请执行 import_mydocs_to_sources：
source_repo=<项目仓路径>
source_docs=<mydocs 路径>
target_repo=<中央知识库路径>
batch=<YYYY-MM-DD-workspace-or-topic>
mode=safe
```

```text
请执行 recover_sources_to_project：
target_repo=<中央知识库路径>
batch=<YYYY-MM-DD-workspace-or-topic>
recover=services,domains,standards
mode=guided
```
