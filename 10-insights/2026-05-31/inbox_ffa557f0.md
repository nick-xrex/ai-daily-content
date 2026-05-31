---
id: inbox_ffa557f0
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/1801-ruflo-releases-v3-10-29-3-dataset-beir-rank-4-11-on-mea-70ef]]"
title: "v3.10.29 — 3-dataset BEIR (rank 4/11 on mean) + ruvector@0.2.27 tier-0 + #2246 fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.29
source: ruflo-releases
published_at: 2026-05-31T03:50:04+00:00
fetched_at: 2026-05-31T18:08:30.414112+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 3.10.29 發布，在 BEIR 基準的 3 個數據集（NFCorpus、SciFact、ArguAna）上達成 mean nDCG@10 0.491，排名 4/11，擊敗發布的 BM25 基準 (+0.024) 及 Contriever、TAS-B。核心改進是整合 ruvector@0.2.27 作為 Tier-0 embedding 級聯，bundled all-MiniLM-L6-v2、無額外依賴，實現 6.2× per-doc 並行加速。修複 3 個用户反饋的 bug：memory_search 硬編碼 6 命名空間（遺漏 95% 記錄）、graph edges DB 初始化缺失。實驗發現跨編碼器 rerank 在 ArguAna（反論檢索）上反而降低效果（nDCG 0.283 vs dense 0.431），管道自適應禁用。"
key_points:
  - "3-dataset mean 0.491 排名 4/11；beats BM25 (+0.024)、Contriever、TAS-B；loses SPLADE++ (-0.033)、BGE-large (-0.088)"
  - "ruvector@0.2.27 Tier-0 bundled all-MiniLM-L6-v2、無 sharp 依賴、disk-cache hit；測得 6.2× per-doc 並行加速"
  - "CE rerank 在 ArguAna (counter-argument retrieval) 上有害 (nDCG 0.283 vs dense 0.431)，管道自動禁用；BGE-large 在 NFCorpus 無提升"
tags: [beir-benchmark, embedding-cascade, neural-ranking, ruvector]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.29 — 3-dataset BEIR (rank 4/11 on mean) + ruvector@0.2.27 tier-0 + #2246 fixes

Ruflo 3.10.29 發布，在 BEIR 基準的 3 個數據集（NFCorpus、SciFact、ArguAna）上達成 mean nDCG@10 0.491，排名 4/11，擊敗發布的 BM25 基準 (+0.024) 及 Contriever、TAS-B。核心改進是整合 ruvector@0.2.27 作為 Tier-0 embedding 級聯，bundled all-MiniLM-L6-v2、無額外依賴，實現 6.2× per-doc 並行加速。修複 3 個用户反饋的 bug：memory_search 硬編碼 6 命名空間（遺漏 95% 記錄）、graph edges DB 初始化缺失。實驗發現跨編碼器 rerank 在 ArguAna（反論檢索）上反而降低效果（nDCG 0.283 vs dense 0.431），管道自適應禁用。

### 重點
- 3-dataset mean 0.491 排名 4/11；beats BM25 (+0.024)、Contriever、TAS-B；loses SPLADE++ (-0.033)、BGE-large (-0.088)
- ruvector@0.2.27 Tier-0 bundled all-MiniLM-L6-v2、無 sharp 依賴、disk-cache hit；測得 6.2× per-doc 並行加速
- CE rerank 在 ArguAna (counter-argument retrieval) 上有害 (nDCG 0.283 vs dense 0.431)，管道自動禁用；BGE-large 在 NFCorpus 無提升

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.29)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>