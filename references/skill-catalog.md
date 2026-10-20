# AI 科研工作流：完整 Skill 目录

这份目录解决两个容易混淆的问题：

1. `ai-research-workflow` 是协调器，会按任务阶段选择下游 Skill；它不会把所有 Skill 一次性运行。
2. 下面标记“本机已安装”的项目，只表示当前 Codex 环境可解析到同名 `SKILL.md`；GitHub 包只分发路由与说明，使用者仍需自行安装下游 Skill。

## 自动路由基础链

| 阶段 | Skill | 用法 |
|---|---|---|
| 选题与策略 | `academic-research-suite` | 输入研究主题、限制条件和目标产物，形成问题、范围、方法和证据计划。 |
| 方向发散 | `brainstorming-research-ideas`、`idea-discovery` | 输入学科、兴趣、资源和约束，比较候选方向并设计小规模验证。 |
| 检索策略 | `nature-academic-search` | 输入研究问题，生成中英文概念组、数据库检索式、纳排标准和筛选记录。 |
| 论文定位 | `paper-lookup` | 用标题、作者、DOI、关键词定位原始论文并核对基本信息。 |
| 文献综合 | `nature-literature-pipeline`、`literature-review` | 输入已核验论文和问题，整理主题、证据、共识、分歧与局限。 |
| 对比与空白 | `compare-papers`、`novelty-check` | 输入两篇以上论文或拟议贡献，输出方法对照、最近邻工作和待验证新意。 |
| 引文核验 | `citation-management`、`citation-audit`、`nature-ref-verifier` | 输入稿件与来源，逐项检查引用、DOI、作者、年份和主张支持关系。 |
| Zotero | `zotero-data-fetcher`、`zotero-fulltext-archiver`、`zotero-analytical-writer` | 先读条目和附件，再按模板归档全文或生成精读笔记。 |
| Obsidian | `paper-vault`、`research-vault-ingest-orchestrator`、`research-vault-literature-retrieval` | 输入论文身份和笔记模板，写入可回溯的知识卡、索引和检索结果。 |
| 实验 | `experimental-design`、`experiment-plan`、`analyze-results` | 依次输入假设、变量、数据和结果，形成方案、分析和限制说明。 |
| 科研图 | `academic-plotting`、`nature-figure`、`figure-qa` | 输入真实数据或可复现代码，生成图、图注并检查单位、来源和可读性。 |
| 论文写作 | `paper-plan`、学科写作 Skill、`citation-audit` | 输入证据卡和目标期刊，搭建结构、写作、核引和定稿。 |
| 中文定稿 | `deai-academic-writing` | 输入已核验的中文正文，只调整表达、语域和句式，不改事实、数字和引用。 |
| 汇报 | `paper-talk`、`paper-slides`、`html-to-pptx` | 输入论文、听众、时长和输出格式，生成故事线、逐页稿和可检查的演示文件。 |
| 追踪 | `daily-literature-digest` | 输入主题、关键词、来源、频率和输出格式，生成带原始链接的日报或周报。 |

## 已安装扩展：按需自动选择

### 研究管理、想法与综述

| Skill | 触发条件与用法 |
|---|---|
| `ara-research-manager` | 需要任务分解、研究状态和多阶段项目管理时调用。 |
| `ara-rigor-reviewer` | 需要从方法严谨性、证据质量和可复现性审查研究时调用。 |
| `bgpt-paper-search` | 需要补充学术搜索入口或批量候选论文时调用。 |
| `comm-lit-review` | 传播学或跨学科文献综述需要主题编码时调用。 |
| `course-paper-writing` | 课程论文需要从题目、提纲到成稿的教学式流程时调用。 |
| `creative-thinking-for-research`、`scientific-brainstorming` | 需要跨学科联想、研究问题重构或实验点子时调用。 |
| `research-pipeline`、`research-refine`、`research-refine-pipeline` | 需要把研究任务拆成可执行、可复核流水线时调用。 |
| `research-lit`、`research-lookup`、`research-review` | 分别用于资料检索、单点查询和研究综述审查。 |
| `research-paper-writing`、`research-writing-skill`、`researchwrite` | 需要通用研究写作、结构整理或长文迭代时调用。 |
| `research-grants`、`market-research-reports` | 研究计划书、基金材料或市场研究报告需要专门结构时调用。 |
| `scientific-critical-thinking` | 需要检查因果、替代解释、证据边界和推理漏洞时调用。 |

### 数据、实验、统计与复现

