---
type: concept
aliases: [Shapley 值, 沙普利值, SHAP]
---

# Shapley Value

## 定义
Shapley 值（Shapley Value）是从合作博弈论引入的特征重要性度量。对于模型 $f$ 中的特征 $i$，其 Shapley 值定义为该特征在所有可能的特征排序中的平均边际贡献：

$$
\phi_i(f) = \sum_{S \subseteq F \setminus \{i\}} \frac{|S|! (|F| - |S| - 1)!}{|F|!} \left[ f_{S \cup \{i\}}(x) - f_S(x) \right]
$$

其中 $F$ 为全部特征集，$S$ 为不包含特征 $i$ 的任意子集，$f_S$ 为仅用 $S$ 中特征评估模型。

## 核心要点
1. **实现**：SHAP 是广泛使用的数值实现框架
2. **用途**：评估 tagger、特征重要性排名、发现物理模式
3. **注意事项**：必须配合干预计划使用，避免确认偏误；需确保度量在完整分析计划中有意义
4. **定性代理**：实际中很少定量计算经典理论的 Shapley 值，但定性代理可减少定性不确定性

## 相关概念
- [[Post-Hoc Interpretability]]: 事后可解释性方法
- [[Interpretability]]: 可解释性
- [[Explainability]]: 可说明性
