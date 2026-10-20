# AI 科研工作流

一个面向 Codex 的综合性科研 Skill。它把“选题 → 检索 → 文献核验 → Zotero → Obsidian → 实验与绘图 → 论文写作 → 汇报与追踪”组织成可复用的阶段链。

它解决的是工具选择和流程衔接问题：用户只需说“按 AI 科研工作流处理这篇论文”，协调器会根据当前任务选择相应的下游 Skill，并把上一阶段的产物交给下一阶段。

## 适用任务

- 从研究方向拆解研究问题和检索策略
- 查找、筛选、比较和核验论文
- 将真实文献整理进 Zotero 和 Obsidian
- 设计实验、分析结果、制作科研图
- 按自然科学、机器学习、系统或社科方向组织论文
- 将论文转为组会汇报、课程 PPT 或 HTML 幻灯片
- 建立每日或每周文献追踪

## 安装

### Codex

把本文件夹复制到：

```text
%USERPROFILE%\.codex\skills\ai-research-workflow
```

重启 Codex 或重新打开对话后，直接输入：

```text
请按 AI 科研工作流处理：我的研究主题是……
```

也可以直接说“论文工作流”“从文献到论文”“从论文到 PPT”等等效表达。

### 依赖

本仓库只分发协调器和阶段路由，不重新打包下游 Skill。使用前请安装或准备任务需要的依赖，最小集合如下：

```text
academic-research-suite   选题、研究设计、综合调研
paper-lookup              论文定位
literature-review         综述与证据综合
citation-audit            引用核查
zotero-data-fetcher       Zotero 元数据与批注读取
paper-vault               Obsidian 论文库
experimental-design       实验设计
analyze-results           结果分析
academic-plotting         科研图
paper-writing             通用论文写作
deai-academic-writing     中文学术表达定稿
paper-talk                汇报故事线
paper-slides              学术幻灯片
```

Zotero 和 Obsidian 还需要对应的 MCP/连接器；Skill 路由本身不会自动获得本地库权限。

## 使用方法

### 1. 文献综述

```text
请按 AI 科研工作流做一篇关于“人机交互中的生成式 AI 反馈”的文献综述。
要求：先给中英文检索式，再查找真实论文，核验 DOI，整理证据矩阵，最后给出研究空白。
```

主要链路：

```text
academic-research-suite
→ brainstorming-research-ideas（需要扩展方向时）
→ nature-academic-search
→ paper-lookup
→ literature-review
→ compare-papers / novelty-check
→ citation-audit
```

### 2. Zotero 到 Obsidian

```text
请读取 Zotero 中“人机交互”集合的 5 篇论文，先核对元数据和 PDF，
再为每篇建立 Obsidian 阅读笔记，保留 DOI、研究问题、方法、数据、结论、局限和可引用证据。
```

主要链路：

```text
zotero-data-fetcher
→ zotero-fulltext-archiver（有可访问 PDF 时）
→ zotero-analytical-writer
→ research-vault-ingest-orchestrator（明确要求入库时）
```

### 3. 论文写作

```text
请根据已有实验结果搭建论文结构，按机器学习论文规范写作，
核对所有实验数字和引用，最后对中文正文做去 AI 腔定稿。
```

主要链路：

```text
paper-plan
→ ml-paper-writing（按学科替换）
→ paper-claim-audit
→ citation-audit
→ deai-academic-writing
```

`deai-academic-writing` 会读取并应用两个上游文字编辑 Skill：`humanizer` 和 `humanizer-zh`。它们只负责表达层检查，不能改变事实、引用、数字和结论。

### 4. 论文转汇报

```text
请把这篇论文做成 15 分钟中文组会汇报，保留真实图表和来源，
给出逐页结构、讲稿、演示链接和最终 PPTX。
```

主要链路：

```text
paper-talk
→ paper-slides 或 nature-paper2ppt
→ frontend-slides（HTML）/ html-to-pptx（转换）
→ 链接、图源、字号和渲染检查
```

## 阶段速查

完整的中文 Skill 用法、触发条件、分支和不可用项目见：

[references/phase-routing.md](references/phase-routing.md)

简化判断如下：

| 任务阶段 | 重点 Skill | 产物 |
|---|---|---|
| 选题与检索策略 | `academic-research-suite`、`brainstorming-research-ideas`、`nature-academic-search` | 研究问题、检索式、筛选标准 |
| 找论文与综述 | `paper-lookup`、`literature-review`、`compare-papers`、`novelty-check` | 已核验论文、证据矩阵、研究空白 |
| Zotero 与 Obsidian | `zotero-data-fetcher`、`zotero-analytical-writer`、`paper-vault` | 条目、全文、阅读笔记、索引 |
| 实验与绘图 | `experimental-design`、`analyze-results`、`academic-plotting`、`figure-qa` | 实验方案、分析结果、科研图 |
| 论文写作 | `paper-plan`、学科写作 Skill、`citation-audit`、`deai-academic-writing` | 有证据支撑的论文正文 |
| 汇报与 PPT | `paper-talk`、`paper-slides`、`nature-paper2ppt`、`html-to-pptx` | 故事线、讲稿、PPTX 或 HTML |
| 文献追踪 | `daily-literature-digest` | 带来源的日报或周报 |

## 重要边界

- AI 检索结果只是候选线索；标题、作者、年份、DOI、方法和结论回到原文核对。
- 不生成虚构论文、DOI、数字、引文、实验结果或数据。
- Zotero/Obsidian 写入前确认连接和权限，写入后读回检查。
- 数据图必须来自真实数据或可复现代码；概念图需要明确标注为示意图。
- `cnki-search`、`wanfang-search`、`pubmed-search` 等截图中的数据库名称不代表本仓库已经包含这些原版 Skill。
- 本仓库的“自动调用”是协调规则，不是运行时插件钩子；最终应报告实际执行的 Skill。

## 目录

```text
SKILL.md                       Codex 入口指令
references/phase-routing.md   中文阶段路由与 Skill 速查
README.md                     安装、示例和边界
THIRD_PARTY_NOTICES.md        引用项目、作者与版权边界
LICENSE                       本仓库许可证
```

