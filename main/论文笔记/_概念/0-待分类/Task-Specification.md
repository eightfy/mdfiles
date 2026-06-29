---
type: concept
aliases: [任务规范, 任务说明, Task Spec]
---

# Task Specification

## 定义
任务规范（Task Specification）是模型设计中精确确定模型需要完成什么任务以及必须满足哪些属性的过程。在 VERaiPHY 框架中，这是可解释性和可说明性努力的前提。

## 需明确的内容
1. **下游科学应用**：模型最终要回答什么问题？什么才是真正物理意义的量？
2. **期望属性**：需要受控不确定性、压缩、分布偏移鲁棒性、物理有意义的参数？
3. **可解释性/可说明性程度**：根据应用决定所需水平
4. **隐式建模选择**：架构选择引入的归纳偏置是否与领域知识一致

## 核心要点
- 任务规范是将内在可解释性/可说明性融入模型设计的前提——必须先知道需要什么属性，才能设计进去
- 避免建模陷阱：如喷注重建中，"分类性能最大化"是中间步骤，真正目标是参数推断

## 代表工作
- [[Interpreting-Interpretability|Interpreting "Interpretability" and Explaining "Explainability" in ML in Physics]]

## 相关概念
- [[Intervention Planning]]: 干预计划
- [[Interpretability]]: 可解释性
- [[Explainability]]: 可说明性
