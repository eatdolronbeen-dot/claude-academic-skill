# Workspace Layout

This document explains the directory structure and the design philosophy behind it.

## Overview

```
my-research-project/
├── papers/           # Raw materials: PDFs, extractions, metadata
├── notes/            # Processed knowledge: papers, topics, learning, research, writing
└── .claude/memory/   # Agent state: user profile, reading progress, feedback
```

## Three-layer architecture

### Layer 1: `papers/` — Source materials

This layer holds everything that came from outside: downloaded papers, extracted text, search results.

- **`papers/inbox/`**: Temporary landing zone for new PDFs. Process them into the organized structure below.
- **`papers/sources/`**: Original PDFs and markdown versions of papers (from MinerU or other extraction tools).
- **`papers/extracted/`**: Raw extraction outputs, including layout JSON, images, and full text.
- **`papers/metadata/`**: Search results, DOI links, acquisition notes, and bibliographic metadata.

**Principle**: Keep originals immutable. Never edit PDFs or raw extractions directly. All analysis goes into `notes/`.

### Layer 2: `notes/` — Processed knowledge

This layer holds your thinking, analysis, and synthesis.

- **`notes/papers/`**: One structured note per paper. These are your personal analyses, not summaries of the paper itself.
- **`notes/topics/`**: Syntheses across multiple papers. A topic note answers a research question using evidence from several sources.
- **`notes/learning/`**: Records of your learning process: quizzes, guided review sessions, wrong-answer notes, concept cards, reasoning paths.
- **`notes/research/`**: Your original research content: goals, frameworks, reusable conclusions, method toolbox, experiment plans, audit records, knowledge maps, open questions.
- **`notes/writing/`**: Thesis chapter drafts, edit records, audit reports, reference lists, reviewer responses.

**Principle**: Separate paper content (`notes/papers/`) from your original research (`notes/research/`). The former records what others found; the latter records what you think and decide.

### Layer 3: `.claude/memory/` — Agent state

This layer enables the agent to remember across sessions.

- **`.claude/memory/user_profile.md`**: Who you are, what you study, how you prefer to learn.
- **`.claude/memory/reading_state.md`**: What you've read, what you're reading, what you've mastered, what needs review.
- **`.claude/memory/feedback.md`**: How the agent should improve based on your past interactions.

**Principle**: Memory is small and stable. It does not contain full paper content or long transcripts. Those stay in `papers/` and `notes/`.

### Legacy `memory/` path

The skill also supports `memory/` at the workspace root as an alternative to `.claude/memory/`. Both locations work; `.claude/memory/` is preferred for new projects.

## Why this structure?

1. **Traceability**: You can always trace a conclusion in `notes/research/` back to a paper note in `notes/papers/` and then to the original PDF in `papers/sources/`.
2. **Separation of concerns**: Source materials, processed knowledge, and agent state each have their own layer with clear rules.
3. **Privacy**: `memory/` and `notes/research/` contain your original thinking. You can keep them private while sharing `notes/papers/` or topic syntheses with collaborators.
4. **Portability**: The skill can be updated independently of your research data.
