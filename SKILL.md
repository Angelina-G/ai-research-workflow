---
name: ai-research-workflow
description: Automatically coordinate the installed academic-research Skills for academic, paper, literature, thesis, experiment, scientific writing, figure, or research presentation tasks. Trigger when the user mentions AI research workflow, academic workflow, paper workflow, literature workflow, or equivalent wording; select and invoke the relevant stage Skills without requiring the user to name them individually.
---

# AI Research Workflow

Use this workflow when a task involves academic research, papers, literature, experiments, thesis writing, scientific figures, or research presentations.

## 中文速查入口

先看[阶段与 Skill 速查表](references/phase-routing.md)，再看[完整 Skill 目录](references/skill-catalog.md)：前者决定阶段链，后者索引已安装扩展、触发条件和课程中仅作参考的名称。用户已有可核验的上游成果时，从对应阶段继续；只把实际读取并应用过的 Skill 报告为“已调用”。

## Core principle

AI supports exploration, organization, drafting, coding, and presentation. The researcher owns the question, source verification, evidence judgment, data, interpretation, and final claims.

## Automatic Skill routing and execution

This Skill is an active coordinator, not a catalog. When the request matches this workflow, select the installed sub-Skills needed for the current stages and execute their instructions in sequence. The user does not need to name each sub-Skill.

### Mandatory execution protocol

For every selected sub-Skill:

1. Resolve its exact installed name and read its `SKILL.md` before doing the stage. Treat patterns such as `zotero-*` or `nature-*` as routing groups, never as literal Skill names.
2. Apply that Skill's workflow and tools to the user's actual request. Do not merely mention the Skill, summarize its description, or recreate a weaker version from memory.
3. Capture the stage artifact and pass it to the next stage: query plan, verified source list, Zotero item key, Obsidian note path, evidence matrix, data file, figure, draft section, or slide outline.
4. Re-check source traceability and completion criteria before moving to the next stage.
5. In the final response, report `已调用的 Skills` and `未调用但判断相关的 Skills` with a short reason for each skipped module.

If a selected Skill contains its own pipeline or explicit sub-Skill chain, follow that chain. If a selected Skill is unavailable, report the missing exact name and continue with the closest available Skill; never claim that an unavailable Skill ran.

### Stage gates

These are mandatory **when that stage is requested or needed for a downstream deliverable**, not a command to run every Skill on every research question. Read each named `SKILL.md` and apply it before producing that stage's artifact.

The table below names the entry gate only. For the complete multi-Skill chains, branch triggers, and installed alternatives from the course workflow, read [references/phase-routing.md](references/phase-routing.md) before selecting Skills. A requested stage is complete only after its applicable chain in that file has run; one representative Skill does not stand in for the chain.

| Activated stage | Required Skill | Completion artifact |
|---|---|---|
| Question framing or search strategy | `academic-research-suite` | research question, scope, inclusion rules, query plan |
| Live paper discovery | `paper-lookup` | candidates with checked title, authors, year, DOI or source URL |
| Claims and references in a deliverable | `citation-audit` | claim-to-source check and unresolved citation list |
| Zotero library intake or organization | `zotero-data-fetcher` plus available Zotero MCP tools | item keys, collection and metadata checks |
| Obsidian reading notes or evidence vault | `paper-vault` plus available Obsidian MCP tools | note paths linked to source identifiers |
| Experiment or data analysis | `experimental-design` then `analyze-results` when results exist | protocol, data provenance, analysis and limits |
| Research figures from data | `academic-plotting` | figure plus source data or reproducible code |
| Paper drafting or revision | relevant discipline writing Skill; default `paper-writing` | sourced draft section |
| Chinese academic prose finalization | `deai-academic-writing`, which must load both bundled `humanizer` and `humanizer-zh` upstream Skills | edited prose with unchanged facts, citations and links |
| Research presentation | `paper-talk` then `paper-slides` | talk arc, slide artifact and checked links |
| Recurring literature monitoring | `daily-literature-digest` | dated digest with verified source links |

Use the Chinese prose gate after evidence and citation review. It applies to prose in papers, reports, lecture scripts, and slides when rewriting is in scope; leave code, metadata, quoted source text, bibliographies, and English text alone unless the user requests edits. A Skill instruction is not a runtime hook: confirm actual use by reading the selected files and checking the resulting artifact. If a tool or Skill is inaccessible, say so rather than treating a route entry as execution.

