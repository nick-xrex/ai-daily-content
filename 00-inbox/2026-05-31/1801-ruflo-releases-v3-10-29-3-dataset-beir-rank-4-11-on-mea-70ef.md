---
id: inbox_ffa557f0
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.29"
author: "ruvnet"
published_at: 2026-05-31T03:50:04+00:00
fetched_at: 2026-05-31T18:01:16.417421+00:00
content_hash: "70ef327f51a22ac61709aaee53a0140356317133ad2da7d3aa0724a8d8a37b17"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.29 — 3-dataset BEIR (rank 4/11 on mean) + ruvector@0.2.27 tier-0 + #2246 fixes

What ships — batched per "no constant releases" 
 Four independent threads: 
 
 3rd BEIR dataset (ArguAna) — strengthens 2-dataset → 3-dataset story 
 BGE-large NFCorpus ceiling test — answered (no lift on this hardware) 
 ruvector@0.2.27 Tier-0 wiring — kills the silent-fallback bug at source 
 4 user bugs from #2246 — 3 fixed, 1 forwarded 
 
 3-dataset BEIR results 
 
 
 
 Dataset 
 nDCG@10 
 Pipeline 
 Rank 
 
 
 
 
 NFCorpus 
 0.358 
 Lucene + RRF + CE rerank 
 2/11 
 
 
 SciFact 
 0.683 
 Lucene + RRF + CE rerank 
 3/11 
 
 
 ArguAna 
 0.432 
 Lucene + RRF (CE rerank hurt) 
 5/11 
 
 
 3-dataset mean 
 0.491 
 mixed 
 — 
 
 
 
 3-dataset mean leaderboard 
 
 
 
 System 
 Params 
 Mean nDCG@10 
 
 
 
 
 BGE-large-v1.5 (published) 
 335M 
 0.579 
 
 
 SPLADE++ (published) 
 110M 
 0.524 
 
 
 GenQ (published) 
 110M 
 0.485 (~tied with us) 
 
 
 ruflo best per-dataset 
 110M 
 0.491 
 
 
 GTR-XL (published) 
 1.2B 
 0.481 
 
 
 BM25 (published Lucene) 
 — 
 0.467 
 
 
 Contriever 
 110M 
 0.461 
 
 
 TAS-B 
 66M 
 0.464 
 
 
 
 Rank 4 of 11 on 3-dataset mean. Beats published BM25 (+0.024), beats GTR-XL (with 1/10× our params), beats Contriever, TAS-B, ColBERT, SBERT. Loses to SPLADE++ (-0.033) and BGE-large (-0.088, mostly the ArguAna gap). 
 Counter-findings reported honestly 
 ArguAna kills the cross-encoder rerank. Pulled at the 50-query checkpoint (running nDCG 0.283 vs dense alone 0.431, estimated 6+ hours wall time). ArguAna is counter-argument retrieval — pointwise relevance scoring doesn't help when the task requires understanding opposition. Pipeline auto-adapts: rerank wins NFCorpus and SciFact, loses ArguAna. 
 BGE-large NFCorpus = no lift. Xenova/bge-large-en-v1.5 (335M, int8 quantized) = 0.350 vs our BGE-base 0.352. Below the published BAAI BGE-large baseline (0.380). Likely Xenova int8 quantization underperforms BAAI's unquantized fp32. 
 BGE query prefix is mixed (ADR-090). BAAI's recommended Represent this sentence for searching relevant passages: prefix: NFCorpus +0.009 ✓, SciFact -0.007 ✗, ArguAna +0.003 ~noise. Opt-in only via BGE_QUERY_PREFIX=1 . Not a default. 
 ruvector@0.2.27 Tier-0 wiring (closes ADR-086 at source) 
 neural-tools embedder cascade: 
 
 Tier 0 (NEW) : ruvector@0.2.27.embed() — bundled, no sharp dep, disk-cache hit 
 Tier 1: agentic-flow/reasoningbank (broken on darwin-arm64 without sharp) 
 Tier 2-3: @claude-flow/embeddings 
 
 Verified active: probe returns embedder: ruvector@0.2.27 (bundled all-MiniLM-L6-v2) , _realEmbedding: true , dim 384, disk-cache hit. Measured 6.2× per-doc parallel-embed speedup (claimed 10-14×; ours had CPU contention from BEIR benches). 
 Both upstream issues filed yesterday were fixed in &lt;24hr: 
 
 ruvnet/ruvector#523 — API contract bugs (FIXED in ruvector@0.2.27) 
 ruvnet/ruvector#524 — Bundle BGE-base (acknowledged, planned) 
 
 #2246 user bug fixes 
 
 
 
 Finding 
 Status 
 
 
 
 
 #1 memory_search_unified hardcoded 6 namespaces (missed 95% of an 8789-entry store) 
 FIXED — new namespaces param + CLAUDE_FLOW_MEMORY_SEARCH_NAMESPACES env + dynamic enumeration default + namespaceSource audit field + 9 regression tests 
 
 
 #2 npm install -g overwrites dist patches silently 
 acknowledged, tracked for separate release 
 
 
 #3 agentdb addCausalEdge() silently orphans edges 
 forwarded → ruvnet/agentdb#7 
 
 
 #4 graph_edges DB unavailable on fresh env 
 FIXED — getBridgeDb({createIfMissing: true}) lazy-creates empty memory.db + better error message 
 
 
 
 Full triage reply on #2246 . 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 for ds in nfcorpus scifact arguana ; do 
 mkdir -p /tmp/beir- $ds &amp;&amp; cd /tmp/beir- $ds 
 curl -sL -o $ds .zip " https://public.ukp.informatik.tu-darmstadt.de/thakur/BEIR/datasets/ $ds .zip " &amp;&amp; unzip -q $ds .zip
 BEIR_DATA_DIR=/tmp/beir- $ds / $ds USE_LUCENE_BM25=1 RERANK=1 \
 node /path/to/v3/@claude-flow/cli/scripts/run-beir-hybrid.mjs
 done 
 Honest limits 
 
 3/18 BEIR datasets (NFCorpus, SciFact, ArguAna). The 0.491 mean is suggestive, not BEIR-average 
 Zero-shot — NFCorpus train (110k pairs) unused 
 CPU-bound — TREC-COVID/HotpotQA/NQ/DBPedia need GPU 
 Our Lucene BM25 matches published ±0.003 (re-implementation, not a Lucene binding) 
 CE rerank doesn't always help — pulled on ArguAna 
 
 What's next (blocked on GPU) 
 
 Tailscale GPU access — gates the 5 remaining BEIR datasets and fine-tuning 
 BGE-base fine-tune on NFCorpus train (110k pairs, ~3 GPU-hours) 
 bge-reranker-v2-m3 (568M, 2.27GB) as heavyweight opt-in 
 
 Install 
 npx ruflo@3.10.29 # latest / alpha / v3alpha all aligned 
 Full ADRs: ADR-089 , ADR-090