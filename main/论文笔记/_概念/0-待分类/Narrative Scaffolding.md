---
type: concept
aliases: [叙事脚手架, 叙述脚手架]
---

# Narrative Scaffolding

## 定义
Narrative Scaffolding（叙事脚手架）是一种通过结构化叙事框架来引导 LLM 推理过程的技术，利用预训练语料中叙事子分布的密集表示来诱导特定形式的推理行为。

## 核心要点
1. 利用 LLM 预训练语料中大量存在的叙事文本作为"锚点"
2. 五段叙事结构（主角→利益相关者→后果→不确定性→承诺）是基础框架
3. 与 CoT 的区别：CoT 是开放式的逐步推理，叙事脚手架提供固定的结构槽位
4. 假设：叙事子分布中的密集表示能让模型"amortise"因果轨迹推理

## 代表工作
- [[NoT]]: 提出叙事脚手架，将其应用于道德困境推理

## 相关概念
- [[Chain-of-Thought]]
- [[Defeasible Reasoning]]
- [[Prompt Engineering]]
