---
type: concept
aliases: [符号回归, Symbolic Regression, 符号拟合]
---

# Symbolic Regression

## 定义
符号回归（Symbolic Regression）是用符号表达式近似数据或更大模型的过程。它包括普通的参数化拟合（预先指定函数形式或函数形式族），以及更通用的自动搜索符号表达式的方法。

## 核心要点
1. 通常具有预定义的数学运算符号集和表达式复杂度概念
2. 可解释性与表达力的权衡可通过复杂度惩罚项控制
3. **常用工具**：PySR
4. 普通参数化拟合可视为严格复杂度预算下的符号回归
5. 在事后可解释性中用于**符号蒸馏（Symbolic Distillation）**——用符号回归找到的解析表达式作为"学生"模型

## 相关概念
- [[Intrinsic Interpretability]]: 内在可解释性
- [[Post-Hoc Interpretability]]: 事后可解释性
- [[Knowledge Distillation]]: 知识蒸馏
