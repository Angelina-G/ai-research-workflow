# AI 科研工作流：阶段与 Skill 速查

先确定任务涉及哪些阶段，再读相应 Skill 的 `SKILL.md` 并执行。下面的“基础链”在该阶段被请求且缺少现成、已核验的上游产物时执行；“按需”只在对应条件成立时执行。箭头表示先后，`+` 表示同一任务需要两项。Skill 提供方法，论文原文、数据库、数据和写入结果仍须核验。最终只报告实际读取并应用过的 Skill。

## 1. 选题与检索策略

**基础链：**明确问题用 `academic-research-suite`；要探索多个研究方向，再接 `brainstorming-research-ideas` → `idea-discovery`。开始正式检索前用 `nature-academic-search` 写出中英文概念组、字段、筛选和排除条件。

| Skill | 什么时候用；怎么用 |
|---|---|
| `academic-research-suite` | 开题、研究设计或系统综述；给出主题与边界，让它形成可回答的问题和研究路线。 |
| `brainstorming-research-ideas` | 方向尚宽时；输入学科、资源和兴趣，比较几种候选问题及验证办法。 |
| `idea-discovery` | 想从宽泛方向走到可试验的 idea；提供方向，按其发现、筛选和小规模验证流程推进。 |
| `nature-academic-search` | 准备真实检索；提供研究问题，产出数据库适配的检索式和纳排标准。 |

**苏格拉底式提问：**读取 `academic-research-suite/ars/deep-research/references/socratic_questioning_framework.md` 与 `socratic_mode_protocol.md`，用“概念、证据、假设、反例、后果”追问学生。它们是套件内参考文件，并非另一个独立安装的 Skill。

## 2. 找论文、精读与证据综合

**基础链：**找真实论文用 `paper-lookup` + `nature-academic-search`；多篇研究再接 `nature-literature-pipeline`。写综述用 `literature-review` → `compare-papers`；主张创新性时再接 `novelty-check`。引文核验用 `citation-management` → `citation-audit`，需要逐字段验真时加 `nature-ref-verifier`。

| Skill | 什么时候用；怎么用 |
|---|---|
| `paper-lookup` | 查某篇或一组论文；用标题、作者、DOI 等线索定位原始记录。 |
| `nature-literature-pipeline` | 多来源批量发现与筛选；给主题、时间窗和标准，输出有来源的候选清单。 |
| `literature-review` | 形成综述；给已核验论文，按主题和证据整理共识、分歧与局限。 |
| `compare-papers` | 比较方法或结论；给至少两篇原文，生成可回溯的对照表。 |
| `novelty-check` | 评估研究空白；给拟议贡献和最近邻论文，区分已有做法与待验证的新意。 |
| `nature-reader` | 精读、双语对照或按问题读一篇；给 PDF/原文和具体问题，保留图表、公式与出处。 |
| `nature-paper-card` | 做单篇深读卡；记录问题、方法、实验到结论的证据链与局限。 |
| `citation-management` | 整理引文与参考文献格式；提供来源记录和目标格式，统一条目。 |
| `citation-audit` | 稿件含引用时；逐项检查正文主张、引用位置和可验证来源。 |
| `nature-ref-verifier` | DOI、作者、年份、卷页可能出错时；逐字段与原始记录交叉核对。 |
| `paper-claim-audit` | 稿件写入实验数字或比较结论时；把每项数字和范围对回原始结果。 |
| `literature-downloader` | 已确认开放获取或机构授权全文时；下载并记录来源、权限和文件身份。 |
| `literature-live-session-pipeline` | 用户明确要求合法浏览器会话采集与 EndNote 整理时；遵守登录与版权边界。 |

截图里的 `cnki-search`、`wanfang-search`、`pubmed-search`、`googlescholar-search`、`cochrane-search`、`scopus-search`、`sciencedirect-search`、`wos-search` 没有核验到原版安装包。课堂或项目使用相应数据库官网与上述已安装检索 Skill，记录数据库、检索日期和筛选条件；不可声称调用了那八个原版 Skill。

## 3. Zotero 与 Obsidian 知识库

