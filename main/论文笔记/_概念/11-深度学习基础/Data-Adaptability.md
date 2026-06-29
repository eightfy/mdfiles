---
type: concept
aliases: [数据适应性, Data Adaptability, 模型适应性]
---

# Data Adaptability

## 定义
数据适应性（Data Adaptability）是模型通过自由参数拟合不同数据分布的能力，即可调参数能覆盖的数据分布广度。

## 核心要点
1. **与表达力（Expressivity）区分**：表达力是模型设计的内在属性，数据适应性与数据和科学内容相关
2. **与可说明性权衡**：可说明性需要结构约束以限制自由度，数据适应性随约束增强而降低
3. 查找表具有无限数据适应性但零可说明性；零参数"万有理论"数据适应性为零但可说明性最大
4. 标准模型通过庞加莱对称性、局域性、幺正性约束自身，代价是其宇宙学数据适应的局限性

## 代表工作
- [[Interpreting-Interpretability|Interpreting "Interpretability" and Explaining "Explainability" in ML in Physics]]: 提出 Explainability vs. Adaptability 权衡框架

## 相关概念
- [[Explainability]]: 可说明性
- [[Expressivity]]: 表达力