- `academic-research-suite`: deep literature review, systematic review, research plan, manuscript structure, citation audit, peer review, rebuttal, and research-to-paper orchestration.
- `academic-research-suite` plus `literature-review`, `paper-lookup`, `citation-management`, `citation-audit`, `compare-papers`, and `novelty-check`: source discovery, evidence synthesis, comparison, and research-gap analysis.
- `zotero-data-fetcher`, `zotero-fulltext-archiver`, `zotero-analytical-writer`, `literature-downloader`, and `paper-vault`: verified source archival, metadata, full text, annotations, collections, and reading queues.
- `open-notebook`, `paper-vault`, `daily-literature-digest`, and `research-vault-ingest-orchestrator`: durable notes, indexes, Dataview-ready records, literature retrieval, and recurring radar workflows. Obsidian MCP tools are the execution layer for the configured vault.
- `nature-academic-search`, `nature-literature-pipeline`, `nature-writing`, `nature-figure`, `nature-statistics`, `academic-plotting`, `statistical-analysis`, `experimental-design`, and the relevant scientific-tool Skill: scientific methods, analysis, reproducible experiments, and figures.
- `ml-paper-writing`, `systems-paper-writing`, `social-science-paper-writing`, `paper-writing`, `paper-write`, `paper-plan`, `paper-compile`, and `office-academic-skill`: discipline-appropriate drafting, revision, LaTeX, DOCX, and citation-aware output.
- `paper-slides`, `paper-talk`, `modern-ppt`, `many-ppt-skills`, `frontend-slides`, and `knowledge-cat-ppt-skill`: paper-to-PPT story structure, visual hierarchy, speaking flow, and slide production.
- `documents`, `pdf`, `spreadsheets`, `presentations`, `frontend-design`, `figma`, and `imagegen`: final artifact operations when the requested deliverable needs them.

Do not invoke every installed Skill by default. Run every required Skill in each activated stage's chain; apply conditional branches only when their stated trigger is met. If several stages are requested together, run them in dependency order and preserve the evidence links between them.

### Trigger language

Activate this coordinator for phrases such as: `AI科研工作流`, `AI科研流程`, `论文工作流`, `文献管理流程`, `从文献到论文`, `从论文到PPT`, `科研自动化`, `academic research workflow`, `paper workflow`, `literature workflow`, or equivalent intent expressed in Chinese or English. A specific Skill name still takes priority when the user clearly requests only that one operation.

### Stage selection

1. Identify the requested stages: framing, search, verification, Zotero archive, Obsidian notes, evidence synthesis, experiment/data, writing, figures, presentation, or tracking.
2. Consult `references/skill-catalog.md`, select the relevant installed Skills from the routing map, and read each selected `SKILL.md` before applying it. Basic chains run when their stage is active; optional modules run only when their trigger matches.
3. Pass forward concrete artifacts: verified DOI/URL, Zotero item key, note path, data path, figure source, draft section, or slide outline.
4. Return to this coordinator after each sub-Skill and check source traceability, claim support, and the next dependency.
5. If a requested module is missing or its MCP is unavailable, continue with the closest installed module and state the limitation.

### Common automatic routes

- **文献检索与综述**: `academic-research-suite` -> `paper-lookup`/`literature-review` -> `citation-management`/`citation-audit` -> `compare-papers` or `novelty-check`.
- **Zotero 到 Obsidian**: `zotero-data-fetcher` -> `zotero-fulltext-archiver` or `paper-vault` -> Obsidian literature MCP -> `daily-literature-digest` or `research-vault-ingest-orchestrator` when a recurring index is requested.
- **论文写作**: `academic-research-suite` -> the discipline Skill (`ml-paper-writing`, `systems-paper-writing`, `social-science-paper-writing`, or `paper-writing`) -> `paper-figure`/`academic-plotting` when figures are requested -> `paper-compile` when a compiled paper is requested -> `citation-audit` -> `deai-academic-writing` for Chinese academic prose.
- **论文转 PPT**: `paper-talk` -> `paper-slides` or `modern-ppt` -> `presentations`/`frontend-slides` -> final link and visual verification.
- **实验与数据**: `experimental-design` or `experiment-plan` -> the domain analysis Skill -> `analyze-results` -> `academic-plotting` -> `paper-write` or `paper-slides`.

