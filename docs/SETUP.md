# Setup Guide

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) installed and configured
- Git (optional, for syncing your research workspace)

## Installation

### Step 1: Clone or copy this skill

Clone this repository into your Claude Code skills directory:

```bash
# macOS / Linux
git clone https://github.com/eatdolronbeen-dot/claude-academic-skill.git \
  ~/.claude/skills/claude-academic-skill

# Windows (PowerShell)
git clone https://github.com/eatdolronbeen-dot/claude-academic-skill.git \
  "$env:USERPROFILE\.claude\skills\claude-academic-skill"
```

Or manually copy the `.claude/skills/claude-academic-skill/SKILL.md` file to your Claude Code skills directory.

### Step 2: Create a research workspace

Create a directory for your research project. This can be anywhere on your filesystem:

```bash
mkdir my-research-project
cd my-research-project
```

### Step 3: Initialize the workspace structure

Create the required directories:

```bash
mkdir -p papers/{inbox,sources/{pdf,markdown},extracted,metadata}
mkdir -p notes/{papers,topics,learning,research}
mkdir -p memory
```

### Step 4: Configure your user profile

Copy the appropriate template from `examples/` to `memory/user_profile.md` and fill in your details:

```bash
# For English
cp examples/user_profile.template.en.md memory/user_profile.md

# For Chinese
cp examples/user_profile.template.zh.md memory/user_profile.md
```

At minimum, set:
- Your research field and questions
- Language preference (`en` or `zh`)

### Step 5: Start using the skill

Open Claude Code in your research workspace and start asking for help:

```
Find papers on [your topic]
```

The skill will automatically load your profile and use your preferred language.

## Updating the skill

To update to the latest version:

```bash
cd ~/.claude/skills/claude-academic-skill
git pull
```

Your research data (`papers/`, `notes/`, `memory/`) is completely separate from the skill and will not be affected by updates.
