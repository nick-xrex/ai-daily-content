---
id: inbox_474af7b7
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.27"
author: "ruvnet"
published_at: 2026-05-30T22:01:56+00:00
fetched_at: 2026-05-31T00:39:12.263990+00:00
content_hash: "846b9e8e2e31bb232af042a735f94e29727a900f697b857eaa1ecad7c9c9de69"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.27 — RRF ablation harness + HONEST NEGATIVE RESULT (default RRF degrades nDCG@10)

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