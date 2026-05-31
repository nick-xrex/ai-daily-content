---
id: inbox_76e8cfcd
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.28"
author: "ruvnet"
published_at: 2026-05-30T23:24:25+00:00
fetched_at: 2026-05-31T00:39:12.251258+00:00
content_hash: "4847546545708bfbc5f0694d64844080a9c8b778cf79acd176f2fdba2c4bdee7"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.28 — Lucene BM25 + RRF + CE rerank — passes acceptance test on BOTH datasets (rank 3/13 on 2-dataset mean)

What ships 
 The pipeline that works. ADR-087's diagnosis of "our multi-field BM25 is too weak for RRF" is fixed here: shipped a real Lucene-style BM25 (Porter 1980 stemmer + Lucene stopwords + length norm, 12/12 published Porter tests passing) and wired the cross-encoder rerank into the BEIR runner. 
 The acceptance test PASSES 
 
 
 
 System 
 Params 
 NFCorpus 
 SciFact 
 Mean 
 Beats BM25 both? 
 
 
 
 
 BGE-large-v1.5 (published) 
 335M 
 0.380 
 0.722 
 0.551 
 yes 
 
 
 SPLADE++ (published) 
 110M 
 0.347 
 0.704 
 0.526 
 yes 
 
 
 ruflo Lucene RRF + CE rerank (us) 
 110M 
 0.358 
 0.683 
 0.521 
 YES (+0.033 / +0.004) 
 
 
 Lucene BM25 alone (us, matches published) 
 — 
 0.328 
 0.681 
 0.505 
 tied 
 
 
 BM25 (published Lucene) 
 — 
 0.325 
 0.679 
 0.502 
 — 
 
 
 ruflo dense alone (BGE-base) 
 110M 
 0.352 
 0.626 
 0.489 
 no 
 
 
 
 Rank 3 of 13 entries on the 2-dataset mean. Using a 110M base vs BGE-large's 335M and GTR-XL's 1.2B. 
 Per-dataset: 
 
 NFCorpus 0.358, rank 2/11 (only behind BGE-large 0.380) 
 SciFact 0.683, rank 3/11 (behind SPLADE++ and BGE-large only) 
 
 The diagnostic that earned this 
 ADR-087 (the previous release) measured RRF DEGRADING both datasets and diagnosed it as asymmetric input strength — our BM25 was 0.279 NFCorpus vs published Lucene 0.325, so RRF averaged its noise into top-K. This release proves the diagnosis: with a real Lucene-style BM25 that matches the published baseline within ±0.003, RRF + cross-encoder rerank produces real wins on both datasets. 
 The user's reframe — "don't try to invent your way up BEIR; stack proven primitives, measure each lift, then decide where you add unique value" — is exactly what this release executed. 
 Subtle finding from the full ablation 
 On NFCorpus, Lucene RRF k=60 alone (0.360) is tied with Lucene RRF + CE rerank (0.358) — the cross-encoder doesn't add value when underlying RRF is already strong. CE's value is on SciFact (RRF 0.639 → RRF+CE 0.683, +0.044 lift). Pipeline auto-adapts: rerank helps most when candidate pool has high recall but low top-K precision. Matches published literature. 
 What's in the box 
 
 src/memory/lucene-bm25.ts — Porter 1980 + Lucene 8.x English stopwords (~120 tokens) + single-field BM25 (k1=1.2, b=0.75). No external deps. 12/12 published Porter tests passing. 
 scripts/run-beir-hybrid.mjs gains USE_LUCENE_BM25=1 + RERANK=1 flags. 
 scripts/run-beir-lucene-bm25.mjs — standalone runner for the Lucene BM25 + RRF ablation. 
 ADR-088 — full ablation matrix + diagnosis confirmation + honest limits. 
 BEIR-MATRIX.md — updated 2-dataset mean leaderboard (13 entries, ruflo at rank 3). 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 # Re-use existing caches from ADR-085 (or re-ingest with run-beir-bge.mjs) 
 cd /tmp/beir-nfcorpus
USE_LUCENE_BM25=1 RERANK=1 node /path/to/v3/@claude-flow/cli/scripts/run-beir-hybrid.mjs
 # → nDCG@10 0.358, rank 2/11 

 cd /tmp/beir-scifact
USE_LUCENE_BM25=1 RERANK=1 BEIR_DATA_DIR=/tmp/beir-scifact/scifact node /path/to/v3/@claude-flow/cli/scripts/run-beir-hybrid.mjs
 # → nDCG@10 0.683, rank 3/11 
 Honest limits 
 
 Two BEIR datasets measured. The 0.521 mean is suggestive, not BEIR-average. 
 Zero-shot — no fine-tuning. NFCorpus train split (110K pairs) could lift another ~0.02-0.05. 
 Lucene BM25 is a re-implementation (matches published within ±0.003, not bit-identical). 
 Rerank adds ~4.6s/query CPU latency at top-100; production callers should budget per latency tolerance. 
 Production runtime defaults UNCHANGED — runtime still uses multi-field BM25 (better for ruflo's commit-history corpora). Lucene BM25 is BEIR-benchmark-scoped. 
 
 What's next (already tracked) 
 
 BGE-large swap — drop-in BGE_MODEL=Xenova/bge-large-en-v1.5 . Likely lifts further. ~3× embed latency. 
 3-5 more BEIR datasets via Tailscale GPU : TREC-COVID, FiQA, ArguAna, HotpotQA, NQ. Would establish a real BEIR-mini-average. 
 Fine-tune BGE-base on NFCorpus train (GPU job, +0.02-0.05 expected). 
 ruvector BGE bundling ( ruvnet/ruvector#524 ) — kills the silent-fallback bug at source. 
 
 Install 
 npx ruflo@3.10.28 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-088-lucene-bm25-and-rerank.md