---
type: concept
aliases: [知识蒸馏, 教师-学生蒸馏, Knowledge Distillation, Student-Teacher]
---

# Knowledge Distillation

## 定义
知识蒸馏（Knowledge Distillation）或"学生-教师"方法，是通过训练一个较小的"学生" ML 模型来逼近现有"教师"模型的输出。在可解释性语境中，学生模型通常选择具有内在可解释性的结构。

## 核心要点
1. 学生模型的结构本身就是解释——例如符号蒸馏用符号回归得到解析表达式
2. 在计算速度和模型大小受限的环境中也常用，如 LHC 触发系统
3. 蒸馏后的可解释模型可用于高需求环境

## 相关概念
- [[Post-Hoc Interpretability]]: 事后可解释性
- [[Symbolic Regression]]: 符号回归
- [[Interpretability]]: 可解释性
