---
id: inbox_e43d2bb9
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/2201-ruflo-releases-v3-32-41-honest-routing-scores-honest-mo-a1e0]]"
title: "v3.32.41 — honest routing scores, honest MoE metrics, real pattern transfer"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.41
source: ruflo-releases
published_at: 2026-07-30T16:30:39+00:00
fetched_at: 2026-07-30T22:06:30.269071+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.41 修復三個影響 Agent 路由和轉移的缺陷。#2864 修復路由評分門檻不一致：學習模式要求 ≥0.65 而靜態模式要求 >0.4，導致低分學習路由被高分靜態路由壓制。真實存儲測試中 61 個重放路由僅 1 個由學習模式決定（一致性 49%）。#2865 修復 MoE 儀表板硬編碼 82.0% 路由準確率假值，改為無實際數據時省略而非造假。#2859 修復跨項目轉移虛報統計：以前未實際讀寫目標記憶體存儲而按百分比計算平均信心和年齡，現在執行真實合併並儲存實際結果。三項修復均通過真實 CLI 重現驗證。"
key_points:
  - "路由評分門檻不一致：學習模式 ≥0.65 vs 靜態模式 >0.4，導致 1/61 路由由學習模式決定，一致性僅 49%"
  - "MoE 儀表板虛報 82.0% 準確率，改為無實際數據時省略"
  - "跨項目轉移以前造假平均信心/年齡，現改為真實讀寫和計算"
tags: [routing-accuracy, moe-metrics, pattern-transfer, honest-metrics]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.41 — honest routing scores, honest MoE metrics, real pattern transfer

Ruflo v3.32.41 修復三個影響 Agent 路由和轉移的缺陷。#2864 修復路由評分門檻不一致：學習模式要求 ≥0.65 而靜態模式要求 >0.4，導致低分學習路由被高分靜態路由壓制。真實存儲測試中 61 個重放路由僅 1 個由學習模式決定（一致性 49%）。#2865 修復 MoE 儀表板硬編碼 82.0% 路由準確率假值，改為無實際數據時省略而非造假。#2859 修復跨項目轉移虛報統計：以前未實際讀寫目標記憶體存儲而按百分比計算平均信心和年齡，現在執行真實合併並儲存實際結果。三項修復均通過真實 CLI 重現驗證。

### 重點
- 路由評分門檻不一致：學習模式 ≥0.65 vs 靜態模式 >0.4，導致 1/61 路由由學習模式決定，一致性僅 49%
- MoE 儀表板虛報 82.0% 準確率，改為無實際數據時省略
- 跨項目轉移以前造假平均信心/年齡，現改為真實讀寫和計算

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.41)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixed 
 #2864 — hooks route gated learned routing patterns at score ≥0.65 vs static patterns at &gt;0.4, so a top-scoring learned pattern could lose to a lower-scoring static one that simply cleared the easier bar. Measured 49% agreement with the router's own recorded training labels on a real store (only 1/61 replayed routes decided by a learned pattern). Both sources now share the same score gate; support/reliability remain the learned-specific quality guard. 
 #2865 — the hooks intelligence MoE panel showed a hardcoded Routing Accuracy: 82.0% (plus Active Experts/Load Balance constants) whenever any local neural data existed, regardless of actual routing quality — the same "self-confidence presented as accuracy" problem already fixed on the hooks metrics path in an earlier release. These fields are now omitted rather than fabricated when no real value is reported. 
 #2859 — hooks transfer from-project reported success and quality stats (avgConfidence, avgAge) without ever reading or writing the destination project's memory store — every number was invented from fixed percentages of the source pattern count. Now performs a real merge: reads the destination, skips low-confidence/duplicate/conflicting entries, and actually persists whatever remains. Reported counts and stats are computed from what was actually processed. 
 All three verified against the exact reproductions in their issues using the real built CLI (not unit mocks). 
 PR: #2869 
 Packages 
 `@claude-flow/cli`, `claude-flow`, and `ruflo` are all at 3.32.41 ; `latest`, `alpha`, and `v3alpha` dist-tags all point to it.

</details>