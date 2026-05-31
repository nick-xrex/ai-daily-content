---
id: inbox_474af7b7
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-ruflo-releases-v3-10-27-rrf-ablation-harness-honest-neg-846b]]"
title: "v3.10.27 — RRF ablation harness + HONEST NEGATIVE RESULT (default RRF degrades nDCG@10)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.27
source: ruflo-releases
published_at: 2026-05-30T22:01:56+00:00
fetched_at: 2026-05-31T00:45:17.091429+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.27 發布誠實的 ablation 研究：RRF（互惠排名融合）k=60 在兩個 BEIR 數據集上均惡化 nDCG@10（NFCorpus -0.024、SciFact -0.057 相對 dense-only 基準），違反教科書預期。根本原因：RRF 成功需要『質量相當但失敗模式互補的系統』，而 Ruflo 的 multi-field BM25 相比 Lucene 基準弱 14%（0.279 vs 0.325），導致 RRF 將弱系統噪音平均進 top-K。但 Recall@100 實際提升（NFCorpus +0.016、SciFact +0.123），為 Stage 2 cross-encoder rerank 預留資源。並揭露隱藏 bug：bge-cache 路徑硬編碼，SciFact 運行無聲覆蓋 NFCorpus 緩存，v3.10.25–26 結果經驗證仍有效。"
key_points:
  - "RRF 在非對稱輸入強度下失敗（自製 BM25 0.279 vs Lucene 0.325），平均弱系統噪音反而惡化 nDCG@10，驗證 RRF 必要條件是『可比強度』"
  - "Recall@100 提升（SciFact +0.123）表示候選池完整度好，為 Stage 2 cross-encoder rerank 準備充分資源"
  - "誠實報告負面結果與 debug 發現：無聲緩存覆蓋 bug 的根源、下一步修復路徑（Lucene BM25 實現）已預先追蹤"
tags: [search-ranking, rrf, ablation-study, honest-reporting]
topics: []
importance: 3
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.27 — RRF ablation harness + HONEST NEGATIVE RESULT (default RRF degrades nDCG@10)

Ruflo v3.10.27 發布誠實的 ablation 研究：RRF（互惠排名融合）k=60 在兩個 BEIR 數據集上均惡化 nDCG@10（NFCorpus -0.024、SciFact -0.057 相對 dense-only 基準），違反教科書預期。根本原因：RRF 成功需要『質量相當但失敗模式互補的系統』，而 Ruflo 的 multi-field BM25 相比 Lucene 基準弱 14%（0.279 vs 0.325），導致 RRF 將弱系統噪音平均進 top-K。但 Recall@100 實際提升（NFCorpus +0.016、SciFact +0.123），為 Stage 2 cross-encoder rerank 預留資源。並揭露隱藏 bug：bge-cache 路徑硬編碼，SciFact 運行無聲覆蓋 NFCorpus 緩存，v3.10.25–26 結果經驗證仍有效。