If a requested Skill is missing, continue with the closest installed Skill or general reasoning, state the missing capability, and avoid pretending that the missing Skill ran.

## Default route

1. **Frame the question**
   - Turn the topic into population or object, context, observable outcome, method, and time boundary.
   - Use Kimi as the first conversational entry when available. Ask for alternatives, assumptions, evidence needs, and bilingual search terms.
   - Separate facts, hypotheses, and items to verify.

2. **Build the search strategy**
   - Generate concept groups, synonyms, inclusion criteria, exclusion criteria, and database-specific query syntax.
   - Prefer the user's discipline and institution access: HIT Library, CNKI, Wanfang, PubMed, Scopus, Web of Science, ScienceDirect, Google Scholar, arXiv, and Semantic Scholar.
   - Use Elicit, Consensus, Undermind, Connected Papers, ResearchRabbit, or Litmaps for discovery and citation networks.
   - Treat AI search results as candidate leads. Verify the original paper, DOI, authors, venue, date, methods, and full text.

3. **Archive verified sources**
   - Save confirmed papers, DOI, PDF, metadata, collection, tags, and reading status in Zotero.
   - Build a reading queue and preserve the source link before asking AI to summarize or compare.
   - Use Zotero MCP or connector only with the minimum permissions needed for the task.

4. **Create durable notes**
   - Store reading notes in Obsidian using a consistent template.
   - Record: research question, one-sentence claim, method, data, main findings, limitations, useful quotation or figure, open questions, and relation to the user's project.
   - Use Dataview or an index page to summarize status, topics, keywords, and links.

5. **Make evidence artifacts**
   - Produce the smallest useful artifact for the task: evidence card, literature matrix, reading queue, concept map, comparison table, research-gap note, or experiment brief.
   - Keep claims linked to the source paper and distinguish source evidence from the researcher's inference.

6. **Choose the discipline workflow**
   - Natural science, medicine, and materials: connect real data, experiments, statistics, scientific figures, and reproducible code.
   - Computer science, AI, and machine learning: connect baseline, code, evaluation, ablation, reproduction, LaTeX, and citation checks.
   - Humanities, social science, Chinese, and interdisciplinary work: emphasize concept definition, theory, argument chain, literature review, and close reading.
   - Use MATLAB for engineering and simulation tasks, Python for analysis and reproducibility, Figma for interface and interaction, and Meshy or other 3D tools for concept modeling. Record the tool's role and verification step.

7. **Write, visualize, and present**
   - Use the paper-writing Skill that matches the discipline.
   - Use real data, real screenshots, real experiment diagrams, and reproducible code for research figures. AI-generated images serve as concept references or teaching illustrations.
   - For paper-to-PPT work: extract claims and evidence, design the story, build the visual hierarchy, add sources, then check typography, links, figures, and speaking order.

8. **Track the topic**
   - For recurring research, define topic, keywords, authors, venues, date range, and output format.
   - Use a daily or weekly digest workflow with Crossref, OpenAlex, arXiv, or discipline databases.
   - Review the radar, revise terms and sources, and archive selected papers into Zotero and Obsidian.

## Reusable output format

When the user has not specified a deliverable, propose or produce:

- Research question and scope
- Search strategy and bilingual keywords
- Candidate sources with verification status
- Zotero archive plan
- Obsidian note structure
- Evidence card or literature matrix
- Research gap and next experiment
- Writing, figure, or presentation plan
- Verification checklist

## Quality and safety checks

- Never invent papers, DOI, authors, data, results, quotations, or citations.
- State when a source, full text, database, API, or local connector is unavailable.
- Respect copyright, database access rules, personal privacy, and course or venue disclosure requirements.
- Keep an audit trail of prompts, source links, downloaded files, transformations, code, and decisions when the task may affect a paper or experiment.

## Useful project resources

When the user's research vault is available, inspect these before creating duplicates:

- `AI科研备课_Obsidian教案.md`
- `skills下载与课堂取舍.md`
- `Skill应用案例_大学生焦虑.md`
- `课堂演示库/论文笔记/00_论文笔记导览.md`
- `课堂演示库/模板/论文笔记模板.md`
