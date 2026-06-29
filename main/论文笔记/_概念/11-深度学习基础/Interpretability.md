---
type: concept
aliases: [可解释性, 结构可解释性, 模型可解释性]
---

# Interpretability

## 定义
模型的可解释性（Interpretability）指理解或近似模型内部工作机制的能力——给定模型 $f_\theta(x)$，能否"读懂" $f$ 或其组成部分所代表的内容，能否近似地表征模型输出与输入/参数的关系。

## 核心要点
1. **与数据无关**：可解释性是模型结构 $f$ 及其对 $\theta$ 和 $x$ 依赖方式的特性，而非 $\theta$ 具体值或 $f_\theta(x)$ 的特性
2. **包含但不限于**机械可解释性（Mechanistic Interpretability）、模型可达性、开放性、文档化、可复现性
3. **与表达力权衡**：可解释性越高，通常表达力（Expressivity）越低
4. **主要分为内在（Intrinsic）和事后（Post-Hoc）两类方法**

## 代表工作
- [[Interpreting-Interpretability|Interpreting "Interpretability" and Explaining "Explainability" in ML in Physics]]: 统一框架，区分可解释性与可说明性

## 相关概念
- [[Explainability]]: 可说明性——将模型映射到领域知识
- [[Expressivity]]: 表达力——模型能逼近的函数空间"体积"
- [[Mechanistic Interpretability]]: 机械可解释性子方向
- [[Intrinsic Interpretability]]: 内在可解释性（by-design）
- [[Post-Hoc Interpretability]]: 事后可解释性（analysis after training）
