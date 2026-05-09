# Workflows

This skill provides 9 structured workflows for academic research.

## 1. Find Papers

**When to use**: You need to discover relevant literature on a topic.

**What it does**:
- Searches arXiv, Semantic Scholar, OpenAlex, Crossref, and Unpaywall
- Ranks candidates by relevance, recency, citation influence, and open-access availability
- Returns a structured table with metadata and relevance justification

**Example prompts**:
- "Find recent papers on transformer architectures for long sequences"
- "What are the seminal works on causal inference in econometrics?"
- "Find survey papers on reinforcement learning for robotics"

## 2. Acquire or Ingest Papers

**When to use**: You have a paper URL, DOI, or PDF file.

**What it does**:
- Downloads open-access PDFs legally
- Organizes files into `papers/sources/` and `papers/metadata/`
- Extracts text using MinerU or other tools when available

**Example prompts**:
- "Download this paper: https://arxiv.org/abs/1706.03762"
- "I uploaded a PDF to papers/inbox/, please organize it"

## 3. Read and Summarize One Paper

**When to use**: You want a structured analysis of a single paper.

**What it does**:
- Generates a standardized note in `notes/papers/`
- Includes metadata, core conclusion, methods, evidence, limitations
- Explicitly separates what the paper supports from what remains unclear

**Output**: A note in `notes/papers/<paper_title>.md` following the paper note template.

## 4. Teach the Paper

**When to use**: You want to deeply understand a paper's concepts.

**What it does**:
- Explains in layers: intuition → technical mechanism → assumptions → related work
- Generates understanding-check questions (3 factual, 2 conceptual, 1 transfer)
- Diagnoses misunderstandings from your answers

**Example prompts**:
- "Teach me the transformer architecture from this paper"
- "Explain the main theorem in simple terms"

## 5. Guided Review (互动共读)

**When to use**: You have already read a paper and want to verify your understanding.

**What it does**:
- Asks you to restate the core conclusion in your own words
- Checks if you can distinguish paper-supported claims from transfer inferences
- Identifies weak points and records them for future review

**Output**: A review record in `notes/learning/<paper>_review.md`.

## 6. Learn from Research Repository

**When to use**: You want to study from your existing research notes, not from raw papers.

**What it does**:
- Reads `notes/research/` and synthesizes knowledge
- Generates quizzes from weak points and unresolved distinctions
- Creates knowledge maps connecting questions, concepts, papers, and methods
- Builds writing scaffolds for proposals, literature reviews, or thesis chapters

**Example prompts**:
- "Quiz me on my research repository"
- "Create a knowledge map of my project"
- "Help me outline the methods section of my thesis"

## 7. Audit Research Content

**When to use**: You want to verify whether a note, idea, or draft is reliable.

**What it does**:
- Consistency audit: Does it conflict with your research goals or prior conclusions?
- Evidence audit: Separates paper-supported claims, user judgments, and transfer inferences
- Relevance audit: Does it serve your research focus?

**Output**: Audit results saved to `notes/research/audit_records.md`.

## 8. Topic Synthesis

**When to use**: You have read multiple papers on a topic and want to synthesize them.

**What it does**:
- Creates or updates a note in `notes/topics/`
- Identifies agreements, disagreements, and methodological differences across papers
- Recommends next papers to read

## 9. Track Open Questions

**When to use**: You discover an unresolved question during any research activity.

**What it does**:
- Checks for duplicates in `notes/research/open_questions.md`
- Assigns unique IDs, priority levels, and linked files
- Reminds you of long-standing open questions at session startup
- Updates source files when questions are resolved

**Output**: Tracked questions in `notes/research/open_questions.md` with status, check history, and resolution logs.
