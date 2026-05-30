---
id: inbox_37bdd54a
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-ruflo-releases-v3-10-9-per-task-bandit-learning-honest-88dd]]"
title: "v3.10.9 — per-task bandit learning + honest intelligence labeling"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.9
source: ruflo-releases
published_at: 2026-05-29T17:37:41+00:00
fetched_at: 2026-05-30T02:24:09.163178+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.9 完成智能系統審計清單，修復了所有可修復項並誠實記載無法修復的上限。Per-task bandit priors 改由複雜度桶（低/中/高）而非全局提前，阻止一個任務類型的失敗壓制所有任務的模型；EWC++ 誠實度澄清 F_i 為嵌入重要性代理而非真梯度曲率 Fisher；HNSW 後端標籤區分原生 vs stub（search 返回空陣列=故障可見）；MicroLoRA 修復 applyUpdates() 簽名 bug（傳遞浮點陣列而非標量學習率）。文檔化但未修復：WASM 加速 HNSW 不存在、WASM MicroLoRA apply() 實測仍惰性。三包鎖步發布 3.10.9，CI 29/29 綠。"
key_points:
  - "Per-task bandit priors 按複雜度桶而非全局，8 Haiku 失敗不再壓制全部"
  - "EWC++ 誠實度：F_i 是嵌入代理非真實 Fisher 曲率"
  - "誠實限制：WASM HNSW 不存在、WASM MicroLoRA 測試仍惰性（拒絕合成虛假梯度）"
tags: [routing-learning, multi-task-bandit, honesty-audit]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.9 — per-task bandit learning + honest intelligence labeling

Ruflo v3.10.9 完成智能系統審計清單，修復了所有可修復項並誠實記載無法修復的上限。Per-task bandit priors 改由複雜度桶（低/中/高）而非全局提前，阻止一個任務類型的失敗壓制所有任務的模型；EWC++ 誠實度澄清 F_i 為嵌入重要性代理而非真梯度曲率 Fisher；HNSW 後端標籤區分原生 vs stub（search 返回空陣列=故障可見）；MicroLoRA 修復 applyUpdates() 簽名 bug（傳遞浮點陣列而非標量學習率）。文檔化但未修復：WASM 加速 HNSW 不存在、WASM MicroLoRA apply() 實測仍惰性。三包鎖步發布 3.10.9，CI 29/29 綠。

### 重點
- Per-task bandit priors 按複雜度桶而非全局，8 Haiku 失敗不再壓制全部
- EWC++ 誠實度：F_i 是嵌入代理非真實 Fisher 曲率
- 誠實限制：WASM HNSW 不存在、WASM MicroLoRA 測試仍惰性（拒絕合成虛假梯度）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.9)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruflo v3.10.9 — per-task bandit learning + honest intelligence labeling 
 Completes the intelligence-audit punch-list ( docs/reviews/intelligence-system-audit-2026-05-29.md ): fixes the genuinely-fixable items and documents honest ceilings for the rest — without fabricating any signals. 
 Fixed 
 
 Per-task bandit priors (ADR-142) — model-routing Beta priors are now keyed by complexity bucket (low/med/high) instead of global-per-model. Failures on one task type no longer suppress a model for all task types (the "8 Haiku failures suppress Haiku everywhere" defect). Backward-compatible schema migration (v1 flat → seed all buckets, version:2 ); proven by a per-bucket isolation test + a migration test. 
 EWC++ honesty — clarifies F_i is a heuristic embedding-importance proxy ( embedding_i2 ), not true gradient-curvature Fisher. 
 HNSW backend label — ruvector-native vs ruvector-stub-search-disabled ; isWasm()===true means the broken stub (search returns [] ), not acceleration, so a regression is now visible. 
 MicroLoRA — fixed the genuine applyUpdates() signature bug (passed a Float32Array where the WASM runtime wants a scalar learning rate). 
 
 Honest ceilings (NOT fixable in-repo — documented, not faked) 
 
 WASM-accelerated HNSW : no WASM HNSW build exists in the stack; native NAPI is already fastest (~1.9–6.5× at N=20k); "150×–12,500×" is unreachable here. 
 WASM MicroLoRA apply() : empirically still inert after the flush (Δ=0 after 200 adapts). We deliberately do not synthesize a gradient from the scalar quality to fake adaptation — that would be a fabricated signal (the same class as the Flash Math.random metric the audit removed). 
 
 All three packages published at 3.10.9 ( latest / alpha / v3alpha in lockstep). CI: 29/29 green. This closes the intelligence punch-list — every item is now fixed, shipped, or documented with an honest reason it's deferred. 
 🤖 Generated with RuFlo

</details>