| Skill | 触发条件与用法 |
|---|---|
| `ablation-planner` | 机器学习实验需要设计消融变量、对照和解释路径时调用。 |
| `analytical-method-validation` | 分析方法需要验证线性、精度、鲁棒性或适用范围时调用。 |
| `exploratory-data-analysis`、`statistical-analysis` | 有数据文件，需要探索分布、异常、相关性或统计检验时调用。 |
| `experiment-audit` | 需要检查数据、代码、参数、图表和结论的一致性时调用。 |
| `experiment-bridge`、`experiment-queue` | 需要把方案接入实验执行、排队或多轮复现实验时调用。 |
| `experiment-tracking-swanlab`、`monitor-experiment` | 需要记录运行指标、比较实验和监控训练过程时调用。 |
| `run-experiment`、`codex-autoresearch` | 用户明确要求执行可重复实验或自动迭代研究时调用。 |
| `formula-derivation` | 需要推导公式、检查假设和整理符号时调用。 |
| `scientific-toolkit-skill`、`scientific-visualization`、`scientific-schematics` | 需要科学计算工具选择、可视化或机制示意图时调用。 |
| `matlab`、`matplotlib`、`academic-plotting` | 分别用于 MATLAB/Octave、Python 绘图和论文级图表设计。 |

### 论文、图表与交付物

| Skill | 触发条件与用法 |
|---|---|
| `paper-write`、`paper-writing` | 需要从材料写成论文正文时按学科和现有格式选择。 |
| `paper-figure`、`paper-illustration-image2`、`figure-description`、`figure-spec` | 需要论文图、概念图、图注或绘图规格时调用。 |
| `paper-qa`、`paper-claim-audit` | 需要按问题检查全文或把数字回对原始结果时调用。 |
| `nature-citation`、`nature-downloader`、`nature-statistics` | 需要 Nature 风格引用、合规下载或统计部分整理时调用。 |
| `nature-paper-to-patent` | 需要把论文贡献转换成专利交底书结构时调用。 |
| `paper-poster`、`paper-poster-html` | 需要学术海报或浏览器海报时调用。 |
| `ppt-agent`、`pptx`、`pptx-posters` | 需要生成、调整或检查 PPTX/海报交付物时调用。 |
| `many-ppt-skills`、`scientific-slides`、`slides-polish` | 需要选择 PPT 方法、制作科研汇报或做视觉复核时调用。 |
| `markdown-mermaid-writing` | 需要用 Markdown/Mermaid 表达流程、关系和证据链时调用。 |

### Zotero 与知识库扩展

| Skill | 触发条件与用法 |
|---|---|
| `zotero-collection-manager` | 需要批量新建集合、移动条目或按规则整理 Zotero 时调用。 |
| `pyzotero` | 需要通过 Python API 批量处理 Zotero 数据时调用。 |
| `research-vault-knowledge-maintainer` | 需要去重、修复链接、维护索引和知识库一致性时调用。 |
| `research-wiki` | 需要把研究内容整理成可导航的 Wiki 时调用。 |
| `open-notebook` | 已部署 Open Notebook 服务并需要带来源问答时调用。 |

## 课程材料中出现、当前不作为可调用 Skill 的名称

下列名称来自课程截图或上游仓库，当前环境没有核验到同名独立 `SKILL.md`，因此路由会给出替代方案，不会声称它们已经运行：

| 名称 | 当前处理 |
|---|---|
| `cnki-search`、`wanfang-search`、`pubmed-search`、`googlescholar-search` | 使用相应数据库官网，配合 `nature-academic-search` 和 `paper-lookup` 记录检索式与结果。 |
| `cochrane-search`、`scopus-search`、`sciencedirect-search`、`wos-search` | 使用学校授权数据库官网，保留检索日期、字段、筛选条件和导出记录。 |
| `research-radar-paper-vault` | 当前以 `daily-literature-digest` + `research-vault-ingest-orchestrator` 替代。 |
| `superpowers` | 当前以 `brainstorming`、`dispatching-parallel-agents` 和对应阶段 Skill 替代。 |
| `ui-ux-pro-max-skill` | 当前以 `frontend-design`、`frontend-design-pro`、`impeccable` 和 `web-design-guidelines` 替代。 |

## 课程引用的上游仓库与本机 Skill 的关系

课程材料列出的 `K-Dense-AI/scientific-agent-skills`、`Yuan1z0825/nature-skills`、`Imbad0202/academic-research-skills-codex`、`leo-lilinxiao/codex-autoresearch`、`zLanqing/codex-claude-academic-skills`、`Orchestra-Research/AI-Research-SKILLS`、`Master-cai/Research-Paper-Writing-Skills`、`fakerqwq/social-science-paper-writing-skill`、`cheneternity/Zotero-Analytical-Workflow-Skills`、`cheneternity/Research-Vault-Literature-Retrieval` 等，可能贡献本机中不同名称的 Skill。以实际安装目录中的 `SKILL.md` 为准；来源和许可证见 `THIRD_PARTY_NOTICES.md`。

