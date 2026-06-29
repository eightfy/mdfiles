---
type: concept
aliases: [事后可解释性, Post-hoc 可解释性, 模型事后分析]
---

# Post-Hoc Interpretability

## 定义
事后可解释性（Post-Hoc Interpretability）指在模型训练完成后，通过分析技术对已有模型 $f_\theta$ 进行解释的方法。

## 分类

### 基于度量的方法
- **[[Shapley Value|Shapley 值]]**：从合作博弈论借用的特征重要性度量
- **[[Saliency Maps|显著图]]**：输出对输入像素的梯度，用于图像模型
- **[[LIME]]**：在单点邻域内生成可解释的局部线性近似

### 基于蒸馏的方法
- **[[Knowledge Distillation|知识蒸馏]]**：用内在可解释的小模型逼近大模型
- **[[Probings|探针分析]]**：从网络内部表示中预测目标属性

## 核心要点
- 通常是模型无关的（model-agnostic），即插即用
- 输出结果需谨慎解读，应结合预先制定的干预计划避免确认偏误
- 目前没有已知策略能直接实现可说明性而不先实现可解释性

## 相关概念
- [[Intrinsic Interpretability]]: 内在可解释性
- [[Interpretability]]: 可解释性
