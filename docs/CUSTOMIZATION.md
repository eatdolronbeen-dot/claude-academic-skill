# Customization Guide

## Language Switching

The skill supports English (`en`) and Chinese (`zh`) output.

### Set your language

Edit `memory/user_profile.md`:

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

## Customizing Research Filenames

If you prefer non-English filenames for your research repository, map them in `memory/user_profile.md`:

```markdown
## Custom filenames
- research_goals.md: 研究问题与目标.md
- error_framework.md: 误差源框架.md
- conclusion_library.md: 论文结论库.md
- experiment_plans.md: 实验方案库.md
- audit_records.md: 审核记录.md
- knowledge_map.md: 知识地图.md
- open_questions.md: 待解决问题追踪.md
```

The skill will use these mappings when referencing files.

## Adapting for Different Fields

This skill is field-agnostic. To adapt it for your domain:

1. **Set your research focus** in `memory/user_profile.md`:
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

3. **Customize the audit dimensions** by updating the skill's audit workflow section if needed.

## Output Style Preferences

Control the depth and format of outputs in `memory/user_profile.md`:

```markdown
## Preferences
- Math depth: beginner | intermediate | advanced
- Output format: structured tables and bullet points
- Explanation style: concise first, expand on request
```

The skill uses these preferences to tune explanations, summaries, and quiz difficulty.

## Extending the Skill

If you need additional workflows, you can:

1. Propose changes to `SKILL.md` through the self-improvement loop (record feedback in `memory/feedback.md`)
2. Fork this repository and modify the skill for your specific needs
3. Submit pull requests for improvements that benefit the broader community
