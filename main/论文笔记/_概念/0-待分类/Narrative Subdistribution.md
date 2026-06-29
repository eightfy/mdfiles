---
type: concept
aliases: [叙事子分布, narrative subdistribution]
---

# Narrative Subdistribution

## 定义
叙事子分布（Narrative Subdistribution）指 LLM 预训练语料中与叙事文本对应的概率子空间。NoT 通过将模型的推理过程"锚定"到这一子分布上，使模型自发地执行叙事结构化的因果推理。

## 核心要点
1. 预训练语料包含大量叙事文本（小说、故事、报道）
2. 五段叙事结构与叙事文本的基本要素高度一致
3. 模型可以通过"填充"熟悉的叙事槽位来降低推理难度
4. 这是 NoT 的底层机制假设

## 代表工作
- [[NoT]]: 提出此概念作为 NoT 有效性的理论基础

## 相关概念
- [[Narrative Scaffolding]]
- [[Chain-of-Thought]]
