---
type: concept
aliases: [文本梯度下降, 文本梯度, Textual Gradient Descent]
---

# TextGrad

## 定义
TextGrad (Textual-Gradient Descent) 是一种使用 LLM 作为优化器对自然语言 prompt 进行迭代优化的方法，将连续优化的概念迁移到文本空间。

## 核心要点
1. 以 LLM 作为"梯度"计算器，提供文本形式的改进建议
2. 通过迭代更新 prompt 来优化目标指标
3. 在 NoT 中被用于从手工设计的 prompt 出发进一步优化

## 代表工作
- [[NoT]]: 从 NoT 初始化 TextGrad，发现跨供应商 training judge 优于同族 judge

## 相关概念
- [[Prompt Engineering]]
- [[Inference-Time Intervention]]
