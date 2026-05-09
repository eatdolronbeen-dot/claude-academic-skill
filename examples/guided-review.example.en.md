# Attention Is All You Need - Guided Review

## Corresponding paper
notes/papers/attention_is_all_you_need.md

## Review date
2024-01-15

## This round's goal
Verify understanding of self-attention mechanism and its advantages over RNNs.

## User's own understanding
The transformer replaces RNN cells with attention layers that look at all positions at once. This makes training faster because it can be parallelized.

## Questions and answers

**Q1: In your own words, what is the core innovation of the transformer?**
A: Using attention instead of recurrence to model sequences.
→ Accurate. Key distinction: no sequential dependency during training.

**Q2: What is the computational complexity advantage of self-attention over RNNs?**
A: Self-attention is O(1) per step while RNN is O(n)?
→ Partially correct direction but imprecise. Self-attention allows parallel processing of all positions, while RNNs must process sequentially. However, self-attention itself is O(n^2) per layer due to the attention matrix.

**Q3: Can you explain why positional encoding is necessary?**
A: Because the model has no recurrence or convolution, so it doesn't know the order of tokens.
→ Correct. Positional encodings inject sequence order information.

## Mastered content
- Core idea: attention replaces recurrence
- Why positional encoding is needed
- General advantage: parallelization

## Weak points and misunderstandings
- Confused complexity: thought self-attention is O(1), but it's actually O(n^2) per layer. The advantage is parallelization, not per-step complexity reduction.
- Did not mention multi-head attention's role in capturing different representation subspaces.

## Content useful for user's research
- Parallelization approach applicable to my long-sequence problem.
- Positional encoding concept useful for my custom data type.

## Content not applicable for now
- Specific BLEU scores and translation benchmarks less relevant.

## Follow-up review questions
1. How does multi-head attention differ from single self-attention? What does "different representation subspaces" mean?
2. Compare the memory usage of transformer vs RNN for a sequence of length n.

## Next actions
- Read "The Illustrated Transformer" blog post for visual intuition.
- Review matrix multiplication view of attention before next session.
