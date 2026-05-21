# Customization Guide

## Language Switching

The skill supports English (`en`) and Chinese (`zh`) output.

### Set your language

Edit `.claude/memory/user_profile.md`:

```markdown
## Preferences
- Language: en   # or zh
```

The skill will read this at the start of each session and use the corresponding templates for all generated notes, headings, and review records.

### What changes with language?

- Section headings in paper notes
- Guided review record structure
- Research repository entry headings
- Session startup notifications
- Audit dimension labels

Paper titles are always kept in their original language unless you explicitly ask for a translation.

## Adapting for Different Fields

This skill is field-agnostic. To adapt it for your domain:

1. **Set your research focus** in `.claude/memory/user_profile.md`:
   ```markdown
   ## Research interests
   - Field: Computer Science
   - Subfield: Natural Language Processing
   - Current project: Low-resource machine translation
   ```

2. **Define your error framework** (if applicable) in `notes/research/error_framework.md`. For example:
   - Robotics: geometric errors, dynamic errors, compliance errors
   - Machine Learning: data bias, model bias, evaluation bias
   - Biology: measurement errors, sampling errors, confounding variables

3. **Customize the audit dimensions** by extending the audit workflow section in a local project `SKILL.md` if needed.

## Output Style Preferences

Control the depth and format of outputs in `.claude/memory/user_profile.md`:

```markdown
## Preferences
- Language: en
- Math depth: beginner | intermediate | advanced
- Output format: structured tables and bullet points
- Explanation style: concise first, expand on request
```

The skill uses these preferences to tune explanations, summaries, and quiz difficulty.

## Code Verification Language

The formula verification workflow defaults to Python/SymPy. If your field uses a different toolchain (MATLAB, Julia, R), set it in your user profile:

```markdown
## Preferences
- Default code verification: MATLAB
```

## Customizing Research Filenames

If you prefer Chinese or other-language filenames for your research repository, add a mapping section to your `user_profile.md`. The skill will use these when creating and referencing files.

## Extending the Skill

If you need additional workflows, you can:

1. Propose changes to `SKILL.md` through the self-improvement loop (record feedback in `.claude/memory/feedback.md`)
2. Fork this repository and modify the skill for your specific needs
3. Submit pull requests for improvements that benefit the broader community
