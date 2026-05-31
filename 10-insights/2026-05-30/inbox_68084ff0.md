---
id: inbox_68084ff0
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/1800-ruflo-releases-v3-10-15-unified-learning-stats-adr-075-531c]]"
title: "v3.10.15 — unified learning stats (ADR-075)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.15
source: ruflo-releases
published_at: 2026-05-30T16:09:24+00:00
fetched_at: 2026-05-30T18:05:10.279403+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.15 統一了碎片化的學習統計來源。系統原本有 4 個獨立統計源：globalStats (軌跡管線計數)、sonaCoordinator (進程內 SONA)、memory-bridge (AgentDB 條目)、neural-patterns (神經存儲列表)，各測量不同層級但相互矛盾。修復方案不是統一存儲，而是統一視圖。新增 getUnifiedLearningStats() 返回所有 4 個子視圖，每個標示其來源路徑。同時加入一致性檢查區塊偵測跨存儲漂移 (例如 globalStats 報告 N 個模式但 neural_patterns 為空)。7 個跨存儲一致性測試驗證修復，並通過 123/123 個完整測試。"
key_points:
  - "統一視圖方案聚合 4 個不同層的統計源：globalStats、sonaCoordinator、memory-bridge、neural-patterns"
  - "新增 getUnifiedLearningStats() 和 hooks_intelligence_unified-stats MCP 工具"
  - "一致性檢查區塊自動偵測跨存儲漂移，7 個測試驗證跨層一致性"
tags: [ruflo, learning-stats, observability, unified-view, data-consistency]
topics: [foundation_models.claude, agents.mcp]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.15 — unified learning stats (ADR-075)

Ruflo v3.10.15 統一了碎片化的學習統計來源。系統原本有 4 個獨立統計源：globalStats (軌跡管線計數)、sonaCoordinator (進程內 SONA)、memory-bridge (AgentDB 條目)、neural-patterns (神經存儲列表)，各測量不同層級但相互矛盾。修復方案不是統一存儲，而是統一視圖。新增 getUnifiedLearningStats() 返回所有 4 個子視圖，每個標示其來源路徑。同時加入一致性檢查區塊偵測跨存儲漂移 (例如 globalStats 報告 N 個模式但 neural_patterns 為空)。7 個跨存儲一致性測試驗證修復，並通過 123/123 個完整測試。

### 重點
- 統一視圖方案聚合 4 個不同層的統計源：globalStats、sonaCoordinator、memory-bridge、neural-patterns
- 新增 getUnifiedLearningStats() 和 hooks_intelligence_unified-stats MCP 工具
- 一致性檢查區塊自動偵測跨存儲漂移，7 個測試驗證跨層一致性

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.15)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Resolves the "four contradictory stat sources" item ADR-074 deferred to a future round. 
 The four sources turned out not to be duplicates — they authoritatively measure four different layers (globalStats = trajectory-pipeline counters, sonaCoordinator = in-process SONA, memory-bridge = AgentDB entries, neural-patterns = neural store rows). So the fix is to aggregate the view , not the store. 
 New surface 
 
 getUnifiedLearningStats() — returns all 4 sub-views with each sub-view naming its source path 
 hooks_intelligence_unified-stats MCP tool exposing it 
 getMemoryBridgeStats() + getNeuralStoreStats() — exported helpers 
 A consistency block that flags cross-store drift (e.g. globalStats reports N patterns but neural_patterns is empty) instead of silently disagreeing 
 
 Verification 
 
 7 cross-store consistency tests 
 Benchmark §F observed: global=10/11 tracks SONA, bridge=10 rows, neural=10, sona.available=true, 1 consistency note correctly flagging the pretrain-vs-neural-store gap 
 123/123 across unified-stats + self-learning + mcp-tools-deep 
 
 Install: npx ruflo@3.10.15

</details>