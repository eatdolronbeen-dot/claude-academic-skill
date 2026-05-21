# Attention Is All You Need - Guided Review

## Session info
- Corresponding paper: notes/papers/attention_is_all_you_need.md
- Review date: 2024-01-15
- This round's goal: Verify understanding of self-attention mechanism and its advantages over RNNs
- Review mode: Socratic mode

## User's own understanding
The transformer replaces RNN cells with attention layers that look at all positions at once. This makes training faster because it can be parallelized.

## Questions and answers

**Q1: What problem does this paper try to solve?**
A: RNNs are too slow to train because they must process sequentially.

**Q2: What do you mean by "sequentially"? Why is it slow?**
A: Each timestep has to wait for the previous one to finish before it can start.

→ Correct. This is the inherent serial dependency of RNNs.

**Q3: How does the transformer get around this?**
A: Self-attention looks at all positions at once, no waiting.

**Q4: But what about self-attention's own complexity? I hear it's also expensive.**
A: ...O(n²)? Because each position attends to all others.

→ Correct. So the advantage is not "lower computation" but "parallelizability."

## Reasoning path
- Which question unlocked understanding: Q4 made the user realize self-attention is also expensive
- Where the user got stuck: Distinguishing parallelization advantage from computational complexity
- What hint helped: Direct hint about self-attention's own complexity

## Mastered content
- Core idea: attention replaces recurrence
- Why positional encoding is needed
- Parallelization advantage

## Weak points and misunderstandings
- Confused complexity: thought self-attention is O(1), but it's actually O(n²) per layer. The advantage is parallelization, not per-step complexity reduction.
- Did not mention multi-head attention's role in capturing different representation subspaces.

## Content useful for user's research
- Parallelization approach applicable to my long-sequence problem.
- Positional encoding concept useful for my custom data type.

## Content not applicable for now
- Specific BLEU scores and translation benchmarks less relevant.

## Reflection
- Clearest point today: Why transformer trains faster than RNN — not less computation, but parallelizable
- Most stuck point today: Relationship between self-attention complexity and parallelization
- A new insight: O(n²) per layer, but wall time is shorter due to parallelism

## Follow-up review questions
1. How does multi-head attention differ from single self-attention?
2. Compare memory usage of transformer vs RNN for a sequence of length n.

## Next actions
- Read "The Illustrated Transformer" blog post
- Consider extracting self-attention mechanism into method toolbox
