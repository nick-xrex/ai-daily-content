---
id: inbox_17e564c9
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0216-ruflo-releases-v3-10-13-agentdb-adr-073-sota-round-9af9]]"
title: "v3.10.13 — agentdb ADR-073 SOTA round"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.13
source: ruflo-releases
published_at: 2026-05-30T00:15:31+00:00
fetched_at: 2026-05-30T02:23:14.081399+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.13 发布（bundled agentdb 3.0.0-alpha.16，SOTA roadmap ADR-073）。安全方面关闭 3 个漏洞：parseJsonStrict 防止 JSON.parse 栈跟踪泄露、validateSqlIdentifier 防止 CWE-89 模板 SQL 注入、crypto.randomBytes() 替换 CWE-338 弱随机数生成。MCP 新增 3 个工具：causal_traverse（多跳图遍历）、agentdb_delete_batch（原子 IN-clause 删除）、consolidate_now（按需执行 NightlyLearner）。基准测试方面：提交真实的 recall benchmark 测试用例（scripts/benchmark-recall.mjs），生产规模（N=2000 D=384）实测 recall@10 = 0.912（超过 0.90 CI 下限），以此替代之前未经验证的「95%」声称；CI guard 防止 recall 下降。14 个新的回归测试覆盖安全 + MCP 处理器 + recall 下限。"
key_points:
  - "安全修复三则：parseJsonStrict 堵止 JSON 栈跟踪泄露、validateSqlIdentifier 防 CWE-89 模板注入、crypto.randomBytes() 替换弱随机源"
  - "MCP 工具扩展：causal_traverse（多跳记忆因果遍历）、agentdb_delete_batch（原子删除）、consolidate_now（按需内存合并运行）"
  - "度量改革：从「我们声称 95%」升级为真实 benchmark 测试数据（N=2000 D=384 上测得 recall@10=0.912）并提交测试用例，CI guard 守卫质量下限"
tags: [ruflo, agentdb, security, mcp, benchmarking, measurement, recall-metric]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## v3.10.13 — agentdb ADR-073 SOTA round

Ruflo v3.10.13 发布（bundled agentdb 3.0.0-alpha.16，SOTA roadmap ADR-073）。安全方面关闭 3 个漏洞：parseJsonStrict 防止 JSON.parse 栈跟踪泄露、validateSqlIdentifier 防止 CWE-89 模板 SQL 注入、crypto.randomBytes() 替换 CWE-338 弱随机数生成。MCP 新增 3 个工具：causal_traverse（多跳图遍历）、agentdb_delete_batch（原子 IN-clause 删除）、consolidate_now（按需执行 NightlyLearner）。基准测试方面：提交真实的 recall benchmark 测试用例（scripts/benchmark-recall.mjs），生产规模（N=2000 D=384）实测 recall@10 = 0.912（超过 0.90 CI 下限），以此替代之前未经验证的「95%」声称；CI guard 防止 recall 下降。14 个新的回归测试覆盖安全 + MCP 处理器 + recall 下限。

### 重點
- 安全修复三则：parseJsonStrict 堵止 JSON 栈跟踪泄露、validateSqlIdentifier 防 CWE-89 模板注入、crypto.randomBytes() 替换弱随机源
- MCP 工具扩展：causal_traverse（多跳记忆因果遍历）、agentdb_delete_batch（原子删除）、consolidate_now（按需内存合并运行）
- 度量改革：从「我们声称 95%」升级为真实 benchmark 测试数据（N=2000 D=384 上测得 recall@10=0.912）并提交测试用例，CI guard 守卫质量下限

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.13)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bumps the bundled agentdb to 3.0.0-alpha.16 ( ruvnet/agentdb#6 — SOTA roadmap, ADR-073). Three categories of improvement: 
 Security — three findings closed: 
 
 parseJsonStrict helper applied to the unguarded JSON.parse site (no more SyntaxError / stack-trace leak from crafted CLI input) 
 validateSqlIdentifier on the residual CWE-89 template-SQL in migrate.ts 
 crypto.randomBytes() IDs in agentdb-fast + GraphDatabaseAdapter (CWE-338) 
 
 MCP surface (3 new tools) : 
 
 causal_traverse — multi-hop graph walk for "why does this memory matter?" 
 agentdb_delete_batch — atomic IN-clause delete with id + table whitelist 
 consolidate_now — on-demand NightlyLearner run instead of waiting for a scheduled pass 
 
 Honest measurement : 
 
 Real recall@k benchmark harness committed ( scripts/benchmark-recall.mjs ) 
 Production-dim run at N=2000 D=384 measures recall@10 = 0.912 (above the documented 0.90 CI floor; the prior "95%" claim was unverified — committed run JSON replaces it) 
 CI guard in tests/recall-benchmark-harness.test.ts fails if recall drops below 0.90 
 
 Tests: 14 new regression tests across security + MCP-handler building blocks + recall floor. 
Full ruflo CLI suite still 2104/0/46-skipped. 
 Install: npx ruflo@3.10.13 
 Bigger SOTA items (RaBitQ 1-bit quantization, worker-thread batch pool, async HNSW rebuild, learned reranking head, tier-aware memory + EWC wiring) are tracked in ruvnet/agentdb#6 for the next round.

</details>