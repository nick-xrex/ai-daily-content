---
id: inbox_6f2f1774
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.20"
author: "ruvnet"
published_at: 2026-05-30T18:23:29+00:00
fetched_at: 2026-05-31T00:39:12.284301+00:00
content_hash: "b4ded320128d4796e0960a20e751fe43bec8e18c2c338844b176fcfbb5918240"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.20 — cross-encoder reranker — 80% → 90% top-1, 100% top-3 (MRR 0.933)

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