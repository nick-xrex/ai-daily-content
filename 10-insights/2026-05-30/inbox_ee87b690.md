---
id: inbox_ee87b690
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-ruflo-releases-v3-10-22-grid-search-retrieval-defaults-4737]]"
title: "v3.10.22 — grid-search retrieval defaults — nDCG@3 0.900 → 0.963 (+7%)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.22
source: ruflo-releases
published_at: 2026-05-30T18:48:56+00:00
fetched_at: 2026-05-31T00:46:13.990550+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.22 針對已標記語料庫重新網格搜索檢索默認值。舊默認（α=0.6, sw=3.0, mmrLambda=0.5）是針對誤導性的正則表達式代理調優。新網格（32 config）發現：α=0.5 勝過 0.6（α=0.7 完全崩潰，top-1 跌至 40-50%），sw=2 勝過 3 和 5（sw=3 壓制 body tokens），mmrLambda=0.7 勝過 0.5。混合路徑 nDCG@3 0.900→0.963，top-3 hit rate 90%→100%。"
key_points:
  - "α=0.5 (vs 0.6)：BM25 比初始信用的在此語料更有區分力；α=0.7 完全崩潰"
  - "sw=2 (vs 3)：身體 token 貢獻度更高；mmrLambda=0.7 (vs 0.5)：純相關度排名優於多樣性偏好"
  - "nDCG@3 0.900→0.963 (+7%)，precision@3 0.4→0.533"
tags: [hyperparameter-grid, bm25-vs-neural, default-tuning]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.22 — grid-search retrieval defaults — nDCG@3 0.900 → 0.963 (+7%)

Ruflo v3.10.22 針對已標記語料庫重新網格搜索檢索默認值。舊默認（α=0.6, sw=3.0, mmrLambda=0.5）是針對誤導性的正則表達式代理調優。新網格（32 config）發現：α=0.5 勝過 0.6（α=0.7 完全崩潰，top-1 跌至 40-50%），sw=2 勝過 3 和 5（sw=3 壓制 body tokens），mmrLambda=0.7 勝過 0.5。混合路徑 nDCG@3 0.900→0.963，top-3 hit rate 90%→100%。

### 重點
- α=0.5 (vs 0.6)：BM25 比初始信用的在此語料更有區分力；α=0.7 完全崩潰
- sw=2 (vs 3)：身體 token 貢獻度更高；mmrLambda=0.7 (vs 0.5)：純相關度排名優於多樣性偏好
- nDCG@3 0.900→0.963 (+7%)，precision@3 0.4→0.533

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.22)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What ships 
 Grid-search-tuned retrieval defaults against the ADR-081 labelled corpus. 
The previous defaults (α=0.6, subjectWeight=3.0, mmrLambda=0.5) were tuned 
against the regex proxy that ADR-081 then revealed was misleading — so we 
re-tuned properly. 
 The win 
 
 
 
 Metric (hybrid path, labelled) 
 3.10.21 
 3.10.22 
 Δ 
 
 
 
 
 Label top-1 
 90% 
 90% 
 tied 
 
 
 Label top-3 
 90% 
 100% 
 +10pp 
 
 
 Label MRR@3 
 0.900 
 0.950 
 +0.05 
 
 
 Label precision@3 
 0.400 
 0.533 
 +0.13 
 
 
 Label nDCG@3 
 0.900 
 0.963 
 +0.06 (+7%) 
 
 
 Label nDCG@5 
 0.875 
 0.938 
 +0.06 
 
 
 Avg latency 
 42 ms 
 55 ms 
 +13 ms 
 
 
 
 The findings 
 Grid swept 32 configs (27 hybrid + 5 rerank) using labelled nDCG@3 as the 
canonical metric: 
 
 
 α=0.5 beats α=0.6, α=0.7 is broken. At α=0.7 (more cosine, less BM25) 
top-1 collapsed to 40-50% across every other parameter combination. BM25 
carries more discriminating power than the bi-encoder on this corpus 
than the original 0.6 default credited it with. 
 
 
 subjectWeight=2 beats sw=3 and sw=5. Less subject weight lets body 
tokens contribute relevance that gets crowded out at sw=3. 
 
 
 mmrLambda=0.7 beats 0.5 and 0.3. Less diversity bias / more pure 
relevance ranking pulls more relevant docs into top-3. 
 
 
 What's still pending 
 A joint α/sw × hybridWeight/ceWeight re-grid for the rerank path — 
the rerank winner (hw=0.7 cw=0.3) was tested against OLD α=0.6 sw=3.0 
baselines; with new α=0.5 sw=2.0 the joint optimum shifted. Kept rerank 
weights at 0.5/0.5 conservatively. Next iteration. 
 Cumulative SOTA push since cosine baseline (3.10.17 → 3.10.22) 
 
 
 
 Metric (labelled) 
 3.10.17 
 3.10.19 
 3.10.20 
 3.10.22 
 
 
 
 
 Label top-1 (hybrid) 
 0% 
 90% 
 90% 
 90% 
 
 
 Label top-3 (hybrid) 
 0% 
 90% 
 90% 
 100% 
 
 
 Label nDCG@3 (hybrid) 
 0.000 
 0.900 
 0.900 
 0.963 
 
 
 Label precision@3 (hybrid) 
 0.000 
 0.400 
 0.400 
 0.533 
 
 
 
 What changed in code 
 
 Defaults updated in src/mcp-tools/neural-tools.ts :
 
 alpha: 0.6 → 0.5 
 subjectWeight: 3.0 → 2.0 
 mmrLambda: 0.5 → 0.7 
 
 
 New script scripts/grid-search-retrieval.mjs — re-runnable harness, 
sweeps hyperparameter space, picks winners by nDCG/top-1/precision@3. 
 --quick mode for fast iteration. 
 Run JSONs at docs/benchmarks/runs/grid-search-retrieval-{ts,latest}.json 
with full per-config metrics. 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 # Pretrain (415 patterns) 
node v3/@claude-flow/cli/scripts/pretrain-from-github.mjs

 # Grid-search (~1 min) 
 cd v3/@claude-flow/cli &amp;&amp; node scripts/grid-search-retrieval.mjs

 # Verify new defaults 
BENCH_NO_WRITE=1 node scripts/benchmark-pretrained-retrieval.mjs
 # → Label nDCG@3 0.963, top-1 90%, top-3 100%, precision@3 0.533 
 Install 
 npx ruflo@3.10.22 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-082-grid-search-retrieval-defaults.md

</details>