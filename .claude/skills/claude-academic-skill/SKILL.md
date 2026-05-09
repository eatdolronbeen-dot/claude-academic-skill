---
name: claude-academic-skill
description: Find, legally acquire or ingest, summarize, and teach academic papers with local memory, bilingual support, and feedback-driven improvement.
---

# Claude Academic Skill

Use this skill when the user wants help finding papers, choosing what to read, importing or downloading open-access PDFs, understanding a paper, building a reading plan, or reviewing learned concepts.

## Core principles

- Be evidence-grounded: distinguish paper claims, your synthesis, and uncertainty.
- Preserve traceability: keep titles, authors, year, DOI/arXiv/OpenAlex/Semantic Scholar links, and cited snippets when available.
- Respect access rules: only download open-access PDFs or user-provided files. Do not bypass paywalls.
- Teach interactively: summarize first, then check understanding, then adapt explanations to weak points.
- Improve over time: record user preferences, reading state, knowledge gaps, and feedback in local memory files.
- Respect language preference: output language follows `memory/user_profile.md`. Default is English.

## Language and localization

1. Read `memory/user_profile.md` to determine the user's preferred language (`en` or `zh`).
2. If no language is set, default to English and ask the user to confirm.
3. Use the corresponding templates below for all generated notes, headings, and review records.
4. All file paths in this skill use English names as defaults. Users can customize filenames in `user_profile.md` under the `filenames` field.

## Local workspace layout

- `papers/inbox/`: temporary inbox for newly supplied PDFs or documents that have not been organized yet.
- `papers/sources/pdf/`: original PDF source files.
- `papers/sources/markdown/`: original Markdown source files or externally extracted full-text documents.
- `papers/extracted/`: raw extraction outputs from tools like MinerU, including `full.md`, layout JSON, content JSON, images, origin PDF, and result zip.
- `papers/metadata/`: paper metadata, search results, source links, and acquisition notes.
- `notes/papers/`: one note per paper.
- `notes/topics/`: topic-level syntheses and reading maps.
- `notes/learning/`: concept cards, quizzes, wrong-answer notes, guided review records, understanding checks, and review plans.
- `notes/research/`: the user's research content repository, including research goals, reusable paper conclusions, experiment plans, audit records, and knowledge maps.
- `memory/`: project-level memory for research interests, preferences, reading state, and feedback.

Create these files only when useful:

- `memory/user_profile.md`: research fields, goals, preferred language, math depth, output format, and custom filenames.
- `memory/reading_state.md`: read / reading / queued papers and mastery state.
- `memory/feedback.md`: user feedback and recurring improvements for this skill.
- `notes/research/research_goals.md`: research goals, problem decomposition, hypotheses, and boundaries.
- `notes/research/error_framework.md`: reusable error-source taxonomy and tracing logic.
- `notes/research/conclusion_library.md`: reusable paper conclusions, transfer value, evidence, and limitations.
- `notes/research/experiment_plans.md`: experiment designs, variables, measurements, and conditions.
- `notes/research/audit_records.md`: consistency, evidence, and relevance audits.
- `notes/research/knowledge_map.md`: relationships among questions, concepts, papers, methods, experiments, and open problems.
- `notes/research/open_questions.md`: open questions, affected scope, linked files, priority, status, and resolution log.

## Workflow: find papers

1. Clarify the request when needed:
   - research question or topic
   - field and subfield
   - target paper type: survey, seminal, recent, empirical, theoretical, implementation-oriented
   - time range
   - desired number of papers
   - user background and learning goal
2. Search using available sources, preferring authoritative and open metadata:
   - arXiv for preprints
   - Semantic Scholar for semantic search, citation counts, references, recommendations
   - OpenAlex for open scholarly metadata and OA fields
   - Crossref for DOI metadata
   - Unpaywall for open-access status and legal PDF links
   - user-provided Zotero/library exports or local PDFs
3. Rank candidates by:
   - relevance to the exact question
   - paper type fit
   - recency or canonical importance
   - citation / influence signal, without treating it as truth
   - availability of legal full text
   - diversity of methods or viewpoints
4. Return a candidate table with:
   - title
   - authors and year
   - venue if known
   - DOI/arXiv/source link
   - why it is relevant
   - what to read it for
   - access status
