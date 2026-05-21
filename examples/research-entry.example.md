## Entry
Transformer architecture for sequence modeling

## Source
Vaswani et al., "Attention Is All You Need", NeurIPS 2017

## Content type
Paper conclusion / reusable method (self-attention mechanism)

## Core content
The transformer replaces recurrence and convolution with pure self-attention, enabling full parallelization during training while maintaining or improving model quality.

## Evidence basis
- WMT 2014 translation benchmarks
- BLEU score improvements over RNN/CNN baselines
- Training time reduction from days to hours on comparable hardware

## Applicable scope
Sequence-to-sequence tasks with sufficient training data. Less suitable for very long sequences (memory O(n²)) or low-data regimes without pre-training.

## Relation to user's research
Directly applicable to my sequence modeling project. The parallelization benefit addresses my primary bottleneck (long training times).

## Uncertainties and open points
- How to adapt for sequences longer than 10k tokens?
- Does the quadratic attention cost become prohibitive for my data size?

## Follow-up learning or experiment actions
- Survey efficient attention variants (sparse, linear, flash attention)
- Benchmark memory usage on my target sequence lengths
