---
type: concept
aliases: [推理时干预, 推理时方法, 推理时脚手架]
---

# Inference-Time Intervention

## 定义
推理时干预（Inference-Time Intervention）指在 LLM 推理阶段（而非训练阶段）通过 prompt 工程、解码约束或外部脚手架修改模型行为的方法论。

## 核心要点
1. 不改变模型权重，零训练开销
2. 包括 system prompt 修改、constrained decoding、scaffolding 等多种形式
3. NoT 属于此类方法，仅通过 system prompt 约束推理结构
4. 优势：部署成本低、可热切换、无需重训练

## 代表工作
- [[NoT]]: 通过 system prompt 级别的五段叙事脚手架实现推理时干预

## 相关概念
- [[Prompt Engineering]]
- [[Narrative Scaffolding]]
