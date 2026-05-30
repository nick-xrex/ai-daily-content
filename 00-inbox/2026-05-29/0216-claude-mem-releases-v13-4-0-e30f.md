---
id: inbox_afe1e220
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.4.0"
author: "thedotmack"
published_at: 2026-05-29T18:35:01+00:00
fetched_at: 2026-05-30T02:16:30.802003+00:00
content_hash: "e30fdefce633d8d45db2ba45025eb78b8bf5c1867aa4fddb6dc10a2438ee6752"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.4.0

v13.4.0 — Defect backlog clearance + provider extensibility 
 Clears a large defect backlog (plans 01–11 plus standalone fixes) and adds provider configurability. Test suite moved 46 → 0 failing and typecheck 24 → 0 errors over the branch. 
 Features 
 
 Configurable OpenAI-compatible base URL for the OpenRouter provider ( CLAUDE_MEM_OPENROUTER_BASE_URL ) — point claude-mem at DeepSeek, LM Studio, or any custom OpenAI-compatible endpoint. 
 
 Fixes (highlights) 
 
 Spawn contract (plan-02): canonical ${CLAUDE_PLUGIN_ROOT} resolution + Windows spawn fixes (codex.cmd, chroma-mcp cmd.exe quoting). 
 Worker lifecycle (plan-03): Windows PID-reuse start-token guard. 
 Output fidelity (plan-11): commit-hash verification before persist; null- cwd no longer strips every hex string from summaries. 
 SQLite self-healing: schema repair via sqlite3 .recover ; close DB handle on repair error paths (no leaked write lock). 
 SessionMessageBuffer: clear() now also resets the dedup set, so a previously-seen toolUseId can re-enter. 
 Standalone: project name, dot-path encoding, path-match, CLAUDE.md denylist. 
 
 CI / tests 
 
 New CI workflow (typecheck · build · test · bundle-size + docker pg+valkey e2e) made green; removed npm-lockfile dependency to match the repo's no-committed-lockfile convention. 
 Fixed mock.module logger leakage across test files and guarded sqlite3 .recover capability so CI runs cleanly. 
 
 Full diff: #2701