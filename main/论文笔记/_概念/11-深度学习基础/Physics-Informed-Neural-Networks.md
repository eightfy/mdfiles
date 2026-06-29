---
type: concept
aliases: [物理信息网络, PINN, 物理信息神经网络]
---

# Physics-Informed Neural Networks

## 定义
物理信息模型（Physics-Informed Models）是通过将已知物理结构嵌入学习过程来实现可解释性的方法。通常通过对 ML 架构或损失函数施加结构约束来实现。

## 常见类型
1. **泛化物理模型的一部分**：广义 event shapes、广义 Lund fragmentation、模块化旋转等变集合架构
2. **满足特定物理性质的通用函数逼近器**：红外/共线安全网络、洛伦兹等变网络、旋转/反射等变星系分类器
3. **特殊损失函数**：约束对称性、求解 PDE 等
4. **参数正则化**：L1 稀疏正则化、L2 参数收缩

## 核心要点
- 相比普通 ML 模型通常具有更高的可说明性，因为领域知识已注入结构
- 但仍依赖神经网络等灵活模型，不如简单参数化模型那样内在可解释
- 可能需要额外的可解释性或可说明性工具

## 相关概念
- [[Intrinsic Interpretability]]: 内在可解释性
- [[Interpretability]]: 可解释性
