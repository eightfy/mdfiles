---
type: concept
aliases: [多智能体辩论, 多方辩论, 智能体辩论]
---

# Multi-Agent Debate

## 定义
Multi-Agent Debate（多智能体辩论）是一种让多个 LLM 智能体从不同立场观点进行辩论，最终达成共识或产生综合决策的方法。

## 核心要点
1. 每个智能体扮演特定角色（如正式决策者、受影响方、第三方）
2. 通过多轮辩论（Round 0-4）逐步收敛到综合方案
3. 调解员角色负责整合各方的修改意见
4. 最终通过二元投票（接受/拒绝）产生决策

## 代表工作
- [[NoT]]: 在实验2中将 NoT 扩展到三方辩论方案，实现 6%→95% 的共识提升

## 相关概念
- [[Defeasible Reasoning]]
- [[Narrative Scaffolding]]
- [[Stakeholder Analysis]]
