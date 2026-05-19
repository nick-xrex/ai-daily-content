---
id: inbox_04fae80c
source: hackernews
source_type: hn
url: "https://github.com/MinishLab/semble"
author: "Bibabomas"
published_at: 2026-05-17T15:37:07+00:00
fetched_at: 2026-05-19T02:02:45.728746+00:00
content_hash: "ad346fb054985d4cb1351bbee86205e53b128d5db5f54c4af640a13eb44fecda"
lang: en
caption_quality: None
raw: true
topics: []
---

# Show HN: Semble – Code search for agents that uses 98% fewer tokens than grep

Hey HN! We (Stephan and Thomas) recently open-sourced Semble. We kept running into the same problem while using Claude Code on large codebases: when the agent can&#x27;t find something directly, it falls back to grep, reading full files or launching subagents. This uses a lot of tokens, and often still misses the relevant code. There are existing tools for this, but they were either too slow to index on demand, needed API keys, or had poor retrieval quality. Semble is our solution for this. It combines static Model2Vec embeddings (using our latest static model: potion-code-16M) with BM25, fused via RRF and reranked with code-aware signals. Everything runs on CPU since there&#x27;s no transformers involved. On our benchmark of ~1250 query&#x2F;document pairs across 63 repos and 19 languages, it uses 98% fewer tokens than grep+read and reaches 99% of the retrieval quality of a 137M-parameter code-trained transformer, while being ~200x faster. Main features: - Token-efficient: 98% fewer tokens than grep+read - Fast: ~250ms to index a typical repo on our benchmark, ~1.5ms per query on CPU (very large repos may take longer) - Accurate: 0.854 NDCG@10, 99% of the best transformer setup we tested - MCP server: drop-in for Claude Code, Cursor, Codex, OpenCode - Zero config: no API keys, no GPU, no external services Install in Claude Code with:
claude mcp add semble -s user -- uvx --from &quot;semble[mcp]&quot; semble Or check our README for other installation instructions, benchmarks, and methodology: Semble: https:&#x2F;&#x2F;github.com&#x2F;MinishLab&#x2F;semble Benchmarks: https:&#x2F;&#x2F;github.com&#x2F;MinishLab&#x2F;semble&#x2F;tree&#x2F;main&#x2F;benchmarks Model: https:&#x2F;&#x2F;huggingface.co&#x2F;minishlab&#x2F;potion-code-16M Let us know if you have any feedback or questions!