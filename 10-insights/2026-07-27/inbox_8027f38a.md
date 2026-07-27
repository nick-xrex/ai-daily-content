---
id: inbox_8027f38a
date: 2026-07-27
source_ref: "[[00-inbox/2026-07-27/0123-ruflo-releases-v3-32-13-mixture-of-agents-route-mode-27-c336]]"
title: "v3.32.13 — Mixture-of-Agents route mode (#2778 dream)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.13
source: ruflo-releases
published_at: 2026-07-27T00:32:51+00:00
fetched_at: 2026-07-27T01:30:01.697679+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.13 引入了 Mixture-of-Agents（MoA）路由模式，一种基于学术研究（arXiv 2605.01566、ACL 2026）的并行代理协调策略。该特性通过 `--mode moa` 标志启用，支持配置 `--moa-parallel`（默认 3）和 `--consensus` 选项（多数投票或置信度排序）。根据发布说明，MoA 通过并行多个 Haiku 生成器和一个合成器，在相等成本下相比 self-consistency 方法获得 2.7pp 的准确度提升。新增的 moaPlan 字段在路由结果中记录执行计划，验证覆盖 7 个 Haiku agent 槽位 + 1 个合成器的端到端场景。"
key_points:
  - "Mixture-of-Agents 架构：N 个并行 Haiku 代理 + 1 个合成器进行多数投票或置信度聚合"
  - "性能数据：相同成本下比 self-consistency 方法提升 2.7pp 准确度（arXiv 2605.01566 验证）"
  - "配置灵活性：--moa-parallel 默认 3（可调），--consensus 支持 majority-vote 或 best-confidence"
tags: [ruflo, mixture-of-agents, agent-routing, test-time-scaling, multi-agent-pattern]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.13 — Mixture-of-Agents route mode (#2778 dream)

Ruflo v3.32.13 引入了 Mixture-of-Agents（MoA）路由模式，一种基于学术研究（arXiv 2605.01566、ACL 2026）的并行代理协调策略。该特性通过 `--mode moa` 标志启用，支持配置 `--moa-parallel`（默认 3）和 `--consensus` 选项（多数投票或置信度排序）。根据发布说明，MoA 通过并行多个 Haiku 生成器和一个合成器，在相等成本下相比 self-consistency 方法获得 2.7pp 的准确度提升。新增的 moaPlan 字段在路由结果中记录执行计划，验证覆盖 7 个 Haiku agent 槽位 + 1 个合成器的端到端场景。

### 重點
- Mixture-of-Agents 架构：N 个并行 Haiku 代理 + 1 个合成器进行多数投票或置信度聚合
- 性能数据：相同成本下比 self-consistency 方法提升 2.7pp 准确度（arXiv 2605.01566 验证）
- 配置灵活性：--moa-parallel 默认 3（可调），--consensus 支持 majority-vote 或 best-confidence

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.13)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Closes the last item of the 2026-07-26 dream-cycle 3-task bundle. 
 Added 
 hooks route --mode moa — Mixture-of-Agents fanout plan. Dream-cycle #2778 (arXiv 2605.01566, ACL 2026 SRW): test-time scaling is Pareto-optimal when parallel generations exceed sequential aggregations — +2.7pp accuracy over self-consistency at equal cost. 
 New flags: 
 
 --mode single|moa (default: single) — opts into MoA planning. 
 --moa-parallel N (default: 3) — fanout width. Distinct name to avoid a boolean-flag collision with --parallel in swarm/workflow. 
 --consensus majority-vote|best-confidence (default: majority-vote). 
 
 When --mode=moa , the router adds a moaPlan field to the result telling the caller to spawn N parallel Haiku Task calls with the primary agent's role, then a synthesizer Task that reads all N verdicts and picks the majority (or highest-confidence) answer. The rationale field explains whether the swap saves cost (only unambiguously below Tier-3 Sonnet). 
 E2E verified: hooks route --mode moa --moa-parallel 7 → 7 Haiku agent slots + 1 synthesizer, JSON output splices moaPlan cleanly, single mode omits the plan. 
 Upgrade 
 npx ruflo@latest --version # → 3.32.13 
 Refs: dream-cycle #2778 .

</details>