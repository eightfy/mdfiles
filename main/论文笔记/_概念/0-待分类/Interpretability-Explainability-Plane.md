---
type: concept
aliases: [Interpretability-Explainability 平面, I-E 平面, IE平面]
---

# Interpretability-Explainability Plane

## 定义
Interpretability-Explainability 平面是 Gambhir、Lucie-Smith 和 Thaler 在 2026 年提出的概念框架，将模型置于以可解释性（结构透明度）为横轴、可说明性（领域知识映射）为纵轴的二维空间中，分四个象限分类。

## 四个象限

| 象限 | 类型 | 示例 |
|------|------|------|
| 高可解释 + 高可说明 | 经典物理模型 | 牛顿力学、标准模型、广义相对论、浅层决策树 |
| 高可解释 + 低可说明 | 理解结构但不能映射到物理 | CNN 激活模式的可视化检查 |
| 低可解释 + 高可说明 | 科学原理清楚但机制不透明 | 数学超越函数 $e^x$、10-loop QCD 预测 |
| 低可解释 + 低可说明 | 科学中价值存疑 | 闭源商业 LLMs |

## 核心要点
1. 所有科学目标都需要一定程度的可解释性和可说明性——图左下角是"禁区"
2. 科学发现需要最高的可解释性和可说明性
3. 模型替代（surrogates）需要高可说明性但可牺牲可解释性

## 代表工作
- [[Interpreting-Interpretability]]: 首次系统提出该平面框架

## 相关概念
- [[Interpretability]]: 可解释性
- [[Explainability]]: 可说明性
