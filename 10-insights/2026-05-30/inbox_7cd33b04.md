---
id: inbox_7cd33b04
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-ruflo-releases-v3-10-23-joint-rerank-re-grid-rerank-ndc-e68a]]"
title: "v3.10.23 — joint rerank re-grid — rerank nDCG@3 0.900 → 0.963 (both paths at corpus ceiling)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.23
source: ruflo-releases
published_at: 2026-05-30T19:02:09+00:00
fetched_at: 2026-05-31T00:46:13.982542+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.23 聯合重排網格搜索。發現 rerank 路徑需要異於非 rerank 路徑的混合子參數：非 rerank 路徑最優 α=0.5, sw=2.0；rerank 路徑最優 α=0.5, sw=3.0, hw=0.7, cw=0.3。Rerank nDCG@3 從 0.900 → 0.963，兩路徑現在均達 corpus ceiling 0.963。trade-off 明確：hybrid 39ms top-3 precision 0.533 vs rerank 1000ms top-3 precision 0.700。"
key_points:
  - "聯合網格搜索發現路徑特定最優值：rerank 路徑需更高 subjectWeight (3.0 vs 2.0) 因下游有語義重排"
  - "nDCG@3: 0.900→0.963 (+7%)，top-3 hit rate 90%→100%，兩路徑均達 corpus ceiling"
  - "明確 cost-vs-richness trade-off：hybrid 39ms 適高吞吐，rerank 1000ms 適需要豐富排名的場景"
tags: [hyperparameter-tuning, cost-tradeoff, corpus-ceiling, reranking]
topics: []
importance: 3
novelty: 2
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.23 — joint rerank re-grid — rerank nDCG@3 0.900 → 0.963 (both paths at corpus ceiling)

Ruflo v3.10.23 聯合重排網格搜索。發現 rerank 路徑需要異於非 rerank 路徑的混合子參數：非 rerank 路徑最優 α=0.5, sw=2.0；rerank 路徑最優 α=0.5, sw=3.0, hw=0.7, cw=0.3。Rerank nDCG@3 從 0.900 → 0.963，兩路徑現在均達 corpus ceiling 0.963。trade-off 明確：hybrid 39ms top-3 precision 0.533 vs rerank 1000ms top-3 precision 0.700。

### 重點
- 聯合網格搜索發現路徑特定最優值：rerank 路徑需更高 subjectWeight (3.0 vs 2.0) 因下游有語義重排
- nDCG@3: 0.900→0.963 (+7%)，top-3 hit rate 90%→100%，兩路徑均達 corpus ceiling
- 明確 cost-vs-richness trade-off：hybrid 39ms 適高吞吐，rerank 1000ms 適需要豐富排名的場景

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.23)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What ships 
 Joint rerank re-grid — the rerank path's hybrid sub-params (α, sw) had been 
tuned against the OLD α=0.6/sw=3.0 baseline; with ADR-082 changing α/sw under it, 
a joint re-grid was the next ceiling-raiser. It paid off: rerank nDCG@3 0.900 → 0.963. 
 The key finding 
 The rerank path wants different hybrid sub-params than the non-rerank path: 
 
 
 
 Path 
 Best α 
 Best sw 
 Best hw/cw 
 nDCG@3 
 
 
 
 
 Non-rerank (hybrid only) 
 0.5 
 2.0 
 — 
 0.963 
 
 
 Rerank 
 0.5 
 3.0 
 hw=0.7 cw=0.3 
 0.963 
 
 
 
 When the cross-encoder is doing semantic understanding downstream, the hybrid 
stage can be more keyword-focused (higher subjectWeight). When hybrid is 
the final stage, lower subjectWeight gives body tokens room to contribute. 
 Implementation: subjectWeight default is now conditional on rerank flag 
(3.0 when reranking, 2.0 otherwise). Explicit param overrides. 
 The win 
 
 
 
 Metric (rerank path, labelled) 
 3.10.22 
 3.10.23 
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
 0.925 
 0.950 
 +0.025 
 
 
 Label precision@3 
 0.700 
 0.700 
 tied 
 
 
 Label nDCG@3 
 0.900 
 0.963 
 +0.063 (+7%) 
 
 
 Label nDCG@5 
 0.904 
 0.944 
 +0.040 
 
 
 
 Both paths now at corpus ceiling (nDCG@3 = 0.963) 
 The choice between them is now purely cost vs richness : 
 
 
 
 Path 
 Latency 
 Top-3 precision 
 Use when 
 
 
 
 
 Hybrid 
 39 ms 
 0.533 
 hot paths, throughput-bound 
 
 
 Rerank 
 1000 ms 
 0.700 
 richness-first, latency-tolerant 
 
 
 
 Cumulative SOTA push since cosine baseline (3.10.17 → 3.10.23) 
 
 
 
 Metric (labelled) 
 3.10.17 
 3.10.19 
 3.10.20 
 3.10.22 
 3.10.23 
 
 
 
 
 Hybrid nDCG@3 
 0.000 
 0.900 
 0.900 
 0.963 
 0.963 
 
 
 Rerank nDCG@3 
 — 
 — 
 0.913 
 0.900 
 0.963 
 
 
 Hybrid top-3 
 0% 
 90% 
 90% 
 100% 
 100% 
 
 
 Rerank top-3 
 — 
 — 
 100% 
 90% 
 100% 
 
 
 Rerank precision@3 
 — 
 — 
 0.667 
 0.700 
 0.700 
 
 
 
 What changed in code 
 
 subjectWeight default is now conditional on useRerank in src/mcp-tools/neural-tools.ts (3.0 if reranking, 2.0 otherwise). 
 hybridWeight / ceWeight defaults updated to grid winners: 0.5/0.5 → 0.7/0.3. 
 scripts/grid-search-retrieval.mjs extended with joint rerank sweep (28 configs across hw/cw × α × sw). 
 Schema descriptions updated to reflect the conditional defaults. 
 
 Pending for next iteration 
 Cross-repo generalisation test — all numbers in ADRs 077-083 are on the 
ruflo corpus. The real SOTA test is "does this hold up on a different repo's 
history?" Pretrain on agentdb / agentic-flow, run a similar labelled bench, 
see if nDCG@3 stays near 0.96. Tracked for 3.10.24 (or its own ADR-084). 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )
node v3/@claude-flow/cli/scripts/pretrain-from-github.mjs

 # Joint grid (~25 min) 
 cd v3/@claude-flow/cli &amp;&amp; node scripts/grid-search-retrieval.mjs

 # Verify both paths at corpus ceiling 
BENCH_NO_WRITE=1 node scripts/benchmark-pretrained-retrieval.mjs # hybrid → nDCG@3 0.963 
RERANK=1 BENCH_NO_WRITE=1 node scripts/benchmark-pretrained-retrieval.mjs # rerank → nDCG@3 0.963 (was 0.900) 
 Install 
 npx ruflo@3.10.23 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-083-joint-rerank-grid.md

</details>