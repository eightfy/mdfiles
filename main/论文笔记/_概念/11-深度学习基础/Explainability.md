---
type: concept
aliases: [可说明性, 科学可说明性, 模型可说明性]
---

# Explainability

## 定义
模型的可说明性（Explainability）指将模型映射到已有科学领域知识的能力——给定模型 $f_\theta(x)$，能否将学到的 $\theta$（或 $\theta$ 的函数）与领域知识关联。可说明性关注模型的 **科学内容**，而可解释性关注模型的 **结构**。

## 核心要点
1. **不能独立存在**：没有已有模型/领域知识作为对照，就没有"可说明性"
2. **知识本质上是关系性的**：科学信息只有在其他信息的语境中才有意义
3. **与数据适应性（Adaptability）权衡**：可说明性需要结构约束，降低自由度
4. **科学语境中几乎永远需要可说明性**——用于验证、预测和发现

## 代表工作
- [[Interpreting-Interpretability|Interpreting "Interpretability" and Explaining "Explainability" in ML in Physics]]: 统一框架，区分可解释性与可说明性

## 相关概念
- [[Interpretability]]: 可解释性——模型结构透明度
- [[Data Adaptability]]: 数据适应性——拟合不同数据分布的能力
- [[XAI]]: 可解释 AI 的广义框架
