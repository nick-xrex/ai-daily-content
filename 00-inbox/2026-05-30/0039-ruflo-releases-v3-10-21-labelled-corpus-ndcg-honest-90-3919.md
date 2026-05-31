---
id: inbox_be5126e3
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.21"
author: "ruvnet"
published_at: 2026-05-30T18:37:54+00:00
fetched_at: 2026-05-31T00:39:12.282625+00:00
content_hash: "39197affbda6bc9d746e4a8d7ecd318a9f169e1cc416d01b10e3a970c946d630"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.21 — labelled corpus + nDCG: honest 90% label top-1, 0.913 nDCG@3

What ships 
 Labelled held-out corpus + nDCG/precision metrics replace the regex-over-subject 
relevance proxy used in ADRs 077-080. Honest SOTA needs honest measurement. 
 The honest-measurement finding 
 The regex proxy was both over- and under-reporting. When the same 4 configs run 
through the labelled corpus, the truth shifts in both directions: 
 
 
 
 Config 
 Regex top-1 
 Labelled top-1 
 Direction 
 
 
 
 
 Hybrid (3.10.19) 
 80% 
 90% 
 regex under -reported 
 
 
 Hybrid + Rerank (3.10.20) 
 90% 
 80% 
 regex over -reported 
 
 
 
 Real numbers (labelled metric, the new canonical) 
 
 
 
 Metric 
 3.10.17 cosine 
 3.10.19 hybrid 
 3.10.20 +rerank 
 
 
 
 
 Label top-1 hit rate 
 0% 
 90% 
 80% 
 
 
 Label top-3 hit rate 
 0% 
 90% 
 100% 
 
 
 Label MRR@3 
 0.000 
 0.900 
 0.883 
 
 
 Label precision@3 
 0.000 
 0.400 
 0.667 
 
 
 Label nDCG@3 
 0.000 
 0.900 
 0.913 
 
 
 Avg query latency 
 29 ms 
 42 ms 
 977 ms (opt-in) 
 
 
 
 The cross-encoder trade-off, now visible 
 The cross-encoder optimises for finding all relevant docs (precision@3 0.40 → 0.67) 
while hybrid alone optimises for finding THE right doc first (top-1 80% → 90%). 
Neither is universally better — it depends on whether the caller wants the single 
best match or a relevant set. 
 Default rerank: false is still correct for top-1-first callers; opt-in 
 rerank: true is now better-documented for richer top-K consumers. 
 Why the regex was wrong 
 
 Under-reporting : for "self-learning wiring task-completed pretrain" , the regex missed the issue title "Self-learning reports success but persists nothing" — exactly the right answer — because no hyphenation variant matched. 
 Over-reporting : for "how was the Opus model alias fixed" , the regex matched the release-bump chore(release): bump 3.10.10 → 3.10.11 (4-issue bug cluster) because its body mentioned Opus, but the release commit isn't the work. 
 
 What changed in code 
 
 QUERIES array gains expectedSubstrings: string[] — hand-curated labels per query, encoded directly in the bench script. 
 isRelevant(name, substrings) helper — case-insensitive substring match (any-of semantics). 
 ndcgAtK(rankedRelevance, k) — standard binary-relevance nDCG with ideal-DCG normalisation. Smoke-checked against canonical fixture: [T,T,T]→1.0 , [F,F,T]→0.5 , [F,T,F]→0.631 , [T,F,T]→0.920 . 
 6 new metrics in summary JSON + console output (label_top1HitRate, label_top3HitRate, label_mrr3, label_precision3, label_ndcg3, label_ndcg5). 
 Regex proxy metrics preserved under "regex proxy" labels so historical ADR 077-080 numbers stay reproducible. 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc )

 # Pretrain (415 patterns) 
node v3/@claude-flow/cli/scripts/pretrain-from-github.mjs

 # All four configs through the labelled bench 
( cd v3/@claude-flow/cli &amp;&amp; {
 HYBRID=0 BENCH_NO_WRITE=1 node scripts/benchmark-pretrained-retrieval.mjs | grep -E " ^(Top|MRR|Precision|nDCG) " 
 BENCH_NO_WRITE=1 node scripts/benchmark-pretrained-retrieval.mjs | grep -E " ^(Top|MRR|Precision|nDCG) " 
 RERANK=1 BENCH_NO_WRITE=1 node scripts/benchmark-pretrained-retrieval.mjs | grep -E " ^(Top|MRR|Precision|nDCG) " 
}) 
 Honest limits (acknowledged in ADR) 
 
 N=10 queries is still small; 50-200 would tighten confidence intervals. 
 Binary relevance — graded scheme ( exact=3, close=2, related=1 ) would distinguish "perfect" from "passable". 
 Single annotator — I curated the labels; inter-annotator agreement is a nice-to-have. 
 No truly held-out test split — labels were authored after seeing outputs, so subsequent tuning against this set has confirmation bias risk. New queries are the right next step. 
 
 What's next 
 
 Larger labelled corpus (50-200 queries) 
 Graded relevance 
 Larger cross-encoder (ms-marco-MiniLM-L-12-v2) if quality &gt; latency 
 Learned distiller ( #2241 round-D) 
 
 Install 
 npx ruflo@3.10.21 # latest / alpha / v3alpha all aligned 
 Full ADR: v3/docs/adr/ADR-081-labelled-corpus-and-ndcg.md