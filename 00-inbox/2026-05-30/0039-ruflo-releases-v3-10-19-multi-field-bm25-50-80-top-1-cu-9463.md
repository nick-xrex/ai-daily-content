---
id: inbox_a4094e19
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.19"
author: "ruvnet"
published_at: 2026-05-30T18:08:50+00:00
fetched_at: 2026-05-31T00:39:12.285707+00:00
content_hash: "9463a084b5d649000b4ac7d6672dec7994682e47a9b1f6ee9d89982338beb9a8"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.19 — multi-field BM25 — 50% → 80% top-1 (cumulative 0% → 80% since 3.10.17)

What ships 
 Multi-field BM25 (subject 3× over body) and an opt-in type penalty for 
meta-commits. Both improvements come with a full ablation table — and the 
ablation drove a real decision (type penalty defaults to OFF because it 
 hurts top-1 when multi-field BM25 is doing the heavy lifting). 
 The cumulative win (3.10.17 cosine → 3.10.19) 
 
 
 
 Metric (N=385, 10 queries) 
 3.10.17 cosine 
 3.10.18 hybrid 
 3.10.19 
 Δ since cosine 
 
 
 
 
 Top-1 hit rate 
 0% 
 50% 
 80% 
 +80pp 
 
 
 Top-3 hit rate 
 0% 
 70% 
 80% 
 +80pp 
 
 
 MRR@3 
 0.000 
 0.583 
 0.800 
 +0.800 
 
 
 Top-1 diversity 
 100% 
 80% 
 100% 
 0pp (recovered) 
 
 
 Avg query latency 
 28.7 ms 
 40.6 ms 
 39.0 ms 
 +10 ms 
 
 
 
 The ablation that drove the decisions 
 
 
 
 Configuration 
 Top-1 
 Top-3 
 MRR@3 
 
 
 
 
 Cosine baseline 
 0/10 
 0/10 
 0.000 
 
 
 Single-field BM25, no penalty (~3.10.18) 
 5/10 
 7/10 
 0.583 
 
 
 Single-field BM25 + type penalty 0.5 
 7/10 
 7/10 
 0.700 
 
 
 Multi-field BM25 3:1, no penalty (3.10.19 default) 
 8/10 
 8/10 
 0.800 
 
 
 Multi-field BM25 3:1 + type penalty 0.5 
 7/10 
 8/10 
 0.750 
 
 
 
 Multi-field BM25 alone wins. Adding the type penalty hurts top-1 because 
some real work commits start with Merge feat/... and get falsely demoted. 
The penalty stays in the codebase as an opt-in for callers with different 
commit conventions. 
 What changed in code 
 
 
 multiFieldBM25() in src/memory/hybrid-retrieval.ts — treats 
pattern subject ( name ) and body ( content ) as separate fields with 
independent IDF distributions. Defaults: subjectWeight=3.0, bodyWeight=1.0 . 
 
 
 typePenalty() + META_COMMIT_REGEX — exported but defaults to no-op 
( typePenaltyFactor=1.0 ). Callers can pass 0.5 for aggressive 
meta-commit suppression. 
 
 
 neural_patterns MCP tool — new params: subjectWeight , 
 bodyWeight , typePenaltyFactor . Response shape unchanged. 
 
 
 39 unit tests in __tests__/hybrid-retrieval.test.ts (was 21 in 
3.10.18); covers ranking, weight collapse cases, regex coverage, factor 
bounds, undefined-name safety. 
 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 # Unit tests 
( cd v3/@claude-flow/cli &amp;&amp; npx vitest run __tests__/hybrid-retrieval.test.ts __tests__/pretrain-from-github.test.ts )

 # Live A/B 
 cd v3/@claude-flow/cli
node scripts/pretrain-from-github.mjs
node scripts/benchmark-pretrained-retrieval.mjs # 3.10.19 default → 80% top-1 
HYBRID=0 node scripts/benchmark-pretrained-retrieval.mjs # cosine baseline → 0% top-1 
 Honest limits 
 
 N=385, 10 queries is small. Relevance metric is regex-over-commit-subject — 
a labelled held-out corpus would tighten confidence intervals. Direction 
(0% → 80% top-1) is robust to noise. 
 Subject:body 3:1 weight chosen by inspection, not grid-search. Future ADR 
could grid-search on a wider corpus. 
 Type penalty regex is hand-curated for ruflo's conventions. Other repos 
with different conventions need their own regex — the function takes one 
as a parameter. 
 
 What's next 
 
 Cross-encoder reranker (3.11.0, MINOR — new dep): paper-proven path 
for closing the remaining 80% → 100% top-1 gap 
 Learned distiller (paper's 11× compression): #2241 round-D 
 Grid-search for subject/body weights on a wider held-out corpus 
 
 Install 
 npx ruflo@3.10.19 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-079-multifield-bm25-and-type-penalty.md