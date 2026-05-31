---
id: inbox_c804a3f6
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/1801-ruflo-releases-v3-10-30-4-dataset-beir-rank-3-11-mean-c-10e1]]"
title: "v3.10.30 — 4-dataset BEIR (rank 3/11 mean) + config-divergence finding"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.30
source: ruflo-releases
published_at: 2026-05-31T07:21:35+00:00
fetched_at: 2026-05-31T18:06:48.266778+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.30 在 BEIR 檢索基準上新增第 4 個資料集（SciDocs），達到 4 資料集平均排名 3/11。核心發現：無單一管道通殺所有資料集。SciDocs 結果 nDCG@10 0.211（排名 2/11），僅落後 BGE-large（0.225），勝於 BM25、GTR-XL（1.2B）。4 資料集平均：Ruflo 於 110M 參數下達 0.421（排名 3/11），超越 SPLADE++（−0.012，基本並駕）與 GTR-XL（1/10 參數）；核心差距源自 ArguAna 資料集適配。配置發散關鍵發現：NFCorpus/SciFact 最優於 Lucene+RRF+CE rerank；ArguAna 最優於 Lucene+RRF（CE rerank 反而傷害 −0.008）；SciDocs 最優於 dense alone（RRF 傷害）。論文建議自動管道選擇需每語料庫校準器（輕量級，無需 GPU）。誠實限制：僅覆蓋 BEIR 4/18 資料集；零樣本評估（未用 NFCorpus/ArguAna 訓練集）；5 大資料集（TREC-COVID 等 >50k 文檔）仍受 GPU 限制。"
key_points:
  - "4 資料集平均 nDCG@10 0.421，排名 3/11，超越 1.2B 參數模型（僅用 110M）"
  - "配置發散啟示：無通用最優管道 → 需要動態管道選擇或每語料庫校準"
  - "零樣本評估限制：4/18 BEIR 資料集、大型資料集仍 GPU 限制、訓練集未用"
tags: [ruflo, beir-benchmark, retrieval, sparse-dense-fusion, config-divergence]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.30 — 4-dataset BEIR (rank 3/11 mean) + config-divergence finding

Ruflo v3.10.30 在 BEIR 檢索基準上新增第 4 個資料集（SciDocs），達到 4 資料集平均排名 3/11。核心發現：無單一管道通殺所有資料集。SciDocs 結果 nDCG@10 0.211（排名 2/11），僅落後 BGE-large（0.225），勝於 BM25、GTR-XL（1.2B）。4 資料集平均：Ruflo 於 110M 參數下達 0.421（排名 3/11），超越 SPLADE++（−0.012，基本並駕）與 GTR-XL（1/10 參數）；核心差距源自 ArguAna 資料集適配。配置發散關鍵發現：NFCorpus/SciFact 最優於 Lucene+RRF+CE rerank；ArguAna 最優於 Lucene+RRF（CE rerank 反而傷害 −0.008）；SciDocs 最優於 dense alone（RRF 傷害）。論文建議自動管道選擇需每語料庫校準器（輕量級，無需 GPU）。誠實限制：僅覆蓋 BEIR 4/18 資料集；零樣本評估（未用 NFCorpus/ArguAna 訓練集）；5 大資料集（TREC-COVID 等 >50k 文檔）仍受 GPU 限制。

### 重點
- 4 資料集平均 nDCG@10 0.421，排名 3/11，超越 1.2B 參數模型（僅用 110M）
- 配置發散啟示：無通用最優管道 → 需要動態管道選擇或每語料庫校準
- 零樣本評估限制：4/18 BEIR 資料集、大型資料集仍 GPU 限制、訓練集未用

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.30)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What ships 
 4th BEIR dataset (SciDocs) joins NFCorpus + SciFact + ArguAna. New finding: no single pipeline wins everywhere. 
 SciDocs results 
 
 
 
 Pipeline 
 nDCG@10 
 Rank 
 
 
 
 
 dense alone (BGE-base) 
 0.211 
 2/11 
 
 
 Lucene RRF (no rerank) 
 0.203 
 (-0.008, RRF hurt) 
 
 
 
 Only behind BGE-large (335M, 0.225). Beats BM25, GTR-XL (1.2B), every other published baseline. 
 4-dataset mean leaderboard 
 
 
 
 System 
 Params 
 NFCorpus 
 SciFact 
 ArguAna 
 SciDocs 
 Mean 
 
 
 
 
 BGE-large (published) 
 335M 
 0.380 
 0.722 
 0.636 
 0.225 
 0.491 
 
 
 SPLADE++ (published) 
 110M 
 0.347 
 0.704 
 0.521 
 0.159 
 0.433 
 
 
 ruflo best (per-dataset) 
 110M 
 0.358 
 0.683 
 0.432 
 0.211 
 0.421 
 
 
 GTR-XL (1.2B) 
 1.2B 
 0.343 
 0.662 
 0.439 
 0.174 
 0.405 
 
 
 GenQ 
 110M 
 0.319 
 0.644 
 0.493 
 0.143 
 0.400 
 
 
 BM25 (Lucene published) 
 — 
 0.325 
 0.679 
 0.397 
 0.158 
 0.390 
 
 
 
 Rank 3 of 11 on 4-dataset mean. Beats GTR-XL with 1/10× the params. Loses only to SPLADE++ (-0.012, basically tied) and BGE-large (-0.070, mostly the ArguAna gap). 
 The config-divergence finding 
 After 4 datasets, no single pipeline wins everywhere : 
 
 
 
 Dataset 
 Best config 
 What hurts 
 
 
 
 
 NFCorpus 
 Lucene + RRF + CE rerank 
 nothing 
 
 
 SciFact 
 Lucene + RRF + CE rerank 
 nothing 
 
 
 ArguAna 
 Lucene + RRF (no CE) 
 CE rerank actively hurts 
 
 
 SciDocs 
 dense alone 
 RRF hurt by 0.008 
 
 
 
 Three of four datasets pick a different best config. Auto-pipeline-selection would need a per-corpus calibrator (cheap, doesn't need GPU — tracked). 
 Honest limits 
 
 4/18 BEIR datasets. The 0.421 mean is suggestive, not BEIR-average. 
 Zero-shot — NFCorpus and ArguAna train splits remain unused. 
 The 5 biggest BEIR datasets (TREC-COVID, FiQA, HotpotQA, NQ, DBPedia, all &gt;50k docs) remain GPU-gated. 
 
 Install 
 npx ruflo@3.10.30 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-091-scidocs-and-config-divergence.md

</details>