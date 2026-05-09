# Claude Academic Skill

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) custom skill for **Agent-Native academic research**. It transforms paper reading from a passive information-gathering activity into a structured, interactive, and self-improving workflow.

[中文介绍](#中文介绍)

---

## Why this exists

Traditional literature review is fragmented: you search, download, read, take notes, and hope you remember the insights months later. This skill replaces that with a **persistent, collaborative agent** that:

- Remembers your research context across sessions
- Diagnoses your understanding gaps through interactive review
- Tracks open questions and reminds you of them
- Audits your notes for consistency and evidence quality
- Improves its own teaching style based on your feedback

## Core features

| Feature | Description |
|---------|-------------|
| **Paper Discovery** | Searches arXiv, Semantic Scholar, OpenAlex, Crossref, and Unpaywall with relevance ranking |
| **Structured Reading** | Generates standardized paper notes separating claims, evidence, and uncertainty |
| **Layered Teaching** | Explains papers from intuition → mechanism → assumptions → related work |
| **Guided Review** | Interactive understanding checks that diagnose weak points and record them for review |
| **Research Repository** | Organizes your original research (goals, frameworks, conclusions, experiments) separately from paper content |
| **Knowledge Audit** | Three-dimension audit: consistency, evidence quality, research relevance |
| **Open Question Tracking** | Numbered issue tracker with priority, status, and automatic reminders |
| **Self-Improvement** | Feedback-driven evolution of search, summary, and teaching behavior |
| **Bilingual Support** | English and Chinese output, switchable via configuration |

## Quick start

### 1. Install the skill

```bash
# macOS / Linux
git clone https://github.com/eatdolronbeen-dot/claude-academic-skill.git \
  ~/.claude/skills/claude-academic-skill

# Windows (PowerShell)
git clone https://github.com/eatdolronbeen-dot/claude-academic-skill.git \
  "$env:USERPROFILE\.claude\skills\claude-academic-skill"
```

### 2. Create a research workspace

```bash
mkdir my-research-project && cd my-research-project
mkdir -p papers/{inbox,sources/{pdf,markdown},extracted,metadata}
mkdir -p notes/{papers,topics,learning,research}
mkdir -p memory
```

### 3. Configure your profile

Copy a template and set your language and research field:

```bash
cp ~/.claude/skills/claude-academic-skill/examples/user_profile.template.en.md memory/user_profile.md
# Edit memory/user_profile.md with your research interests
```

### 4. Start researching

Open Claude Code in your workspace and ask:

```
Find papers on [your topic]
```

## Documentation

- [Setup Guide](docs/SETUP.md) — Detailed installation and configuration
- [Workspace Layout](docs/WORKSPACE_LAYOUT.md) — Directory structure and design philosophy
- [Workflows](docs/WORKFLOWS.md) — The 9 research workflows explained
- [Customization](docs/CUSTOMIZATION.md) — Language switching, field adaptation, output style

## Project structure

```
claude-academic-skill/
├── .claude/skills/claude-academic-skill/SKILL.md   # The skill definition
├── examples/                                        # Templates and examples
│   ├── user_profile.template.{en,zh}.md
│   ├── paper-note.example.{en,zh}.md
│   ├── guided-review.example.{en,zh}.md
│   └── ...
└── docs/                                            # Documentation
    ├── SETUP.md
    ├── WORKSPACE_LAYOUT.md
    ├── WORKFLOWS.md
    └── CUSTOMIZATION.md
```

## Key design principles

1. **Evidence-grounded**: Every claim is labeled as paper-supported, user judgment, or transfer inference
2. **Traceability**: Every conclusion links back to its source paper and original PDF
3. **Separation of concerns**: Source materials (`papers/`), processed knowledge (`notes/`), and agent state (`memory/`) live in distinct layers
4. **Cross-session persistence**: The agent remembers what you have mastered and what still confuses you
5. **Self-improvement**: Feedback is classified and used to evolve the skill itself

## License

MIT — see [LICENSE](LICENSE).

---

## 中文介绍

**Claude Academic Skill** 是一个用于 Claude Code 的自定义 Skill，它将论文阅读从被动的信息收集转变为**结构化、交互式、可自我改进**的 Agent-Native 工作流。

### 核心特性

- **智能发现**：搜索 arXiv、Semantic Scholar、OpenAlex、Crossref、Unpaywall
- **结构化精读**：生成标准化论文笔记，区分 claims、evidence、uncertainty
- **分层教学**：从直观理解 → 技术机理 → 假设条件 → 相关工作的递进式讲解
- **互动共读**：通过提问诊断理解盲区，记录错题本和个性化复习路径
- **研究库管理**：将个人研究内容（目标、框架、结论、实验）与论文内容分离管理
- **三维审核**：一致性、证据质量、研究相关性审计
- **开放问题追踪**：编号制问题管理，自动提醒长期未解决问题
- **双语支持**：英文/中文输出，通过配置文件切换

### 快速开始

```bash
# 克隆 skill 到 Claude Code 的 skills 目录
git clone https://github.com/eatdolronbeen-dot/claude-academic-skill.git \
  ~/.claude/skills/claude-academic-skill

# 创建研究工作区并初始化目录结构
mkdir my-research && cd my-research
mkdir -p papers/{inbox,sources/{pdf,markdown},extracted,metadata}
mkdir -p notes/{papers,topics,learning,research}
mkdir -p memory

# 复制中文用户画像模板并配置
cp ~/.claude/skills/claude-academic-skill/examples/user_profile.template.zh.md memory/user_profile.md
# 编辑 memory/user_profile.md 填写你的研究方向
```

然后在 Claude Code 中开始你的研究：

```
Find papers on [你的研究主题]
```
