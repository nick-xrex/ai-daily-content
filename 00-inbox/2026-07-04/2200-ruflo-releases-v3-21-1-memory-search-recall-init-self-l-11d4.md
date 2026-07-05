---
id: inbox_e7a1a69b
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.21.1"
author: "ruvnet"
published_at: 2026-07-04T15:06:45+00:00
fetched_at: 2026-07-04T22:00:22.955656+00:00
content_hash: "11d47712acc385f256f8a3985b057e0593ba4b5b61895fd37c10b099dcf19eff"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.21.1 — memory search recall + init self-learning fixes

Two external-reported regression fixes. 
 Fixed 
 
 #2558 — memory search broken (keyword recall random, HNSW index 0 vectors). Two defects: the Phase-2 BM25 fusion silently dropped the keyword-coverage floor (IDF collapses on small corpora → docs containing the query word scored below threshold), and WAL-mode writes were never checkpointed so WAL-blind readers saw 0 vectors. Fix: coverage floor + recall-friendly fusion + wal_checkpoint on store + accurate total_vectors . Search now recalls confirmed-stored entries (targeted, not a dump). 169/169 memory suite. 
 #2545 — npx ruflo init left self-learning a silent no-op. @claude-flow/memory (optionalDependency) lands in the npx cache, off the project's node_modules walk-up, so the auto-memory hook never resolved it. Fix: init records the resolved path in a .claude-flow/memory-package.json sidecar; hook reads it first and now fails LOUD when memory is genuinely absent; doctor --fix repairs it. 
 
 PRs: #2567 , #2564