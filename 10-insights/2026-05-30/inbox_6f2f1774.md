---
id: inbox_6f2f1774
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-ruflo-releases-v3-10-20-cross-encoder-reranker-80-90-to-b4de]]"
title: "v3.10.20 — cross-encoder reranker — 80% → 90% top-1, 100% top-3 (MRR 0.933)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.20
source: ruflo-releases
published_at: 2026-05-30T18:23:29+00:00
fetched_at: 2026-05-31T00:47:58.076987+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.20 加入 cross-encoder reranker（Xenova/ms-marco-MiniLM-L-6-v2，int8 量化，~30MB），採用混合策略（0.5·hybrid + 0.5·cross-encoder）將 top-1 hit rate 從 80% 推至 90%、top-3 從 80% 推至 100%，MRR 達 0.933。延遲代價為 39ms → 984ms（可選啟用）。完整 ablation 表顯示單獨使用 cross-encoder 在短 commit 主題上表現較弱（MS MARCO 校準噪聲），而 hybrid 則優於 top-1；weight grid-search 確認加權區間 0.3:0.7 至 0.5:0.5 均達最優 MRR 0.933。三版本累積進度（3.10.17 cosine 0% → 3.10.19 hybrid 80% → 3.10.20 rerank 90% top-1）展示檢索管線漸進式優化。"
key_points:
  - "混合策略：0.5·hybrid + 0.5·cross-encoder，MRR 0.800 → 0.933，top-1 top-3 分別達 90% / 100%"
  - "模型細節：Xenova/ms-marco-MiniLM-L-6-v2 int8，~30MB，lazy-loaded，無網路時優雅降級無拋錯"
  - "延遲折衝：opt-in rerank 帶來 25× 延遲成本（1s vs 39ms），預設仍用 hybrid 保持熱路徑速度，設計決策由 ablation 驅動"
tags: [cross-encoder-rerank, hybrid-retrieval, neural-ranking, ablation-study]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.20 — cross-encoder reranker — 80% → 90% top-1, 100% top-3 (MRR 0.933)

Ruflo v3.10.20 加入 cross-encoder reranker（Xenova/ms-marco-MiniLM-L-6-v2，int8 量化，~30MB），採用混合策略（0.5·hybrid + 0.5·cross-encoder）將 top-1 hit rate 從 80% 推至 90%、top-3 從 80% 推至 100%，MRR 達 0.933。延遲代價為 39ms → 984ms（可選啟用）。完整 ablation 表顯示單獨使用 cross-encoder 在短 commit 主題上表現較弱（MS MARCO 校準噪聲），而 hybrid 則優於 top-1；weight grid-search 確認加權區間 0.3:0.7 至 0.5:0.5 均達最優 MRR 0.933。三版本累積進度（3.10.17 cosine 0% → 3.10.19 hybrid 80% → 3.10.20 rerank 90% top-1）展示檢索管線漸進式優化。

### 重點
- 混合策略：0.5·hybrid + 0.5·cross-encoder，MRR 0.800 → 0.933，top-1 top-3 分別達 90% / 100%
- 模型細節：Xenova/ms-marco-MiniLM-L-6-v2 int8，~30MB，lazy-loaded，無網路時優雅降級無拋錯
- 延遲折衝：opt-in rerank 帶來 25× 延遲成本（1s vs 39ms），預設仍用 hybrid 保持熱路徑速度，設計決策由 ablation 驅動

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.20)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What ships 
 Cross-encoder reranker (opt-in) — Xenova/ms-marco-MiniLM-L-6-v2 (int8, 
~30MB) lazy-loaded via @xenova/transformers, gracefully degrading when 
unavailable. Pushes top-1 from 80% → 90% and top-3 from 80% → 100% on 
the same A/B harness. 
 Cumulative SOTA push (3.10.17 → 3.10.20) 
 
 
 
 Metric 
 3.10.17 cosine 
 3.10.18 hybrid 
 3.10.19 multi-field 
 3.10.20 +rerank 
 
 
 
 
 Top-1 hit rate 
 0% 
 50% 
 80% 
 90% 
 
 
 Top-3 hit rate 
 0% 
 70% 
 80% 
 100% 
 
 
 MRR@3 
 0.000 
 0.583 
 0.800 
 0.933 
 
 
 Top-1 diversity 
 100% 
 80% 
 100% 
 100% 
 
 
 Avg query latency 
 29 ms 
 41 ms 
 39 ms 
 984 ms (opt-in) 
 
 
 
 The ablation that drove the architecture 
 
 
 
 Configuration 
 Top-1 
 Top-3 
 MRR@3 
 
 
 
 
 Hybrid only (3.10.19) 
 8/10 
 8/10 
 0.800 
 
 
 Cross-encoder alone (over top-30 pool) 
 6/10 
 10/10 
 0.733 
 
 
 Combined 0.5·hybrid + 0.5·CE (3.10.20 default) 
 9/10 
 10/10 
 0.933 
 
 
 
 Cross-encoder alone finds all relevant docs in top-3 but loses top-1 — 
