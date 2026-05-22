# MyKnowledge Skill

`myknowledge-skill` 是一个用于初始化和维护本地 Markdown / Obsidian 风格知识库的 Agent Skill。

它的核心目标不是创建一套固定分类目录，而是先初始化一个最小可用的 MyKnowledge 骨架，再让后续目录、主题总览页和导航结构根据真实材料与检索需求逐步生长。

## 它会初始化什么

默认初始化只创建以下结构：

```text
AGENTS.md
CLAUDE.md
raw/
  llm-wiki.md
wiki/
  log.md
  governance-log.md
system/
  AGENTS.md
  CLAUDE.md
  wiki-harness.md
  wiki-governance.md
```

## 直接复制给 Agent 使用

把下面这句话复制给 Agent：

```text
请你按照 https://github.com/Wcof/myknowledge-skill 这个 skill 项目初始化当前项目。
```

Agent 应该读取这个仓库里的 `SKILL.md` 和 `references/structure-template.md`，然后在当前项目里初始化 MyKnowledge 最小骨架。

如果你想更明确一点，也可以这样说：

```text
请你按照 https://github.com/Wcof/myknowledge-skill 这个 skill 项目初始化当前项目。只初始化最小 MyKnowledge 骨架，不要创建主题目录、wiki/index.md、presentation、.agents、.claude、.obsidian 或 .git。
```


## 初始化后的工作方式

初始化后，Agent 应遵循这个顺序：

1. 先读取 `AGENTS.md` 或 `CLAUDE.md`。
2. 再读取 `system/wiki-harness.md`。
3. 如果任务涉及 Raw/Wiki 晋级、主题总览页、行动项、健康检查或治理记录，再读取 `system/wiki-governance.md`。
4. 原始、未验证、上下文不完整的材料先进入 `raw/`。
5. 已提炼出判断、结论、规则、方法、口径或可复用素材的内容进入 `wiki/`。
6. 结构性变更写入 `wiki/log.md`。
7. 治理问题、健康检查和暂不处理的问题写入 `wiki/governance-log.md`。

## 关键规则

- 先解决“怎么找东西”，再决定“放在哪里”。
- 不从固定模板套分类。
- 每个 Wiki 页面必须有 `primary_entry`，可以有多个 `secondary_entries`。
- 主题目录是派生结果，不是初始化结果。
- 不为了整齐创建空目录。
- 不把 `presentation/` 或导出文件当作知识源。
- 不在 `system/` 下新增脚本，除非用户明确批准长期自动化设计。

## 适合的场景

- 初始化个人知识库骨架。
- 把原始材料沉淀为结构化 Wiki 页面。
- 维护 metadata、主题总览页、治理日志。
- 做知识库健康检查。
- 重整知识库结构，但保留检索路径。

## 不适合的场景

- 单纯写文章，不维护知识库。
- 普通代码项目开发。
- 只要一次性回答，不希望沉淀到本地知识库。
- 需要完整呈现层、PPT 生成流水线或全库可视化系统。

呈现层目前不作为默认初始化内容。如果需要 HTML、deck、PPT 或报告页生成，应先单独确认呈现规则。