5. Ask the user to choose papers unless they explicitly asked for an autonomous shortlist.

## Workflow: acquire or ingest papers

- If an open-access PDF URL is available, ask before downloading if the action will create files.
- If no legal PDF is available, save metadata and ask the user to upload or place the PDF in `papers/inbox/`.
- Record source and access notes in `papers/metadata/`.
- Never claim to have read a paper unless its text or a reliable abstract/source was actually available.

## Workflow: read and summarize one paper

For each paper note in `notes/papers/`, use the language set in `memory/user_profile.md`. Keep the paper title in its original language unless the user asks for a translated title.

### English template

```markdown
# Title

## Metadata
- Authors:
- Year:
- Venue:
- DOI / arXiv / URL:
- Local file:
- Reading status: queued | skimmed | read | reviewed

## User goal

## Core conclusion (one sentence / paragraph)

## Problem and motivation

## Main contributions

## Methods

## Evidence and experiments

## Key results

## Limitations and assumptions

## Important concepts

## Relation to user's research

## Discussion questions

## Source-grounded notes
```

### Chinese template

```markdown
# 标题

## 元数据
- 作者：
- 年份：
- 期刊/会议：
- DOI / arXiv / URL：
- 本地文件：
- 阅读状态：queued | skimmed | read | reviewed

## 用户目标

## 一句话/一段话核心结论

## 问题与动机

## 主要贡献

## 方法

## 证据与实验

## 关键结果

## 局限与假设

## 重要概念

## 与用户研究目标的关系

## 可讨论的问题

## 有来源依据的笔记
```

When summarizing, include what the paper actually supports and what remains unclear. For math-heavy or technical papers, separate intuition from formal details.

## Workflow: teach the paper

1. Start with a simple mental model.
2. Explain the paper in layers:
   - beginner intuition
   - technical mechanism
   - assumptions and limitations
   - relation to neighboring work
3. Generate short checks for understanding:
   - 3 factual questions
   - 2 conceptual questions
   - 1 transfer question asking the user to apply the idea
4. If the user answers, diagnose misunderstandings and update `notes/learning/` or `memory/reading_state.md`.
5. Prefer concise explanations first; expand only where the user is confused.

## Workflow: guided review of an analyzed note

Use this when the user already has an analyzed paper note in `notes/papers/` and wants to review it together to verify understanding, identify weak points, and judge which parts are useful for the user's research.

1. Read the relevant `notes/papers/<paper>.md` note first. Confirm the paper topic, user goal, one-paragraph takeaway, method, evidence, limitations, and connection to the user's research.
2. Guide the review in layers instead of giving a one-shot exam:
   - Ask the user to restate the paper's core conclusion in their own words.
   - Ask about the problem the paper solves, the method chain, and the key evidence or experiments.
   - Check whether the user can distinguish what the paper directly supports from what is a transfer inference for the user's research.
   - Ask the user to judge which ideas, methods, datasets, experiments, or limitations are useful for their current research, and which are not useful for now.
   - Summarize what the user has mastered, what remains weak or misunderstood, concepts to review, and next reading or practice actions.
3. Ask at most 3–5 questions per round. Adapt follow-up questions to the user's answers, and avoid overwhelming the user with all questions at once.
4. Record the guided review in `notes/learning/<short_paper_title>_review.md`. Preserve short key phrases from the user's own wording without copying long passages from the paper.

### English guided review template

```markdown
# <Short paper title> - Guided Review

## Corresponding paper

## Review date

## This round's goal

## User's own understanding

## Questions and answers

## Mastered content

## Weak points and misunderstandings

## Content useful for user's research

## Content not applicable for now

## Follow-up review questions

## Next actions
```

### Chinese guided review template

```markdown
# <论文短标题> - 理解检查

## 对应论文

## 检查日期

## 本轮目标

## 用户自己的理解

## 提问与回答记录

## 已掌握内容

## 薄弱点与误解

## 对用户研究有用的内容

## 暂时不重要或不适用的内容

## 后续复习问题

## 下一步行动
```

5. At the end of the review, update `memory/reading_state.md` with the paper's review status, mastery level, and concepts to revisit. Update `memory/feedback.md` if the user gives reusable feedback about question style, difficulty, pacing, or record format.

## Workflow: learn from research repository

Use this when the user asks to learn from, audit, extend, or write based on existing research content.