### 重點
- RRF 在非對稱輸入強度下失敗（自製 BM25 0.279 vs Lucene 0.325），平均弱系統噪音反而惡化 nDCG@10，驗證 RRF 必要條件是『可比強度』
- Recall@100 提升（SciFact +0.123）表示候選池完整度好，為 Stage 2 cross-encoder rerank 準備充分資源
- 誠實報告負面結果與 debug 發現：無聲緩存覆蓋 bug 的根源、下一步修復路徑（Lucene BM25 實現）已預先追蹤

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.27)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What ships 
 Honest negative result. The textbook "lowest-regret" first move — BM25+dense RRF k=60 — degrades nDCG@10 on both NFCorpus and SciFact because our multi-field BM25 is materially weaker than Lucene's. We ship the ablation harness + the finding anyway. 
 Acceptance test outcome 
 "RRF improves or preserves nDCG@10 on both NFCorpus and SciFact, bootstrap CI does not undermine the claim, defaults fixed before viewing test result." FAILS. 
 
 
 
 Config (BOTH datasets, fixed defaults BEFORE viewing) 
 NFCorpus 
 SciFact 
 Mean 
 
 
 
 
 dense alone (BGE-base) 
 0.352 
 0.626 
 0.489 
 
 
 RRF k=60 equal (textbook default) 
 0.328 ↓ 
 0.569 ↓ 
 0.449 ↓ 
 
 
 RRF k=30 equal (best ablation) 
 0.335 ↓ 
 0.582 ↓ 
 0.459 ↓ 
 
 
 RRF k=60 dense=1.2, bm25=0.8 
 0.334 ↓ 
 0.577 ↓ 
 0.456 ↓ 
 
 
 RRF k=60 dense=0.8, bm25=1.2 
 0.323 ↓ 
 0.558 ↓ 
 0.441 ↓ 
 
 
 
 Every RRF variant underperforms dense-alone on the 2-dataset mean (-0.04 nDCG@10 worse). 
 What DID work — recall 
 Recall@100 IS up on both: 
 
 
 
 Dataset 
 Dense R@100 
 RRF R@100 
 Δ 
 
 
 
 
 NFCorpus 
 0.305 
 0.321 
 +0.016 
 
 
 SciFact 
 0.828 
 0.951 
 +0.123 
 
 
 
 RRF surfaces more candidates correctly — it just ranks them worse at top-K. This is the right setup for stage 2: cross-encoder rerank on the wider candidate pool (ADR-088 / 3.10.28). 
 Diagnosis (why RRF hurt) 
 The classic RRF win assumes comparably-strong systems with different failure modes . Our setup is asymmetric: BGE-base dense is strong (0.626 SciFact), our multi-field BM25 is weak (0.576 SciFact vs Lucene published 0.679). Pure BM25 nDCG@10 on NFCorpus: 0.279 vs Lucene 0.325 — we're 14% relative below. 
 When one input is weak, RRF averages its noise into top positions instead of cancelling it. The math works perfectly for the documented Lucene+strong-dense case; we don't match that profile yet. 
 Bug found and fixed 
 bge-cache/ was hardcoded to /tmp/beir-nfcorpus/bge-cache/ — the SciFact run silently overwrote the NFCorpus cache. Caught only when the first RRF run returned nDCG=0.14 (random-noise level), forcing investigation. Now per-dataset path. 3.10.25 and 3.10.26 NFCorpus numbers were computed before the overwrite and are still valid. 
 What's in the box 
 
 scripts/run-beir-rrf-ablation.mjs — re-runnable ablation harness with bootstrap CI on the fixed default config + full ablation matrix. 
 scripts/run-beir-hybrid.mjs — full RRF + opt-in cross-encoder rerank runner (rerank wired but pending ADR-088 measurement). 
 bge-cache/ per-dataset path fix in run-beir-bge.mjs. 
 ADR-087 — full negative-result writeup with diagnosis + tracked next steps. 
 Updated BEIR-MATRIX.md with ablation rows + the honest 2-dataset mean comparison. 
 No default change — dense-only stays the BEIR runner default. RRF is opt-in for callers with Lucene-strength BM25. 
 
 Next steps (already tracked) 
 
 ADR-088 / 3.10.28 : Cross-encoder rerank on RRF's wider candidate pool (Recall@100 0.951 on SciFact says the candidates ARE there). 
 Lucene-style BM25 : Porter/Snowball stemmer + Lucene stopword list + length norm. Would make RRF actually work as designed. 
 ruvnet/RuVector#524 : bundle BGE in ruvector so downstream packages stop hitting the sharp dependency. 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

mkdir -p /tmp/beir-nfcorpus &amp;&amp; cd /tmp/beir-nfcorpus
curl -sL -o nf.zip ' https://public.ukp.informatik.tu-darmstadt.de/thakur/BEIR/datasets/nfcorpus.zip ' &amp;&amp; unzip -q nf.zip
node /path/to/v3/@claude-flow/cli/scripts/run-beir-bge.mjs # ingest 
node /path/to/v3/@claude-flow/cli/scripts/run-beir-rrf-ablation.mjs # ablation matrix 
 Install 
 npx ruflo@3.10.27 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-087-rrf-negative-result.md

</details>