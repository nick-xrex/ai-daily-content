---
id: inbox_9a055d80
date: 2026-05-30
source_ref: "[[00-inbox/2026-05-30/0039-ruflo-releases-v3-10-25-top-2-on-beir-nfcorpus-ndcg-10-4f6d]]"
title: "v3.10.25 — TOP-2 on BEIR NFCorpus (nDCG@10 0.352, direct BGE dense, no fine-tune/rerank)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.25
source: ruflo-releases
published_at: 2026-05-30T20:24:31+00:00
fetched_at: 2026-05-31T00:46:13.805619+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.25 建立可重複的 BEIR NFCorpus 基準。直接 BGE-base-en-v1.5（110M 參數）路徑達 nDCG@10 0.352（rank 2/11），僅 0.028 差於 BGE-large（335M）。關鍵發現：發現環境缺陷，embedding 路徑因 sharp/libvips darwin-arm64 問題無聲降級為 hash 回退，但 neural store 報告 _realEmbedding: true。新建 BGE 直接路徑移除 sharp 依賴，繞過該缺陷。包含 on-disk embedding cache 與 per-query 指標存儲。"
key_points:
  - "BGE-base (110M) nDCG@10 = 0.352 vs BGE-large (335M) = 0.380，僅 0.028 差距，小模型競爭力強"
  - "發現無聲 embedding 降級缺陷：sharp/libvips 問題導致每次調用拋異常被吞噬，系統無聲降格為純 BM25"
  - "新路徑 @xenova/transformers AutoTokenizer + AutoModel 直接加載 BGE，移除影像預處理不必要的依賴"
tags: [embedding-bug, bge-model, direct-dense, reproducibility]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.25 — TOP-2 on BEIR NFCorpus (nDCG@10 0.352, direct BGE dense, no fine-tune/rerank)

Ruflo v3.10.25 建立可重複的 BEIR NFCorpus 基準。直接 BGE-base-en-v1.5（110M 參數）路徑達 nDCG@10 0.352（rank 2/11），僅 0.028 差於 BGE-large（335M）。關鍵發現：發現環境缺陷，embedding 路徑因 sharp/libvips darwin-arm64 問題無聲降級為 hash 回退，但 neural store 報告 _realEmbedding: true。新建 BGE 直接路徑移除 sharp 依賴，繞過該缺陷。包含 on-disk embedding cache 與 per-query 指標存儲。

### 重點
- BGE-base (110M) nDCG@10 = 0.352 vs BGE-large (335M) = 0.380，僅 0.028 差距，小模型競爭力強
- 發現無聲 embedding 降級缺陷：sharp/libvips 問題導致每次調用拋異常被吞噬，系統無聲降格為純 BM25
- 新路徑 @xenova/transformers AutoTokenizer + AutoModel 直接加載 BGE，移除影像預處理不必要的依賴

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.25)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ruflo 3.10.25 — reproducible BEIR NFCorpus benchmark, nDCG@10 0.352, top-2 against listed public baselines 
 We now have a reproducible BEIR benchmark harness, run JSONs, per-query metrics 
(in 3.10.26), and a clean direct BGE dense path. 
 First public result: BEIR NFCorpus 
 nDCG@10 = 0.352 using BGE-base-en-v1.5 (110M params) via the direct 
dense path (no fine-tuning, no hybrid BM25+dense fusion, no cross-encoder 
reranker). Internal hybrid pipeline is isolated from this comparison so the 
dense-vs-dense numbers stay honest. 
 
 
 
 Rank 
 Method 
 Params 
 nDCG@10 
 
 
 
 
 1 
 BGE-large-v1.5 (listed) 
 335M 
 0.380 
 
 
 2 
 ruflo + BGE-base-en-v1.5 ← us 
 110M 
 0.352 
 
 
 3 
 SPLADE++ 
 110M 
 0.347 
 
 
 4 
 GTR-XL 
 1.2B 
 0.343 
 
 
 5 
 DocT5query / Contriever 
 — 
 0.328 
 
 
 7 
 BM25 (Lucene) 
 — 
 0.325 
 
 
 8 
 TAS-B / GenQ 
 — 
 0.319 
 
 
 10 
 ColBERT 
 110M 
 0.305 
 
 
 11 
 SBERT msmarco 
 110M 
 0.272 
 
 
 
 This is top-2 on BEIR NFCorpus , NOT "top-2 on BEIR." BEIR is an 18-dataset 
suite; NFCorpus is one dataset. The broader BEIR average requires TREC-COVID, 
FiQA, ArguAna, HotpotQA, NQ, etc. SciFact (2nd dataset) is queued. 
 The more important part — the audit trail 
 We found and fixed a real environment bug where the embedding path could 
silently degrade into hash fallback because of a sharp / libvips issue on 
darwin-arm64. The neural store reported _realEmbedding: true because the 
 import succeeded — but per-call embeds threw and got swallowed by an inner 
catch. The pure-BM25 path (with broken random cosine) was carrying the entire 
"hybrid" signal undetected. 
 The new path bypasses that dependency by loading BGE directly through 
 @xenova/transformers 's AutoTokenizer + AutoModel . Text bi-encoders 
don't need image preprocessing; sharp is a transitive dep that's never 
needed for retrieval. 
 What changed in code 
 
 src/memory/bge-embedder.ts — lazy-loaded singleton, supports 
bge-small (33M, 384-dim), bge-base (110M, 768-dim, default), 
bge-large (335M, 1024-dim). CLS-token pooling + L2 normalisation 
per BAAI spec. 
 scripts/run-beir-nfcorpus.mjs — hybrid-pipeline harness; with the 
embedder broken this collapses to pure-BM25 (measured 0.289 vs published 
BM25 0.325). 
 scripts/run-beir-bge.mjs — direct-dense BEIR runner, on-disk 
embedding cache, dataset auto-detect. 
 docs/benchmarks/BEIR-MATRIX.md — public benchmark tracking page 
(added in 3.10.26). 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

mkdir -p /tmp/beir-nfcorpus &amp;&amp; cd /tmp/beir-nfcorpus
curl -sL -o nfcorpus.zip ' https://public.ukp.informatik.tu-darmstadt.de/thakur/BEIR/datasets/nfcorpus.zip ' 
unzip -q nfcorpus.zip

 # BGE-base direct dense (one-time ~25min ingest + ~2min full eval) 
node /path/to/v3/@claude-flow/cli/scripts/run-beir-bge.mjs
 # → nDCG@10 0.352, rank 2/11 against listed baselines 

 # Cached subsequent runs (~2 min) 
SKIP_INGEST=1 node /path/to/scripts/run-beir-bge.mjs 
 Honest limits 
 
 One BEIR dataset measured. SciFact in progress; broader BEIR average 
tracked. 
 Zero-shot, no fine-tuning. NFCorpus has a 110K-pair train split that 
could fine-tune for an additional ~0.02-0.05 nDCG. 
 The 0.005 gap to SPLADE++ is small. Paired bootstrap CI shipping 
in 3.10.26 will determine if it's statistically significant. 
 The _realEmbedding: true lie in neural-tools.ts is bypassed, not 
fixed. BGE direct-API path is the workaround; the underlying flag bug 
is tracked. 
 
 Install 
 npx ruflo@3.10.25 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-085-beir-public-benchmark.md

</details>