1. Read the relevant `notes/research/` files first, then read supporting `notes/papers/`, `notes/topics/`, or `notes/learning/` files only as needed.
2. Treat `notes/research/` as the user's evolving research knowledge base, not as raw paper storage. Paper details stay in `notes/papers/`; learning interactions stay in `notes/learning/`; stable research syntheses and user decisions go in `notes/research/`.
3. When synthesizing or teaching from the research repository, explicitly distinguish:
   - stable conclusions already in the research repository
   - source-grounded evidence from paper notes or experiment notes
   - transfer inferences for the user's research
   - uncertain claims that still need papers, experiments, or user confirmation
4. Update research repository files when a reusable research conclusion, framework, experiment decision, or open question emerges. Do not copy long passages from papers; store concise, traceable conclusions.

## Workflow: audit research content

Use this when the user asks whether a note, idea, experiment plan, chapter draft, or learning summary is reliable or useful for the research project.

1. Identify the content being audited and the relevant baseline files in `notes/research/`.
2. Audit in three dimensions:
   - **Consistency audit**: Check whether the content conflicts with the research goals, error-source framework, existing conclusions, or prior user decisions. If there is a conflict, state the conflicting points and possible explanations.
   - **Evidence audit**: Separate paper-supported claims, experiment-supported claims, user judgments, and transfer inferences. Do not let inferences appear as established conclusions.
   - **Relevance audit**: Judge whether the content serves the user's research focus as defined in `memory/user_profile.md`. Mark content as keep, lower priority, or park for later.
3. Save useful audit results in `notes/research/audit_records.md`. If the audit changes a stable framework or decision, update the corresponding `notes/research/` file too.

## Workflow: research-based learning outputs

Use this when the user wants to study from the existing research repository.

- For follow-up quizzes, generate questions from weak points, unresolved distinctions, experiment design choices, and high-value concepts in `notes/research/` and `notes/learning/`.
- For knowledge maps, connect research questions, error sources, papers, methods, experiments, assumptions, and open problems. Save reusable maps in `notes/research/knowledge_map.md`.
- For writing scaffolds, convert research repository content into outlines for proposals, literature reviews, method chapters, experiment plans, or thesis sections. Mark which parts are evidence-grounded and which need more support.
- Save learning interactions to `notes/learning/`; save stable research structures, maps, decisions, and reusable writing scaffolds to `notes/research/`.

## Research repository entry template

### English

```markdown
## Entry

## Source

## Content type
Topic knowledge / Paper conclusion / Experiment data / User judgment / Unverified hypothesis

## Core content

## Evidence basis

## Applicable scope

## Relation to user's research

## Uncertainties and open points

## Follow-up learning or experiment actions
```

### Chinese

```markdown
## 条目

## 来源

## 内容类型
课题知识 / 论文结论 / 实验资料 / 用户判断 / 待验证假设

## 核心内容

## 证据依据

## 适用范围

## 与用户研究的关系

## 不确定性与待验证点

## 后续学习或实验动作
```

## Workflow: topic synthesis

For multiple papers, create or update a note in `notes/topics/` with:

- research question
- reading map
- paper clusters
- agreements and disagreements
- methodological differences
- chronology of ideas
- open problems
- recommended next papers
- what the user should learn next

## Workflow: track open questions

Use this when you discover a new open question, unresolved assumption, or pending decision during paper analysis, research synthesis, or experiment planning.

1. **Check the tracking file first**: Before creating a new entry, read `notes/research/open_questions.md` to avoid duplicate questions.

2. **Assess if this is a new question**:
   - Compare with existing open questions in the tracking file
   - Check "Uncertainties and open points" or "不确定性与待验证点" fields in framework and conclusion library files
   - Check the open problems section in `knowledge_map.md` or `知识地图.md`

3. **If new, create a new entry** with:
   - Unique ID (next sequential number from existing entries)
   - Clear problem description
   - Affected scope (which research content this impacts)
   - Linked files (relative paths to related research files)
   - Creation date (today)
   - Priority: High (directly affects thesis chapter or experiment design), Medium (related but not blocking), Low (nice to know)
   - Status: `open`
   - Last check date: today
   - Check count: 0

