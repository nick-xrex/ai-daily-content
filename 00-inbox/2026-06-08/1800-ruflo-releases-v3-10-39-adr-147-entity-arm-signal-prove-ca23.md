---
id: inbox_63e724cc
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.39"
author: "ruvnet"
published_at: 2026-06-08T17:36:55+00:00
fetched_at: 2026-06-08T18:00:51.509972+00:00
content_hash: "ca23814014ec1d405a89f625401e6e4cb0bff31adb74ffa7d4c26ca0b7b37fed"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.39 — ADR-147 entity arm + signal provenance

First implementation landed from the dream-cycle research cluster ( #2316 - #2324 ). Adds entity matching as a third RRF arm in hybridSearch alongside dense (HNSW/RaBitQ) and sparse (FTS5/BM25), plus per-result signal provenance. 
 What's new 
 @claude-flow/memory 3.0.0-alpha.20 — entity arm + signal provenance in the hybridSearch controller: 
 
 entity-tagger.ts — regex extractor for emails, URLs, file paths (POSIX + Windows), quoted phrases, proper-noun 2-grams. Deliberately conservative: false negatives OK, false positives would dilute RRF. 
 hybridSearch now runs three arms in parallel: dense + sparse + entity (per-token keyword scan, gated on extractEntities(query).length &gt; 0 ). Empty entity set drops the arm rather than passing [] to dilute fusion. 
 signals: ('vector' | 'bm25' | 'entity')[] on every fused result. Computed by pre-fusion set membership; lets callers debug which arms surfaced an entry without re-running the search. 
 
 Capability smoke (end-to-end against built dist) 
 Corpus: 30 generic "authentication" entries + 1 "Alice Smith" needle. Query: "Alice Smith authentication" : 
 score=0.0477 signals=["vector","bm25","entity"] key=alice-needle ← #1
score=0.0323 signals=["vector","bm25"] key=generic-1
score=0.0323 signals=["vector","bm25"] key=generic-0
score=0.0313 signals=["vector","bm25"] key=generic-3
score=0.0301 signals=["vector","bm25"] key=generic-2
 
 Alice ranks #1 with full triplet provenance — runners-up only fire on vector + sparse. ~47% RRF score boost from the entity signal. 
 Packages 
 
 
 
 Package 
 Old 
 New 
 Tags 
 
 
 
 
 @claude-flow/memory 
 3.0.0-alpha.19 
 3.0.0-alpha.20 
 latest, alpha, v3alpha 
 
 
 @claude-flow/cli 
 3.10.38 
 3.10.39 
 latest, alpha, v3alpha 
 
 
 claude-flow 
 3.10.38 
 3.10.39 
 latest, alpha, v3alpha 
 
 
 ruflo 
 3.10.38 
 3.10.39 
 latest, alpha, v3alpha 
 
 
 
 @claude-flow/cli 's @claude-flow/memory dep pinned to ^3.0.0-alpha.20 so wrapper users get the entity arm automatically. v3/pnpm-lock.yaml regen included (lesson from #2311 — bumping a workspace dep without lockfile regen breaks pnpm install --frozen-lockfile ). 
 What this implements vs the dream-cycle ADR 
 ADR-147 ( #2317 ) split the work as P1 "wire FTS5 + RRF fusion" and P2 "entity arm + provenance". The investigation found P1 was already shipped in controller-registry.ts:713 before the ADR was filed — applyRRF(k=60) + applyMMR(λ=0.7) over dense + sparse was already in. This release lands the actual gap, P2 . 
 Tracking note for the dream-cycle process posted on #2324 . 
 Tests 
 
 12 new entity-tagger.test.ts (regex pinning — generic prose returns empty, and/or → empty, "a" over "b" → empty, single capitalized words → empty) 
 2 new graceful-retrieval.test.ts ADR-147 assertions (signal provenance on every fused result; needle-in-haystack) 
 Full memory suite: 416/420 (4 pre-existing Windows-env failures in agent-memory-scope , auto-memory-bridge , benchmark — untouched files) 
 
 Out of scope (follow-ups) 
 
 Dedicated SQL entity index — current per-entity searchKeyword calls are fine for typical query entity counts (1-3); unbounded if a query mentions 20+. A future ADR can add an entity_index table for hard-bound latency. 
 Async writes by default (ADR-147 P3) — orthogonal; consolidator already handles HNSW background rebuild. 
 LoCoMo benchmark publication (ADR-147 P4) — needs harness wiring + dataset access; separate workstream.