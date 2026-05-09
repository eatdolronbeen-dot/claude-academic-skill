# Attention Is All You Need

## 元数据
- 作者：Vaswani 等
- 年份：2017
- 期刊/会议：NeurIPS
- DOI / arXiv / URL：https://arxiv.org/abs/1706.03762
- 本地文件：papers/sources/pdf/attention_is_all_you_need.pdf
- 阅读状态：reviewed

## 用户目标
理解 Transformer 架构，用于序列建模项目。

## 一句话核心结论
Transformer 仅使用注意力机制就达到了机器翻译的最优结果，完全消除了对循环和卷积的需求。

## 问题与动机
RNN 序列模型训练慢，因为是顺序处理的。作者提问：能否在不顺序处理的情况下捕捉长距离依赖？

## 主要贡献
1. 提出了仅基于自注意力的 Transformer 架构。
2. 证明仅靠注意力就能达到或超越 RNN/CNN 的性能。
3. 引入了多头注意力和位置编码。

## 方法
- 基于缩放点积的自注意力机制。
- 多头注意力，同时关注不同表示子空间的信息。
- 位置编码注入序列顺序信息。

## 证据与实验
- WMT 2014 英德、英法翻译任务。
- BLEU 分数：英德 28.4（当时最优），英法 41.8。
- 训练时间相比 RNN 基线大幅减少。

## 关键结果
- 自注意力支持并行化，将训练时间从数天缩短到数小时。
- 模型很好地泛化到其他任务（后被 BERT、GPT 证实）。

## 局限与假设
- 序列长度的二次复杂度（O(n^2) 注意力）。
- 需要大量训练数据。
- 位置编码是固定的，非学习的（原始论文中）。

## 重要概念
- 自注意力：关联单个序列的不同位置。
- 多头注意力：并行运行多次注意力。
- 位置编码：加到输入嵌入上的正弦函数。

## 与用户研究目标的关系
与序列建模项目直接相关。并行化优势对长序列尤为重要。

## 可讨论的问题
1. Transformer 如何高效处理非常长的序列？
2. 注意力机制能否适配非序列数据（如图）？

## 有来源依据的笔记
- "The dominant sequence transduction models are based on complex recurrent or convolutional neural networks..." (Introduction)
- "Transformer is the first transduction model based entirely on self-attention..." (Abstract)
