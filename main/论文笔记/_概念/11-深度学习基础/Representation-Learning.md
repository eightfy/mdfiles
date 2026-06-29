---
type: concept
aliases: [表示学习, 表征学习, Representation Learning]
---

# Representation Learning

## 定义
表示学习（Representation Learning）是将高维数据映射到低维"潜空间"（latent space）的过程，旨在发现数据中隐藏的结构化信息。

## 核心要点
1. **经典方法**：PCA（主成分分析）学习线性降维，主成分正交且按方差排序
2. **深度学习方法**：推广到非线性映射，可能揭示隐藏的广义结构
3. **解纠缠表示（Disentangled Representations）**：旨在将不同独立变化因子隔离到不同潜变量维度
   - InfoGAN：最大化潜变量子集与标签间的互信息
   - β-VAE：通过重建精度与潜空间独立性的平衡促进解纠缠
   - SciNet：学到的潜参数恢复预期的物理参数
4. **关键挑战**：没有显式归纳偏置的情况下，有意义的解纠缠表示难以实现

## 相关概念
- [[Intrinsic Interpretability]]: 内在可解释性
- [[Post-Hoc Interpretability]]: 事后可解释性
