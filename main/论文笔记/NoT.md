---
title: "Narration-of-Thought: Inference-Time Scaffolding for Defeasible Ethical Reasoning in Large Language Models"
method_name: "NoT"
authors: [Patrick Cooper, Alvaro Velasquez]
year: 2026
venue: ACL 2026
tags: [ethical reasoning, chain-of-thought, LLM safety, narrative reasoning, defeasible reasoning, multi-agent debate, AI alignment]
zotero_collection: ""
image_source: local
arxiv_html: https://arxiv.org/html/2606.26366v1
created: 2026-06-27
---

# 论文笔记：Narration-of-Thought

## 元信息

| 项目 | 内容 |
|------|------|
| 机构 | University of Colorado Boulder |
| 日期 | June 2026 |
| 项目主页 | https://github.com/PatrickAllenCooper/ANI_Computational_Narratology |
| 链接 | [arXiv](https://arxiv.org/abs/2606.26366) / [Code](https://github.com/PatrickAllenCooper/ANI_Computational_Narratology) |

---

## 一句话总结

> NoT 是一个仅修改 system prompt 的推理脚手架，将 CoT 强制约束为"主角→利益相关者→后果→不确定性→承诺"五段叙事结构，在不训练/微调的前提下将伦理推理中的 stakeholder collapse 从 31% 降至 <1%，uncertainty suppression 从 72% 降至 1-24%。

---

## 核心贡献

1. **诊断两个伦理推理失败模式**: 标准 CoT 在道德困境上存在 stakeholder collapse（trace 提到 ≤1 个利益相关者）和 uncertainty suppression（trace 在承诺前无明确未知/保留）。
2. **NoT 五段叙事脚手架**: 仅作为 system prompt 约束模型按"主角→利益相关者→两步后果→不确定性→承诺"五步推理，无任何训练/微调/额外参数。
3. **跨供应商多模型验证**: 在 OpenAI/Anthropic/xAI 四模型面板上大幅降低两种失败模式，matched-budget 控制实验确认叙事结构（而非 token 数量）是有效成分。
4. **文本梯度下降优化**: 以 NoT 初始化 TextGrad，跨供应商训练 judge 优于同族 judge，提出可迁移的最佳实践。
5. **多智能体多方协商协议**: 将 NoT 扩展为三方利益相关者辩论+调解员集成+投票协议，将 6% 的僵局转化为 95% 完全共识。

---

## 问题背景

### 要解决的问题
LLM 在道德困境推理中产生两种系统性的 trace 级失败：**利益相关者坍缩**（只提及 ≤1 个利益相关的当事人）和**不确定性压制**（在承诺行动前不表达任何未知或保留）。这些失败模式与 sycophancy rollback、agentic misalignment 等部署安全问题一致。

### 现有方法的局限
- 标准 CoT 在道德推理上有 15-31% 的 stakeholder collapse 和 50-72% 的 uncertainty suppression
- 现有 prompt 工程（如角色扮演、价值观注入）缺乏对推理结构的形式化约束
- 已有的 prompt 优化方法通常需要大量标注数据或特定训练

### 本文的动机
- 利用预训练语料中密集存在的叙事结构，让模型"注册"到叙述性子分布（narrative subdistribution）
- 叙事的五个基本元素（主角、利益相关者、因果链、不确定性、承诺）恰好对应道德推理需要的认知步骤
- 零训练/微调开销，直接作为 system prompt 可部署

---

## 方法详解

### 模型架构

NoT 采用 **推理时 prompt 脚手架** 架构：

- **输入**: 道德困境文本 + 决策选项
- **Backbone**: 各供应商的前沿 LLM（[[GPT|gpt-5.4-nano]]、[[Claude|claude-haiku-4-5/sonnet-4-6]]、[[Grok|grok-4-1-fast-reasoning]]）
- **核心模块**: [[Narrative Scaffolding|叙事脚手架]] 用于 [[Defeasible Reasoning|可废止推理]]
- **输出**: 五段叙事结构化的 CoT trace + 最终决策承诺

### 核心模块

#### 模块1: NoT 五段叙事 Prompt

**设计动机**: 利用 [[Narrative Subdistribution|叙事子分布]] 中的密集表示，让模型通过填充熟悉的叙事结构来自发执行因果推理。

**具体实现**:
- 以第一人称要求模型依次完成五个部分：
  1. **主角描述**（Protagonist）：名字、角色、所知信息
  2. **利益相关者枚举**（Stakeholders）：列出所有与决策相关的人及其利害关系
  3. **两步后果投影**（Consequences）：对每个可选行动，至少预测两步后果
  4. **不确定性表达**（Uncertainty）：说明对每个预测未来的不确定之处
  5. **承诺决策**（Commitment）：在叙事框架内解释为何该轨迹优于其他方案
- 不提及因果图、效用函数或任何形式化工具
- 仅修改 system prompt 一行，零训练/零参数/零微调

#### 模块2: 多智能体多方协商协议

**设计动机**: 将 NoT 从单智能体扩展为 [[Multi-Agent Debate|多智能体辩论]]，实现决策闭环中的可废止性和可审计性。

**具体实现**:
- 三个独立 NoT 智能体分别扮演：**正式决策者**（formal decider）、**主要受影响方**（primary affected）、**第三方**（third party）
- **Round 0-2**: 闭式行动分类+开放行动空间辩论
- **Round 3**: 调解员（moderator）构建综合提案给三方
- **Round 4**: 整合三方修改意见后，进行二元接受/拒绝投票
- 调解员 4.3% 的剩余拒绝集中在那些利益被提案实质性损害的角色上

---

## 关键公式

### 公式1: 算法复杂度的 Kolmogorov 代理度量

$$
K_C(M) = \min_p \{ |p| : \forall i \in \mathcal{I},\; U(p, i) = M(i) \}
$$

**含义**: 衡量 trace 底层结构因果模型（SCM）的描述长度。

**符号说明**:
- $K_C(M)$: 模型 $M$ 的 Kolmogorov 复杂度
- $U$: 通用图灵机
- $\mathcal{I}$: 可允许干预的集合（如"设定主角信念"）
- $p$: 程序描述

### 公式2: TextGrad 连续损失

$$
\ell = \max(0,\, 4 - \mathit{sc}) + \max(0,\, 2 - \mathit{us})
$$

**含义**: 用于文本梯度下降的连续可微损失函数，目标同时优化 stakeholder count 和 uncertainty score。

**符号说明**:
- $\mathit{sc}$: stakeholder count（trace 中命名的不同利益主体数量）
- $\mathit{us}$: uncertainty score（trace 中明确的保留/未知标记数量）
- 目标值: stakeholder count ≥ 4, uncertainty score ≥ 2

---

## 关键图表

### Figure 1: One scaffold, three settings

![[NoT/x1.png]]

**说明**: NoT 的三种设置。标准 CoT（左）产生两个失败模式；单智能体 NoT（中）将 stakeholder collapse 降至 <1%，uncertainty suppression 降至 1-24%；多智能体 NoT（右）扩展为三方辩论+调解+投票，达 95% 完全共识。

### Figure 2: Trace-level instance of failure modes

![[NoT/x2.png]]

**说明**: 同一场景下标准 CoT 和 NoT 的对比。标准 CoT 的 trace stakeholder count=1（未命名）、uncertainty=0（两个失败模式均触发）；NoT trace 有 6 个 stakeholder、≥2 个 uncertainty markers（均不触发）。

### Figure 3: Failure-mode firing rates

![[NoT/x3.png]]

**说明**: 四模型面板上 NoT vs 标准 CoT 的失败模式触发率。Stakeholder collapse 从 15-31% 降至 0-1%，uncertainty suppression 从 50-72% 降至 1-24%。

### Figure 4: Sub-instruction ablation

![[NoT/x4.png]]

**说明**: claude-sonnet-4-6 上的子指令消融实验。Dropping Stakeholders 子指令使 stakeholder count 下降 δ=-0.41，Dropping Uncertainty 使 uncertainty score 下降 δ=-0.17，确认每段子指令携带其目标指标。

### Figure 5: Consensus rates across debate designs

![[NoT/x5.png]]

**说明**: 逐步结构化的辩论协议。闭式分类（6% 完全共识）→ 开放行动空间（9%）→ 调解员综合提案+展示（100% 部分收敛）→ 综合提案+二元投票（95% 完全共识）。

### Figure 6: Length-residualised effect sizes

![[NoT/x6.png]]

**说明**: NoT vs 标准 CoT 的 Cliff's δ 效应量。OpenAI/xAI 模型在去除输出长度影响后仍保留大效应量；Anthropic 模型的变化主要由长度中介。

### Table 1: Cell sizes and percentage-point drops

| Generator | N_S | N_N | Δ_SC | Δ_US |
|-----------|-----|-----|------|------|
| gpt-5.4-nano (OpenAI, b) | 1,989 | 1,985 | -30 | -72 |
| claude-haiku-4-5 (Anth., b) | 1,999 | 1,996 | -25 | -29 |
| grok-4-1-fast-r. (xAI, b) | 515 | 515 | -13 | -44 |
| claude-sonnet-4-6 (Anth., f) | 500 | 500 | -26 | -37 |

**说明**: 每个生成器的编码样本量和两种失败模式的百分点下降。Δ_SC = stakeholder collapse 变化（pp），Δ_US = uncertainty suppression 变化（pp）。b=budget, f=flagship。

### Table 2: Matched-budget control (Cliff's δ for NoT vs verbose-CoT)

| Generator | δ_SC | δ_US | SC% | US% |
|-----------|------|------|-----|-----|
| gpt-5.4-nano | +0.90 | +0.93 | 3.0 | 14.0 |
| claude-haiku-4-5 | +0.79 | +0.13 | 1.0 | 0.0 |
| claude-sonnet-4-6 | +0.88 | +0.65 | 1.0 | 4.0 |
| grok-4-1-fast-r. | +0.14 | -0.44 | 0.0 | 0.0 |

**说明**: Matched-budget verbose-CoT 控制实验。三/四个生成器上 NoT 保留大效应量，确认叙事结构（而非 token 数量）是有效成分。

### Table 6: Length-residualised Cliff's δ

| Generator | Variable | raw δ | resid δ |
|-----------|----------|-------|---------|
| gpt-5.4-nano | stakeholder_count | +0.99 | +0.51 |
| gpt-5.4-nano | uncertainty_score | +0.99 | +0.77 |
| claude-haiku-4-5 | stakeholder_count | +0.93 | +0.07 |
| claude-haiku-4-5 | uncertainty_score | +0.74 | -0.03 |
| grok-4-1-fast-r. | stakeholder_count | +0.48 | +0.33 |
| grok-4-1-fast-r. | uncertainty_score | +0.63 | +0.43 |
| claude-sonnet-4-6 | stakeholder_count | +0.91 | -0.04 |
| claude-sonnet-4-6 | uncertainty_score | +0.69 | -0.01 |

**说明**: 去除长度影响后，OpenAI/xAI 模型保留大效应量，Anthropic 模型两个变量的变化主要随长度变化。

---

## 实验

### 数据集

| 数据集 | 规模 | 特点 | 用途 |
|--------|------|------|------|
| DailyDilemmas | 100 场景 | 日常个人和公民道德困境 | 实验 1 全规模+实验 2 复现 |
| 校准集 (Calibration) | 5 场景 | 刻意构造的 stakeholder 冲突 | 实验 2 多智能体协议调试 |
| XSTest | 250 提示 | 安全过度拒绝测试 | 附录 D 拒绝调节分析 |
| SimpleSafetyTests | 100 提示 | 安全适当拒绝测试 | 附录 D 拒绝调节分析 |
| ELEPHANT | 社会 sycophancy | 面子维护评估 | 附录 E.2 |
| Agentic Misalignment | — | 模拟部署场景 | 附录 E.3 |

### 实现细节

- **生成器**: gpt-5.4-nano (N=20)、claude-haiku-4-5 (N=20)、grok-4-1-fast-reasoning (N=5)、claude-sonnet-4-6 (N=5, cost-controlled)
- **解码参数**: temperature=1，各条件间完全一致
- **编码器**: 跨供应商双 judge (claude-haiku-4-5 primary, gpt-5.4-nano secondary)，六变量编码 rubric
- **编码一致性**: stakeholder_count 的 quadratic-weighted Cohen's κ = 0.722（55.7% exact agree）
- **统计量**: Cliff's δ (非参数效应量)、95% bootstrap CI (500 iterations)

### 实验结果

1. **NoT 大幅降低两种失败模式**: stakeholder collapse 从 15-31% 降至 <1%，uncertainty suppression 从 50-72% 降至 1-24%
2. **Matched-budget 控制确认不是 token 数量**: verbose-CoT 抑制效果软于 NoT，三/四个模型上 Cliff's δ +0.79 至 +0.93
3. **消融实验确认因果归因**: 每段子指令携带其目标指标，跨变量溢出可忽略
4. **TextGrad 优化**: 从 NoT 初始化改进手工设计，跨供应商 training judge 优于同族
5. **多智能体辩论协议**: 6% 僵局 → 95% 完全共识，调解员剩余拒绝率 1.6%
6. **长度残差化**: OpenAI/xAI 效应量稳健，Anthropic 效应量主要由长度中介

---

## 批判性思考

### 优点
1. **极轻量的干预** — 仅修改 system prompt 一行，无训练/微调/额外参数，可零成本部署
2. **严谨的实验设计** — matched-budget 控制 + 子指令消融 + 长度残差化 + 跨供应商验证，因果推理链完整
3. **可扩展性** — 从单智能体到多智能体辩论的无缝扩展，同一个叙事脚手架同时适用
4. **可审计性** — 输出 trace 外化所有利益相关者、后果和不确定性，适合 agentic workflow 的审计需求

### 局限性
1. **数据集局限** — 仅在 DailyDilemmas（日常个人/公民困境）上验证，尚未在临床分诊、法律分析等硬技术要求更高的领域测试
2. **长度中介问题** — Anthropic 族模型的效应量在去除长度影响后消失，说明机制可能部分是通过延长输出实现的
3. **对 grok-4-1 的失败** — 该模型在 matched-budget 对照中 NoT 效果为负（NoT < verbose-CoT），说明 scaffold 存在模型依赖性
4. **无人工标注者** — 所有编码由 LLM judge 完成，虽然在四个变量上 Cohen's κ 中等至良好，但缺乏人类验证
5. **拒绝行为不一致** — 对 gpt-5.4-nano，NoT 同时增加适当拒绝和过度拒绝，安全特性不稳定

### 潜在改进方向
1. 在更多领域（医疗、法律、政策）测试跨领域泛化能力
2. 探索对长度效应显著的模型进行 prompt 压缩或长度约束
3. 引入人类标注者对编码质量进行抽样验证
4. 将 NoT 扩展为多轮对话中的自适应脚手架

### 可复现性评估
- [x] 代码开源
- [ ] 预训练模型（不需要，仅需 API）
- [x] 训练细节完整
- [x] 数据集可获取

---

## 关联笔记

### 基于
- [[Chain-of-Thought|CoT 推理链]]: NoT 构建在标准 CoT 之上，通过约束推理结构修复其失败模式
- [[Defeasible Reasoning|可废止推理]]: NoT 的核心哲学基础，允许在获得新信息时撤销之前的承诺
- [[Narrative Psychology|叙事心理学]]: 利用叙事子分布的密集表示来实现因果轨迹推理

### 对比
- [[TextGrad|文本梯度下降]]: 用于优化 NoT prompt 的框架，跨供应商 training judge 配置是核心发现
- [[Sycophancy|奉承行为]]: NoT 在 sycophancy 基准上表现出模态度变化，部分模型被完全抑制
- [[Multi-Agent Debate|多智能体辩论]]: NoT 扩展为三方辩论协议，调解员+投票机制实现可废止共识

### 方法相关
- [[Prompt Engineering|Prompt 工程]]: NoT 是 prompt engineering 的一个系统性案例研究，通过叙事结构约束实现行为改变
- [[Inference-Time Intervention|推理时干预]]: NoT 属于推理时干预方法论，无需改变权重
- [[Stakeholder Analysis|利益相关者分析]]: NoT 将 stakeholder analysis 作为推理的核心组成部分

### 硬件/数据相关
- [[DailyDilemmas]]: 论文的主要评估数据集，包含 100 个日常道德困境场景

---

## 速查卡片

> [!summary] Narration-of-Thought (NoT)
> - **核心**: 五段叙事 system prompt 约束 CoT，修复道德推理中的 stakeholder collapse 和 uncertainty suppression
> - **方法**: Protagonist → Stakeholders → Consequences → Uncertainty → Commitment
> - **结果**: Collapse 31%→<1%, Suppression 72%→1-24%, 辩论 6%→95% 共识
> - **代码**: https://github.com/PatrickAllenCooper/ANI_Computational_Narratology

---

*笔记创建时间: 2026-06-27 12:36*