**基础链：**提取已有 Zotero 条目用 `zotero-data-fetcher`；有合法可读 PDF 才接 `zotero-fulltext-archiver`；需要中文精读笔记再接 `zotero-analytical-writer`。明确要将指定论文写入研究库时用 `research-vault-ingest-orchestrator`。写入后通过 Zotero/Obsidian 工具读回核验。

| Skill | 什么时候用；怎么用 |
|---|---|
| `zotero-data-fetcher` | 已有条目 key 或标题；提取元数据、批注与可访问证据，本身不代替精读。 |
| `zotero-fulltext-archiver` | 已有可访问 PDF；保存可追踪的全文 Markdown、图片和条目关联。 |
| `zotero-analytical-writer` | 需要精读笔记；依据真实元数据、批注与全文按 Vault 模板写分析卡。 |
| `research-vault-ingest-orchestrator` | 用户指定论文要入库；串联 Zotero 身份、全文、笔记、校验与日志。 |
| `research-vault-literature-retrieval` | 向现有 Obsidian 库提问；先查笔记，再到全文和 PDF 核实。 |
| `paper-vault` | 建论文卡片库或阅读看板；导入已筛选论文，组织主题、状态与 PDF 路径。 |
| `open-notebook` | 已部署 Open Notebook 服务时；导入资料并做带来源的问答、搜索和笔记。 |

MCP 是软件连接工具，并非 Skill。只有连接可用且得到授权时才读取或写入 Zotero/Obsidian；不能把 Skill 路由当作连接成功的证明。

## 4. 实验、数据和科研图

**基础链：**新实验用 `experimental-design` → `experiment-plan`；已有结果用 `analyze-results`，需要方法审计再接 `experiment-audit`。真实数据作图用 `academic-plotting` 或 `nature-figure`，成图后接 `figure-qa`。具体学科工具按数据类型选择。

| Skill | 什么时候用；怎么用 |
|---|---|
| `experimental-design` | 设计实验；明确假设、对照、变量、样本与测量。 |
| `experiment-plan` | 要可执行方案；把设计展开成步骤、资源、指标和停止条件。 |
| `nature-experiment-log` | 连续实验；记录日期、参数、偏差与结果来源。 |
| `analyze-results` | 已有数据或结果文件；统计与解释结果，标出不确定性。 |
| `experiment-audit` | 审查可复现性；检查数据、代码、参数和结论是否一致。 |
| `nature-data` | 写数据/代码可用性声明；核对仓库、访问条件和 FAIR 元数据；它不是通用清洗工具。 |
| `academic-plotting` | 论文架构图或数据驱动图；提供真实结果与图意，保存生成代码或出处。 |
| `nature-figure` | 科研图稿或图注；按目标期刊与数据材料制作、审查图。 |
| `figure-qa` | 图完成后；检查可读性、标注、单位、来源和数据一致性。 |
| `paper-figure` | 图要嵌入论文时；把图与正文主张、编号、图注关联。 |
| `paper-illustration` | 要概念示意图时；提供方法或结构说明，明确它是示意而非实测证据。 |
| `matlab` | 工科仿真或 MATLAB/Octave 分析；提供模型、参数和可运行脚本。 |
| `matplotlib` | Python 绘图；提供数据与期望图型，产出可复现代码。 |

## 5. 论文写作、核查与去 AI 化

**基础链：**先用 `paper-plan` 定结构，再按学科选择一种写作 Skill。通用全流程可用 `paper-writing`；自然科学用 `nature-writing`，机器学习用 `ml-paper-writing`，系统论文用 `systems-paper-writing`，社科用 `social-science-paper-writing`。稿件交付前做 `citation-audit`；有实验数字再做 `paper-claim-audit`。中文学术文字的最后一遍交给 `deai-academic-writing`。