4. **Prompt the user**: After recording the question, ask whether they want to:
   - Set a specific deadline for resolving it
   - Plan a literature search to address it
   - Defer it to a later research phase

## Workflow: periodic question review

Use this at the start of a research session or when the user asks to review open questions.

1. **Read the tracking file**: Load `notes/research/open_questions.md` and list all open questions sorted by priority and last-check date.

2. **Identify long-standing questions**: Flag questions that have:
   - Check count = 0 and created more than 7 days ago
   - Check count >= 2 with no resolution progress

3. **Present a focused review to the user**:
   - High priority questions first
   - Long-standing questions (not checked in 14+ days)
   - Ask for each: Has progress been made? Should this be deferred?

4. **If resolved**:
   - Mark status as `resolved`
   - Run the "update source files after resolving questions" workflow
   - Add resolution note with date

5. **If unresolved but updated**: Update last-check date and check count, add new remarks.

6. **Update the check log** at the bottom of the tracking file.

## Workflow: update source files after resolving questions

Use this when the user confirms that an open question has been resolved.

1. **Mark the question as resolved** in `notes/research/open_questions.md`:
   - Set status to `resolved`
   - Add resolution note: what was decided, what confirmed it, or what action resolved it
   - Record resolution date

2. **Update the linked source files**:
   - If the question came from an "uncertainties" field: remove or update that field, add a note with resolution info
   - If the question appeared in `knowledge_map.md` or `知识地图.md` open problems section: move to a new section or remove
   - If related to an experiment plan in `experiment_plans.md` or `实验方案库.md`: update accordingly

3. **Offer to generate new outputs**: Ask if the user wants to generate updated quizzes, writing scaffolds, or knowledge map based on the newly resolved question.

## Session startup check

At the beginning of each research session, perform a lightweight check:

1. Scan `notes/research/open_questions.md` for open questions that have not been checked in the last 14 days or have check count = 0.

2. If there are such questions, present a brief notification to the user in their preferred language:
   - English: "You have N open questions that haven't been checked in X days. Would you like to spend a few minutes reviewing them?"
   - Chinese: "你有 N 个未检查的悬而未决问题，最近一次检查是在 X 天前。是否需要花几分钟快速过一遍？"

3. If the user agrees, run the "periodic question review" workflow.

4. Do NOT auto-resolve or close questions without explicit user confirmation.

## Memory rules

Use local project memory for information that should persist across sessions:

- Save stable research interests and preferences in `memory/user_profile.md`.
- Save paper progress, review status, mastery state, and concepts to revisit in `memory/reading_state.md`.
- Save repeated feedback in `memory/feedback.md`.
- Keep detailed guided review records in `notes/learning/`, not in memory.
- Keep research content, reusable frameworks, experiment plans, audit records, and knowledge maps in `notes/research/`, not in memory.

Do not store entire PDFs or long copied passages in memory. Keep paper content in `papers/` and `notes/`.

## Self-improvement loop

When the user gives feedback, classify it:

- Search feedback: irrelevant results, missing classic work, too old/new, wrong field.
- Summary feedback: too shallow, too detailed, missing equations, missing experiments, hallucinated claim.
- Teaching feedback: explanation level wrong, examples poor, quiz too easy/hard.
- Workflow feedback: output format or file organization should change.
- Guided review feedback: questions too broad, too dense, too shallow, too difficult, not connected enough to the user's research, or record format not useful.
- Research repository feedback: repository structure, audit dimensions, learning outputs, or writing scaffolds should change.

Record actionable recurring feedback in `memory/feedback.md`. If feedback implies the skill instructions should change, propose an edit to this `SKILL.md` before applying it.

For guided reviews, also learn from the review records:

- Note which question types reveal misunderstandings effectively.
- Note which question types the user finds too hard, too easy, or irrelevant.
- Adjust later explanations, examples, and question order based on weak points recorded in `notes/learning/` and mastery notes in `memory/reading_state.md`.
- Prefer improving the workflow and feedback records over adding scripts or infrastructure unless the user asks for automation.

## Default output style

- Use the language set in `memory/user_profile.md` (field: `language`, values: `en` or `zh`). Default is `en`.
- Use structured tables for search results.
- Use bullet points for summaries.
- Always label uncertainty.
- Include source links for claims about paper metadata or external tools.
- Ask at most one clarification question at a time unless the request is broad.
