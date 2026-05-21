# Attention Is All You Need

## Metadata
- Authors: Vaswani et al.
- Year: 2017
- Venue: NeurIPS
- DOI / arXiv / URL: https://arxiv.org/abs/1706.03762
- Local file: papers/sources/attention_is_all_you_need.pdf
- Reading status: reviewed

## User goal
Understand the transformer architecture for potential application in my sequence modeling project.

## Core conclusion
The transformer architecture achieves state-of-the-art machine translation results using only attention mechanisms, eliminating the need for recurrence and convolution entirely.

## Problem and motivation
RNN-based sequence models are slow to train because they process sequentially. The authors ask: can we build a model that captures long-range dependencies without sequential processing?

## Main contributions
1. Proposed the transformer architecture based solely on self-attention.
2. Demonstrated that attention alone can match or exceed RNN/CNN performance.
3. Introduced multi-head attention and positional encoding.

## Methods
- Self-attention mechanism with scaled dot-product attention.
- Multi-head attention to jointly attend to information from different representation subspaces.
- Positional encodings to inject sequence order information.

## Evidence and experiments
- WMT 2014 English-to-German and English-to-French translation tasks.
- BLEU scores: 28.4 EN-DE (state of the art at the time), 41.8 EN-FR.
- Training time significantly reduced compared to RNN baselines.

## Key results
- Self-attention allows parallelization, reducing training time from days to hours.
- The model generalizes well to other tasks (later confirmed by BERT, GPT).

## Limitations and assumptions
- Quadratic complexity in sequence length (O(n²) attention).
- Requires large amounts of training data.
- Positional encoding is fixed, not learned (in the original paper).

## Important concepts
- Self-attention: relating different positions of a single sequence.
- Multi-head attention: running attention multiple times in parallel.
- Positional encoding: sinusoidal functions added to input embeddings.

## Relation to user's research
Directly relevant to my sequence modeling project. The parallelization benefit is especially important for long sequences.

## Discussion questions
1. How does the transformer handle very long sequences efficiently?
2. Can the attention mechanism be adapted for non-sequential data (e.g., graphs)?

## Source-grounded notes
- "The dominant sequence transduction models are based on complex recurrent or convolutional neural networks..." (Introduction)
- "Transformer is the first transduction model based entirely on self-attention..." (Abstract)

> **Note**: This paper contains a reusable methodological tool — the self-attention mechanism itself. Consider whether to extract it into the method toolbox (`notes/research/method_toolbox.md`) for future writing reference.