| Skill | 什么时候用；怎么用 |
|---|---|
| `paper-plan` | 动笔前；给研究结论与目标读者，生成论证顺序和章节大纲。 |
| `paper-writing` | 从研究材料到完整论文；按其叙事、章节、编译和质检流程推进。 |
| `nature-writing` | 自然科学新稿；用证据和目标期刊规范组织章节。 |
| `ml-paper-writing` | 机器学习论文；突出 baseline、实验、消融、评估与引用。 |
| `systems-paper-writing` | 系统论文；围绕问题、系统设计、实现与性能证据写作。 |
| `social-science-paper-writing` | 社会科学论文；交代理论、研究设计、样本、论证与边界。 |
| `office-academic-skill` | Word/WPS 等办公文档；处理学术格式、图表和交付。 |
| `nature-reviewer` | 模拟同行评审；按证据、方法、表达和贡献给修改清单。 |
| `nature-response` | 收到审稿意见；逐条回应并指向实际修改位置。 |
| `nature-polishing` | 已有正文需润色、翻译或压缩；保持事实、术语和证据边界。 |
| `paper-compile` | 需要编译后的论文文件；构建并检查版面和引用。 |
| `deai-academic-writing` | 中文学术文字定稿；定位模板腔、核对证据后改写，保持原意。 |
| `humanizer` | 母 Skill 启用时必须读取；检查英文来源规则中的结构化 AI 痕迹与作者声音。 |
| `humanizer-zh` | 母 Skill 启用时必须读取；检查中文语序、语域、归因和确定程度。 |
| `autoresearch` | 用户明确要自动迭代研究且有评估目标；设置试验、检查点与人工复核。 |
| `auto-paper-improvement-loop` | 用户明确要多轮改稿且有评价标准；逐轮比较版本和证据变化。 |

母 Skill 读取的是随包附带的两个上游 `SKILL.md`；模式命中不能成为编造事实、数字或引用的理由。只修用户允许修改的文字。

## 6. 论文汇报、页面与持续追踪

**基础链：**学术汇报先用 `paper-talk` 定听众、时长和故事线；要会议演示文件再用 `paper-slides`，中文论文汇报可选 `nature-paper2ppt`。成品制作按目标格式选 HTML、PPTX 或图片页重建分支，最后检查链接、图源、字号与讲述顺序。

| Skill | 什么时候用；怎么用 |
|---|---|
| `paper-talk` | 要完整学术报告；给论文、听众与时长，形成讲述线和逐页安排。 |
| `paper-slides` | 要会议幻灯片与讲稿；从论文形成可展示的页稿、演讲备注和导出文件。 |
| `nature-paper2ppt` | 中文文献汇报或组会；输入论文与图表，整理证据、术语和 PPTX。 |
| `frontend-slides` | 要浏览器 HTML 幻灯片；制作可交互页面并检查投屏效果。 |
| `modern-ppt` | 选其现成页面模板或制作流程时；按模板生成和检查。 |
| `html-to-pptx` | 已有 HTML 课件需转 PPTX；逐页渲染、转换并核对链接与截图。 |
| `nature-image2ppt` | 图片、截图或扫描 PDF 需变可编辑 PPT；重建文字和图形对象。 |
| `knowledge-cat-ppt-skill` | 要做或评审整套演示稿；先梳理故事，再按输出格式做视觉质检。 |
| `frontend-design` | 演示包含真实交互网站时；设计并实现页面。 |
| `impeccable` | 页面已成形需视觉打磨；检查排版、间距、层级和一致性。 |
| `web-design-guidelines` | 审查网页时；按可用性和设计规则列问题并修复。 |
| `daily-literature-digest` | 需要每日/每周论文更新；给关键词、来源和时间，生成有原始链接的摘要。 |

**追踪入库链：**`daily-literature-digest` → 人工确认候选 → `zotero-data-fetcher` 核对/读取选中条目 → 对用户明确指定的论文用 `research-vault-ingest-orchestrator` 入库。自动定时运行还需可用的调度工具和用户确认频率。

## 查阅与执行约定

每次只启动本次任务涉及的阶段，但该阶段的适用链要逐项执行。若用户已经提供经核验的检索清单、实验结果或论文全文，可以从相应产物往下走，并注明跳过的上游步骤。工具或数据源不可用时标记“未运行/受限”，不能写成“已调用”。截图中的 `superpowers`、`ui-ux-pro-max-skill`、`research-radar-paper-vault` 等仓库名尚不是本机确认的同名独立 Skill；选择替代 Skill 时说明替代理由。
