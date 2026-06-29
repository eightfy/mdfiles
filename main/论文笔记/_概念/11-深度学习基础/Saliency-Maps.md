---
type: concept
aliases: [显著图, Saliency Map, 梯度显著图]
---

# Saliency Maps

## 定义
显著图（Saliency Maps）通过计算模型输出对每个输入像素的梯度来为图像模型提供像素级归因。梯度幅度大表示该区域对模型预测敏感。

## 常见变体
- **Grad-CAM**：通过对中间特征图池化，改善类别特异性
- **SmoothGrad**：通过对扰动输入的平均梯度去噪
- **Class Activation Mapping (CAM)**：加权中间特征图

## 核心要点
- 表征模型**敏感性**（结构特性）而非**因果重要性**（需额外建模）
- 仅捕获线性化关系
- 基础 Vanilla 梯度往往产生噪声图

## 相关概念
- [[Post-Hoc Interpretability]]: 事后可解释性
- [[LIME]]: 局部可解释模型
