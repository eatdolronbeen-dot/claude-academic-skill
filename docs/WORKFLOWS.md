# Workflows

This skill provides 14 structured workflows for academic research, organized into four groups.

---

## Literature workflows

### 1. Find Papers

**When to use**: You need to discover relevant literature on a topic.

**What it does**:
- Searches arXiv, Semantic Scholar, OpenAlex, Crossref, and Unpaywall
- Ranks candidates by relevance, recency, citation influence, and open-access availability
- Returns a structured table with metadata and relevance justification

**Example prompts**:
- "Find recent papers on transformer architectures for long sequences"
- "What are the seminal works on causal inference in econometrics?"
- "Find survey papers on reinforcement learning for robotics"

### 2. Acquire or Ingest Papers

**When to use**: You have a paper URL, DOI, or PDF file.

**What it does**:
- Downloads open-access PDFs legally
- Organizes files into `papers/sources/` and `papers/metadata/`
- Extracts text using MinerU or other tools when available

**Example prompts**:
- "Download this paper: https://arxiv.org/abs/1706.03762"
- "I uploaded a PDF to papers/inbox/, please organize it"

### 3. Read and Summarize One Paper

**When to use**: You want a structured analysis of a single paper.

**What it does**:
- Generates a standardized note in `notes/papers/`
- Includes metadata, core conclusion, methods, evidence, limitations
- Explicitly separates what the paper supports from what remains unclear
- Handles figures and prompts for method extraction when applicable

**Output**: A note in `notes/papers/<paper_title>.md` following the paper note template.

### 4. Guided Review / Teach the Paper

**When to use**: You want to deeply understand a paper or review a note you've already analyzed.

**What it does** — three modes:
- **Explain mode**: Explains in layers: intuition → technical mechanism → assumptions → related work
- **Review mode**: Generates understanding-check questions. Two sub-modes:
  - Regular: 3–5 questions (factual → conceptual → transfer)
  - Socratic: Adaptive question chain, hints instead of answers, reasoning path recording
- **Transfer mode**: Helps you judge what is useful for your research vs. what is not applicable

**Output**: A review record in `notes/learning/<paper>_review.md` with reasoning path and reflection.

**Example prompts**:
- "Teach me the transformer architecture from this paper"
- "Explain the main theorem in simple terms"
- "Socratic me on this paper"
- "Help me judge what in this paper is useful for my project"

### 5. Extract Methodological Tools

**When to use**: A reusable method, framework, or protocol emerges from reading or discussion.

**What it does**:
- Identifies generalizable tools distinct from paper conclusions
- Records with source, scope, method value, and writing citation reference
- Cross-links with existing research repository files

**Output**: Entries in `notes/research/method_toolbox.md` with GB/T 7714 citation format.

---

## Research synthesis workflows

### 6. Topic Synthesis

**When to use**: You have read multiple papers on a topic and want to synthesize them.

**What it does** — three modes:
- **Basic synthesis**: Creates or updates a note in `notes/topics/` with research question, reading map, paper clusters, agreements and disagreements, methodological differences, chronology of ideas, open problems
- **Conflict mode**: Detects contradictions across papers and generates a conflict table with severity assessment
- **Research transfer mode**: Evaluates adoptability of each paper's methods

### 7. Open Question Lifecycle

**When to use**: You discover an unresolved question, modeling ambiguity, or pending decision.

**What it does**:
- Checks for duplicates in `notes/research/open_questions.md`
- Assigns unique IDs, priority levels, and linked files
- At review, proposes concrete resolution paths (simulation, literature search, audit)
- Updates source files when questions are resolved

**Output**: Tracked questions in `notes/research/open_questions.md` with status, check history, and resolution logs.

### 8. Verify Formula with Code

**When to use**: You need to check the correctness of a formula, equation, or algorithm.

**What it does**:
- Generates verification code in Python/SymPy (default) or MATLAB
- Checks numerical correctness, dimensional consistency, and edge cases
- Distinguishes formula errors from implementation issues

**Output**: Conclusions recorded in `notes/research/audit_records.md`.

---

## Audit workflows

### 9. Audit Research Content

**When to use**: You want to verify whether a note, idea, draft, formula, or code is reliable.

**What it does** — 8 audit modes:

| Mode | Scope |
|------|-------|
| Research consistency | Does it conflict with your research goals or prior conclusions? |
| Evidence quality | Separates paper-supported claims, user judgments, and transfer inferences |
| Research relevance | Keep, lower priority, or park for later |
| Writing quality | Terminology, formula numbering, citations, figure references |
| Data and units | Units, dimensions, significant figures, plausible ranges |
| Logic quality | Premise-conclusion alignment, causal claims, transitions |
| AI-trace reduction | Generic phrases, empty modifiers, boilerplate |
| Code-formula consistency | Symbols, units, reference side, naming mismatches |

**Output**: Summary judgment (pass/fail/conditional), issue table, and file update suggestions.

---

## Writing workflows

### 10. Generate Chapter Draft

**When to use**: You need to draft a thesis chapter from accumulated research notes.

**What it does**:
- Scans research repository for ready-to-assemble content
- Marks uncertain or missing sections explicitly
- Generates prose with inline citations and evidence checklists

**Output**: Draft saved to `notes/writing/<chapter>-draft.md`.

### 11. Edit Academic Content

**When to use**: You want to polish, restructure, or improve academic writing.

**What it does** — 6 editing dimensions:
- Expression polishing, logical restructuring, evidence strengthening
- Formula/symbol alignment, information density, AI-trace reduction
- Each suggestion labeled by risk level

### 12. Citation Management

**When to use**: You need to organize citations or generate a reference list.

**What it does**:
- Extracts all mentioned literature from a draft
- Retrieves pre-formatted citations from the research repository
- Produces a GB/T 7714 formatted reference list

### 13. Generate Abstract and Keywords

**When to use**: A chapter or thesis draft is nearly complete.

**What it does**:
- Generates Chinese abstract (300–500 chars) and English abstract (150–250 words)
- Generates field-specific keywords in both languages
- Consistency check against the source draft

---

## Advanced writing workflows

### 14. Cross-Chapter Consistency / Reviewer Response

**Cross-chapter consistency check**:
- Loads all chapter drafts, builds a glossary
- Checks terminology, symbol consistency, forward/backward references, narrative arc

**Reviewer response**:
- Classifies comments (Major/Minor/Wording/Question)
- Maps comments to thesis locations
- Generates a response document with proposed modifications and response text
