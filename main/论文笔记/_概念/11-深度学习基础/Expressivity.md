---
type: concept
aliases: [表达力, 模型表达力, Model Expressivity]
---

# Expressivity

## 定义
模型的表达力（Expressivity）指模型能逼近的函数空间的"体积"。模型 A 比模型 B 更具表达力，如果至少每个 B 能逼近的函数，A 也能逼近。通用逼近定理保证了神经网络的高表达力。

## 核心要点
1. **与可解释性权衡**：表达力越高通常可解释性越低，反之亦然
2. 神经网络、Transformer 等架构具有高表达力，适合未知或高度复杂的函数逼近
3. 参数化拟合等简单模型表达力低但可解释性高
4. **实用原则**：选择能捕获目标特征的前提下最可解释的模型

## 代表工作
- [[Interpreting-Interpretability|Interpreting "Interpretability" and Explaining "Explainability" in ML in Physics]]: 系统讨论 Interpretability vs. Expressivity 权衡

## 相关概念
- [[Interpretability]]: 可解释性
- [[Data Adaptability]]: 数据适应性（与表达力相关但不同）