MS MARCO's calibration on short commit subjects is noisy. Hybrid is the 
opposite: strong top-1, weaker top-3. Linear combination captures both. 
 Weight grid-search confirms a broad plateau: 
 
 
 
 hybrid : ce 
 top-1 
 top-3 
 MRR@3 
 
 
 
 
 0.5 : 0.5 (default) 
 9/10 
 10/10 
 0.933 
 
 
 0.4 : 0.6 
 9/10 
 10/10 
 0.933 
 
 
 0.3 : 0.7 
 9/10 
 10/10 
 0.933 
 
 
 
 Why opt-in 
 Latency cost is ~25× hybrid (1.0 s vs 39 ms per query at N=385). The default 
hybrid path stays for hot paths and batch retrieval. Callers needing SOTA 
relevance flip {rerank: true} per call. 
 What changed in code 
 
 
 src/memory/cross-encoder-rerank.ts — lazy-loaded singleton via direct 
 AutoTokenizer + AutoModelForSequenceClassification . The xenova v2 
 pipeline('text-classification') API can't handle {text, text_pair} pairs 
reliably; the lower-level API does. Handles single-logit (sigmoid) AND 
binary-logit (softmax) heads. 
 
 
 One-shot load policy — after a failed load, subsequent calls return 
null immediately. No retry loops in hot paths. 
 
 
 neural_patterns MCP tool — three new params: 
 
 rerank: boolean (default false) 
 hybridWeight: number (default 0.5) 
 ceWeight: number (default 0.5) 
 Response includes crossEncoderScore when rerank is on. 
 
 
 
 5 new tests in __tests__/cross-encoder-rerank.test.ts covering the 
graceful-degradation contract (no network needed — forces failure with a 
guaranteed-bad model name). 
 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 # Unit tests (no network) — 44 total 
( cd v3/@claude-flow/cli &amp;&amp; npx vitest run __tests__/cross-encoder-rerank.test.ts __tests__/hybrid-retrieval.test.ts __tests__/pretrain-from-github.test.ts )

 # Live A/B (cross-encoder downloads ~30MB on first run) 
 cd v3/@claude-flow/cli
node scripts/pretrain-from-github.mjs
node scripts/benchmark-pretrained-retrieval.mjs # 3.10.19 default → 80% top-1 
RERANK=1 node scripts/benchmark-pretrained-retrieval.mjs # 3.10.20 + rerank → 90%/100% 
HYBRID=0 node scripts/benchmark-pretrained-retrieval.mjs # cosine baseline → 0% 
 Honest limits 
 
 N=385, 10 queries, regex-relevance proxy. Direction (0% → 90% top-1) is 
robust to noise; absolute numbers could shift on a different corpus. A 
labelled held-out evaluation is the right next gauge. 
 30 MB cross-encoder model downloads on first run. Subsequent runs hit 
local cache. 
 The remaining 10% top-1 gap is one query that the regex can't see clearly 
— may be genuinely ambiguous or a regex-proxy artefact. 
 
 What's next 
 
 Labelled held-out corpus for tighter relevance confidence intervals 
 Larger cross-encoder (ms-marco-MiniLM-L-12-v2) if quality matters more 
than latency 
 Learned distiller ( #2241 round-D) — still tracked 
 
 Install 
 npx ruflo@3.10.20 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-080-cross-encoder-reranker.md

</details>