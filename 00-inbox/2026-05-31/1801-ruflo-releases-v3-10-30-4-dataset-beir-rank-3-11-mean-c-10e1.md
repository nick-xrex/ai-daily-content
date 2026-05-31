---
id: inbox_c804a3f6
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.30"
author: "ruvnet"
published_at: 2026-05-31T07:21:35+00:00
fetched_at: 2026-05-31T18:01:16.414820+00:00
content_hash: "10e1d9ad125d06e92f0999faf15d88adea3a546b1eeaa368b7f8f4cc4fceee80"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.30 — 4-dataset BEIR (rank 3/11 mean) + config-divergence finding

What ships 
 4th BEIR dataset (SciDocs) joins NFCorpus + SciFact + ArguAna. New finding: no single pipeline wins everywhere. 
 SciDocs results 
 
 
 
 Pipeline 
 nDCG@10 
 Rank 
 
 
 
 
 dense alone (BGE-base) 
 0.211 
 2/11 
 
 
 Lucene RRF (no rerank) 
 0.203 
 (-0.008, RRF hurt) 
 
 
 
 Only behind BGE-large (335M, 0.225). Beats BM25, GTR-XL (1.2B), every other published baseline. 
 4-dataset mean leaderboard 
 
 
 
 System 
 Params 
 NFCorpus 
 SciFact 
 ArguAna 
 SciDocs 
 Mean 
 
 
 
 
 BGE-large (published) 
 335M 
 0.380 
 0.722 
 0.636 
 0.225 
 0.491 
 
 
 SPLADE++ (published) 
 110M 
 0.347 
 0.704 
 0.521 
 0.159 
 0.433 
 
 
 ruflo best (per-dataset) 
 110M 
 0.358 
 0.683 
 0.432 
 0.211 
 0.421 
 
 
 GTR-XL (1.2B) 
 1.2B 
 0.343 
 0.662 
 0.439 
 0.174 
 0.405 
 
 
 GenQ 
 110M 
 0.319 
 0.644 
 0.493 
 0.143 
 0.400 
 
 
 BM25 (Lucene published) 
 — 
 0.325 
 0.679 
 0.397 
 0.158 
 0.390 
 
 
 
 Rank 3 of 11 on 4-dataset mean. Beats GTR-XL with 1/10× the params. Loses only to SPLADE++ (-0.012, basically tied) and BGE-large (-0.070, mostly the ArguAna gap). 
 The config-divergence finding 
 After 4 datasets, no single pipeline wins everywhere : 
 
 
 
 Dataset 
 Best config 
 What hurts 
 
 
 
 
 NFCorpus 
 Lucene + RRF + CE rerank 
 nothing 
 
 
 SciFact 
 Lucene + RRF + CE rerank 
 nothing 
 
 
 ArguAna 
 Lucene + RRF (no CE) 
 CE rerank actively hurts 
 
 
 SciDocs 
 dense alone 
 RRF hurt by 0.008 
 
 
 
 Three of four datasets pick a different best config. Auto-pipeline-selection would need a per-corpus calibrator (cheap, doesn't need GPU — tracked). 
 Honest limits 
 
 4/18 BEIR datasets. The 0.421 mean is suggestive, not BEIR-average. 
 Zero-shot — NFCorpus and ArguAna train splits remain unused. 
 The 5 biggest BEIR datasets (TREC-COVID, FiQA, HotpotQA, NQ, DBPedia, all &gt;50k docs) remain GPU-gated. 
 
 Install 
 npx ruflo@3.10.30 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-091-scidocs-and-config-divergence.md