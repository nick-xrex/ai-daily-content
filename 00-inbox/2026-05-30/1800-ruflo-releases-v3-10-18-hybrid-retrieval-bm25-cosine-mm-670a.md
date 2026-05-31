---
id: inbox_a177296e
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.18"
author: "ruvnet"
published_at: 2026-05-30T17:23:52+00:00
fetched_at: 2026-05-30T18:00:42.577351+00:00
content_hash: "670a36c366265f6dd8365d6e290d7263aa2785eea84908a9eeeabb8ce88bfb64"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.18 — hybrid retrieval (BM25 + cosine + MMR) — 0% → 50% top-1 relevance

What ships 
 Hybrid retrieval (BM25 + cosine + MMR) plus outcome signal for the 
pretrain harvester. Closes the relevance gap that ADR-077 exposed: cosine-only 
search was returning plausible-but-off-topic results because the bridge ONNX 
bi-encoder gets distracted on small corpora by IDF-cheap shared tokens. 
 The actual win 
 Measured on this checkout (N=385 patterns, 10 queries, real bridge ONNX 
embedder — same setup ADR-077 used): 
 
 
 
 Metric 
 Cosine (pre-3.10.18) 
 Hybrid (3.10.18) 
 Δ 
 
 
 
 
 Top-1 hit rate (RELEVANCE) 
 0% 
 50% 
 +50pp 
 
 
 Top-3 hit rate (RELEVANCE) 
 0% 
 70% 
 +70pp 
 
 
 MRR@3 
 0.000 
 0.583 
 +0.583 
 
 
 Top-1 diversity 
 100% 
 80% 
 -20pp 
 
 
 Avg query latency 
 28.7 ms 
 40.6 ms 
 +11.9 ms 
 
 
 
 Cosine was returning 0% relevant top-3 results — finding "something" but never 
the right thing. Hybrid lands a relevant top-1 50% of the time, top-3 70%. 
 What changed 
 
 
 src/memory/hybrid-retrieval.ts — pure functions, no deps: 
 tokenize , buildCorpusStats , bm25Score , normalise , hybridScores , 
 cosineSim , mmrRerank . 21 unit tests covering edge cases. 
 
 
 neural_patterns MCP tool — new search params: 
 
 mode: 'hybrid' | 'cosine' (default hybrid; cosine preserved for A/B) 
 alpha — cosine weight in [0,1] (default 0.6) 
 mmrLambda — 1.0 = pure relevance, 0.0 = pure diversity (default 0.5) 
 limit — top-K (default 10, max 100) 
 Response includes hybridScore , cosineScore , bm25Score , mmrScore 
so callers can inspect why a result ranked where it did 
 
 
 
 Pattern.content field — neural store now persists source text (cap 
4096 chars). BM25 needs tokens to score against. Backwards compatible: 
pre-3.10.18 patterns fall back to name for BM25 tokenisation. 
 
 
 Outcome signal in pretrain harvester — detects: 
 
 reverted — later commit's subject is Revert "&lt;this subject&gt;" 
 hotfixed — later commit (within window) shares ≥50% files AND has 
fix/hotfix/patch in subject 
 Verdict mix in summary.feed.verdictMix ; original outcome in 
 metadata.outcomeVerdict on each trajectory 
 
 
 
 Reproduce 
 git clone https://github.com/ruvnet/ruflo &amp;&amp; cd ruflo
npm install &amp;&amp; ( cd v3/@claude-flow/cli &amp;&amp; npx tsc -b )

 # Unit tests (no I/O) — 21 + 7 tests 
( cd v3/@claude-flow/cli &amp;&amp; npx vitest run __tests__/hybrid-retrieval.test.ts __tests__/pretrain-from-github.test.ts )

 # A/B benchmark 
node v3/@claude-flow/cli/scripts/pretrain-from-github.mjs
node v3/@claude-flow/cli/scripts/benchmark-pretrained-retrieval.mjs # hybrid (default) 
HYBRID=0 node v3/@claude-flow/cli/scripts/benchmark-pretrained-retrieval.mjs # cosine baseline 
 Honest limits 
 
 N=385 with 10 queries is small. The relevance metric is regex-over-subject — 
a labelled held-out set would be stronger. Direction is robust; magnitude 
could move on a different corpus. 
 Hybrid is 40% slower per query (28.7 → 40.6 ms). Still &lt;50 ms but worth 
budgeting on hot paths. Cosine-only mode preserved for callers who need it. 
 This checkout has zero reverts/hotfixes in the 200 most recent commits, so 
the outcome detector emits a clean success=200 distribution. Detector is 
unit-tested; the empty count reflects a clean recent history. 
 
 What's next 
 
 Cross-encoder reranker (3.11.0, MINOR — new dep): standard SOTA pattern 
for another +0.05-0.15 MRR 
 Learned distiller (paper's 11× compression target): #2241 round-D 
 Negative-reward propagation on retrieval miss : needs agent-level success 
attribution we don't yet emit reliably 
 
 Install 
 npx ruflo@3.10.18 # or @latest, @alpha, @v3alpha (all aligned) 
 Full ADR: v3/docs/adr/ADR-078-hybrid-retrieval-and-outcome-signal.md