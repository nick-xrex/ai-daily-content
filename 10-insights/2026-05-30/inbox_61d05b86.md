---
id: inbox_61d05b86
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/1800-ruflo-releases-v3-10-14-self-learning-wiring-adr-074-cl-e479]]"
title: "v3.10.14 — self-learning wiring (ADR-074, closes #2245)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.14
source: ruflo-releases
published_at: 2026-05-30T15:39:35+00:00
fetched_at: 2026-05-30T18:05:10.280917+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.14 修復 #2245 號報告的關鍵問題：自學系統報告成功但未持久化任何可查詢的結果。發布完成 3 個 CLI 端配線：hooks_task-completed 現呼叫真實的 SONA + EWC++ 軌跡管線 (之前僅返回 patternsLearned: 0 的佔位符)；signalsProcessed 從死指標恢復為信號持久化計數，重啟後不再歸零；hooks_pretrain 透過 storeNeuralPatterns 將模式寫入神經存儲。基準測試證明：signalsProcessed +10、訓練 10/10 @~18 毫秒/呼叫、預訓練儲存 10/列出 10、多步 5 個持久化/5 個 SONA 更新，全部通過。此修復揭示系統設計原則：學習信號必須貫穿完整端到端管線 (收集→處理→持久化→檢索)。"
key_points:
  - "修復 3 個 CLI 配線：hooks_task-completed 呼叫真實 SONA+EWC++、signalsProcessed 恢復為持久化計數、hooks_pretrain 寫入神經存儲"
  - "基準測試 signalsProcessed +10、訓練 10/10 @~18 ms/call、預訓練 10/10、多步 5/5"
  - "模式：前端成功報告 + 後端空結果的矛盾源於管線不完整；端到端貫通是必須"
tags: [ruflo, self-learning-wiring, trajectory-pipeline, signal-persistence, end-to-end]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.14 — self-learning wiring (ADR-074, closes #2245)

Ruflo v3.10.14 修復 #2245 號報告的關鍵問題：自學系統報告成功但未持久化任何可查詢的結果。發布完成 3 個 CLI 端配線：hooks_task-completed 現呼叫真實的 SONA + EWC++ 軌跡管線 (之前僅返回 patternsLearned: 0 的佔位符)；signalsProcessed 從死指標恢復為信號持久化計數，重啟後不再歸零；hooks_pretrain 透過 storeNeuralPatterns 將模式寫入神經存儲。基準測試證明：signalsProcessed +10、訓練 10/10 @~18 毫秒/呼叫、預訓練儲存 10/列出 10、多步 5 個持久化/5 個 SONA 更新，全部通過。此修復揭示系統設計原則：學習信號必須貫穿完整端到端管線 (收集→處理→持久化→檢索)。

### 重點
- 修復 3 個 CLI 配線：hooks_task-completed 呼叫真實 SONA+EWC++、signalsProcessed 恢復為持久化計數、hooks_pretrain 寫入神經存儲
- 基準測試 signalsProcessed +10、訓練 10/10 @~18 ms/call、預訓練 10/10、多步 5/5
- 模式：前端成功報告 + 後端空結果的矛盾源於管線不完整；端到端貫通是必須

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.14)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Wires up the self-learning subsystem the reporter found was reporting success but persisting nothing queryable ( #2245 ). Three CLI-side wirings + honest multi-path output + a proof harness. 
 What's fixed 
 
 hooks_task-completed {trainPatterns: true} now invokes the real SONA + EWC++ trajectory pipeline (was a stub returning patternsLearned: 0 ). Returns learningPath: 'trajectory-pipeline' | 'recorded-only' so callers know what happened. 
 signalsProcessed was a dead counter — initialized 3×, read 1×, incremented 0× anywhere. Now wired into bridgeStoreEntry so every memory-bridge write counts. loadPersistedStats also restores patternsLearned + signalsProcessed so a process restart no longer zeroes the learning history. 
 hooks_pretrain now writes per-pattern rows into the neural store (via new storeNeuralPatterns ), so neural_patterns list reflects them. Response surfaces both patternsBundled + patternsIndexed + sources.stores . 
 
 Honest multi-path messaging (per the goal-condition) 
Every learning-adjacent surface declares the path it took and the store(s) it wrote to. The task-completed description lists the three paths explicitly: (a) trainPatterns:true for one-step learning, (b) hooks_intelligence_trajectory-* for multi-step, (c) memory_store for storage without learning. 
 Adversarial hardening ( #2241 ASI06) 
Basic content sanitization on task-completed content before it feeds SONA (strip ASCII control chars, cap to 4 KB). 
 Proof 
 
 __tests__/self-learning-2245.test.ts — 9 tests across EASY / MEDIUM / COMPLEX categories. CI gate. 
 scripts/benchmark-self-learning.mjs — 5 sections (A–E), writes a committed run JSON. Latest run: signalsProcessed +10, trained=10/10 at ~18 ms/call, pretrain stored=10/listed=10, multi-step persisted=5/sonaUpdate=5. All passed. 
 Reproduction guide: v3/docs/learning/self-learning-2245-proof.md 
 ADR: v3/docs/adr/ADR-074-self-learning-wiring-2245.md 
 
 Install: npx ruflo@3.10.14 
 Tracked for round 2 (not in this release) 
Unify the 4 stat aggregators (globalStats / memory_bridge / hooks_metrics / neural_patterns); wire post-edit / post-command to feed the trajectory pipeline; Structured Distillation ( #2241 ) of trajectory content for 11× compression + better MRR.

</details>