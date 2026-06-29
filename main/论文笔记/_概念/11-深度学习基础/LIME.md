---
type: concept
aliases: [LIME, Local Interpretable Model-Agnostic Explanations, 局部可解释模型]
---

# LIME

## 定义
LIME（Local Interpretable Model-Agnostic Explanations）是一种事后可解释性方法，在单个预测点 $x$ 的邻域内生成可解释的局部线性近似。LIME 扰动输入 $x$，收集模型在扰动样本上的响应，然后用加权线性回归拟合局部代理模型。

## 核心要点
- 局部近似而非全局描述（类似泰勒展开）
- 扰动方案和邻近核是用户定义的超参数，对结果有显著影响
- 属于基于蒸馏的事后方法

## 相关概念
- [[Post-Hoc Interpretability]]: 事后可解释性
- [[Shapley Value]]: Shapley 值
- [[Saliency Maps]]: 显著图
