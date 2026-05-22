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

默认不会创建：

```text
wiki/index.md
wiki/01、产品PM/
wiki/02、工作任务/
presentation/
.agents/
.claude/
.obsidian/
.git/
```

这些目录和导航页应由后续真实内容、检索入口和治理规则推导出来。

## 最简单的使用方式

如果你的 Agent 可以读取 GitHub 仓库，可以直接把下面这段话发给 Agent：

```text
请你按照 https://github.com/Wcof/myknowledge-skill 这个 skill 项目初始化当前项目。

要求：
1. 先读取该仓库的 SKILL.md。
2. 再读取 references/structure-template.md。
3. 只创建 raw、wiki、system 三个目录，以及 AGENTS.md、CLAUDE.md、system/AGENTS.md、system/CLAUDE.md、system/wiki-harness.md、system/wiki-governance.md、wiki/log.md、wiki/governance-log.md、raw/llm-wiki.md。
4. 不要创建 wiki/index.md、主题目录、presentation 目录、.agents、.claude、.obsidian 或 .git。
5. 初始化完成后，后续整理知识库时必须先读取 system/wiki-harness.md。
```

## 安装到 Codex Skills

如果你希望 Agent 自动识别这个 skill，可以把仓库复制到本地 skills 目录。

```bash
mkdir -p ~/.codex/skills
git clone git@github.com:Wcof/myknowledge-skill.git ~/.codex/skills/myknowledge-skill
```

之后可以这样对 Agent 说：

```text
使用 $myknowledge-skill 初始化当前目录为 MyKnowledge 风格知识库。
```

或者：

```text
使用 $myknowledge-skill 整理这段原始会议记录：……
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
