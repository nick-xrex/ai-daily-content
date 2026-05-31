---
id: inbox_4bfdd606
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/1800-ruflo-releases-v3-10-16-round-b-wiring-round-c-structur-6121]]"
title: "v3.10.16 — Round B wiring + Round C Structured Distillation (ADR-076)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.16
source: ruflo-releases
published_at: 2026-05-30T16:33:20+00:00
fetched_at: 2026-05-30T18:05:10.276383+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.16 包含兩個重點：Round B 完成 #2245 學習管線的配線工作，Round C 實現基於 arXiv:2603.13017 論文的結構化蒸餾。新增 4 欄位架構 (summary、detail、labels、paths) 將高信號標記放在前排，改進檢索排序。在 30 個軌跡的 MRR 基準測試中 (bridge ONNX embedder, Xenova/all-MiniLM-L6-v2)，蒸餾後的 MRR 從 0.0964 提升至 0.1367，提升幅度 +41.8%。規則型蒸餾器目前達 0.74 倍壓縮 (反向擴大 35%)，遠低於論文的 11 倍目標，但框架預留了可互換接口供未來的學習型蒸餾器達成目標壓縮率。"
key_points:
  - "結構化蒸餾 4 欄位架構 (summary/detail/labels/paths) 將高信號標記置於前排"
  - "MRR 改進 0.0964 → 0.1367 (+41.8%)，方向與 arXiv:2603.13017 一致"
  - "當前壓縮率 0.74 倍 (規則型)，論文目標 11 倍；預留接口供學習型蒸餾器插入"
tags: [ruflo, structured-distillation, mrr-optimization, arxiv-2603.13017, trajectory-retrieval]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.16 — Round B wiring + Round C Structured Distillation (ADR-076)

Ruflo v3.10.16 包含兩個重點：Round B 完成 #2245 學習管線的配線工作，Round C 實現基於 arXiv:2603.13017 論文的結構化蒸餾。新增 4 欄位架構 (summary、detail、labels、paths) 將高信號標記放在前排，改進檢索排序。在 30 個軌跡的 MRR 基準測試中 (bridge ONNX embedder, Xenova/all-MiniLM-L6-v2)，蒸餾後的 MRR 從 0.0964 提升至 0.1367，提升幅度 +41.8%。規則型蒸餾器目前達 0.74 倍壓縮 (反向擴大 35%)，遠低於論文的 11 倍目標，但框架預留了可互換接口供未來的學習型蒸餾器達成目標壓縮率。

### 重點
- 結構化蒸餾 4 欄位架構 (summary/detail/labels/paths) 將高信號標記置於前排
- MRR 改進 0.0964 → 0.1367 (+41.8%)，方向與 arXiv:2603.13017 一致
- 當前壓縮率 0.74 倍 (規則型)，論文目標 11 倍；預留接口供學習型蒸餾器插入

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.16)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Two SOTA-direction rounds packaged together. 
 Round B — finishes the #2245 wiring story (closes the "wiring side" gap left in ADR-074/ADR-075) 
 
 hooks_post-edit now feeds the trajectory pipeline (synthesises a one-step trajectory from the edit outcome). 
 hooks_post-command does the same for command outcomes. 
 hooks_intelligence_trajectory-end ALSO bumps globalStats (was only feeding sonaCoordinator); response includes learning.globalStatsTrajectoriesDelta . 
 Every handler returns learningPath: 'trajectory-pipeline' | 'recorded-only' + an explicit note naming what fired. 
 
 Round C — Structured Distillation ( #2241 §SOTA, arXiv:2603.13017) 
 
 New module src/memory/structured-distill.ts — 4-field schema ( summary / detail / labels / paths ), rule-based deterministic extractor, embedding-ready serialiser that puts high-signal tokens at the front. 
 New corpus bench/trajectory-mrr-corpus.json — 30 paired (raw, query) trajectories. 
 New MRR harness scripts/benchmark-trajectory-mrr.mjs — bridge ONNX embedder with hash-deterministic fallback (clearly warned as degraded). 
 
 Measured proof (bridge ONNX, Xenova/all-MiniLM-L6-v2, N=30): 
 
 
 
 Metric 
 Raw 
 Distilled 
 Δ 
 
 
 
 
 MRR 
 0.0964 
 0.1367 
 +0.0403 (+41.8%) 
 
 
 Direction 
 — 
 — 
 ✅ distilled better 
 
 
 
 Direction matches arXiv:2603.13017 (+0.014 absolute on a 214K paper corpus); relative delta is larger here because the small curated corpus benefits more from labels-and-paths-first ordering. 
 Honest: a rule-based distiller cannot deliver the paper's 11× byte compression (current ratio: 0.74× — distilled is 35% bigger). The schema, corpus, harness, and serialiser are in place so a future round can plug in a learned distiller as a drop-in extractor swap and pick up that compression number while keeping this MRR direction. 
 Tests: 9 schema tests + 3 Round B wiring tests = 12 new. Affected suite 135/135. 
 Install: npx ruflo@3.10.16

</details>