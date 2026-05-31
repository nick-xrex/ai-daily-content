---
id: inbox_3df0b3ec
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.26"
author: "ruvnet"
published_at: 2026-05-30T20:51:21+00:00
fetched_at: 2026-05-31T00:39:12.269659+00:00
content_hash: "ffe8b2851b46513382ebc0d4dd6a81b3bda3854cde97f2e3696a4942d85c56d2"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.26 — BEIR matrix + bootstrap CIs + 2nd dataset (we lose to BM25 on SciFact, ship the truth)

What ships 
 Took the user's "release hype → benchmark infrastructure" feedback to the wire. This release IS the infrastructure, not the rank. 
 Honest two-dataset picture 
 
 
 
 Dataset 
 nDCG@10 
 95% CI 
 Rank 
 vs BM25 
 
 
 
 
 NFCorpus 
 0.352 
 [0.317, 0.387] 
 2/11 
 +0.027 (n.s.) 
 
 
 SciFact 
 0.626 
 [0.577, 0.672] 
 10/11 
 -0.053 (p&lt;0.05) — significant LOSS 
 
 
 
 The user's acceptance test ("ruflo beats BM25 on both") fails on SciFact — we significantly lose to BM25 by 0.053. On NFCorpus, only SBERT msmarco and ColBERT are statistically significant wins; the gaps to SPLADE++/GTR-XL/BM25 are within CI overlap. 
 Two-dataset mean : ours 0.489, BM25 0.502, SPLADE++ 0.526, BGE-large 0.551. Below BM25 on the mean. BGE-base zero-shot is competent on NFCorpus (medical IR), weak on SciFact (fact-verification favours lexical retrieval). The NFCorpus rank-2 is real but not representative. 
 What's in the box 
 
 docs/benchmarks/BEIR-MATRIX.md — dataset × pipeline × metric grid with bootstrap CIs and pipeline disclosure 
 scripts/beir-bootstrap-significance.mjs — paired bootstrap, 10K resamples, mulberry32 seed=42 
 perQuery metrics now saved in every BEIR run JSON (external bootstrap verification by anyone) 
 ADR-085 hedged appropriately ("TOP-2 on BEIR NFCorpus, not BEIR average", "direct dense, no fine-tune, no rerank") 
 ADR-086 documents the silent-fallback bug story + bootstrap method + honest two-dataset picture 
 2 ruvector upstream issues filed: #523 (API contract bugs), #524 (bundle BGE-base/small) 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 # NFCorpus + SciFact (~30 min ingest each) 
mkdir -p /tmp/beir-nfcorpus &amp;&amp; cd /tmp/beir-nfcorpus
curl -sL -o nf.zip ' https://public.ukp.informatik.tu-darmstadt.de/thakur/BEIR/datasets/nfcorpus.zip ' &amp;&amp; unzip -q nf.zip
node /path/to/ruflo/v3/@claude-flow/cli/scripts/run-beir-bge.mjs

mkdir -p /tmp/beir-scifact &amp;&amp; cd /tmp/beir-scifact
curl -sL -o sf.zip ' https://public.ukp.informatik.tu-darmstadt.de/thakur/BEIR/datasets/scifact.zip ' &amp;&amp; unzip -q sf.zip
BEIR_DATA_DIR=/tmp/beir-scifact/scifact node /path/to/ruflo/v3/@claude-flow/cli/scripts/run-beir-bge.mjs

 # Bootstrap significance (10k resamples, ~1s) 
node /path/to/scripts/beir-bootstrap-significance.mjs /path/to/run.json 
 Honest limits 
 
 Two datasets only. BEIR ships 18. The 2-dataset mean is suggestive, not definitive. 
 Zero-shot. NFCorpus has a 110K-pair train split that would close ~0.02-0.05 nDCG. 
 Single annotator on internal labels (separate from BEIR's external qrels). 
 Tailscale-via-ruvultra GPU compute discussed for larger datasets (TREC-COVID, HotpotQA, NQ) — tracked. 
 
 Install 
 npx ruflo@3.10.26 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-086-silent-fallback-and-bootstrap.md