---
id: inbox_5d6565dd
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.3.0"
author: "thedotmack"
published_at: 2026-05-21T10:26:08+00:00
fetched_at: 2026-05-26T00:14:50.179406+00:00
content_hash: "738db903a6c5b1ea5c6871d7c11e84d9a2374f4a17cbcc884257cff94ccf4d2e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.3.0

What's New 
 New skills 
 
 design-is ( #2483 ) — audits a design against Dieter Rams' ten "Good design is..." principles. Produces per-principle 0–3 scores with file:line evidence and a NEW / REFINE / REDESIGN verdict, then hands off a ready-to-run /make-plan prompt. 
 weekly-digests ( #2399 ) — produces a chapter-per-ISO-week serial digest of a project's full claude-mem timeline. Sequential subagent pipeline keeps the narrative coherent across 30+ chapters. 
 oh-my-issues ( #2409 ) — root-cause issue clustering. Codifies the consolidation method that turned ~100 open issues into 6 plan-masters during the v13.0.1 cycle. Three modes: cluster pass, triage, bundle. 
 
 Fixes 
 
 fix(mcp): drop duplicate root .mcp.json ( #2411 ) — Claude Code's /doctor was warning "MCP server mcp-search skipped — same command/URL as already-configured mcp-search" for every plugin user. The root copy was vestigial; the plugin's namespaced registration now wins. 
 fix: stop Codex transcript replay after hooks migration ( #2365 ) — disables the default ~/.codex/sessions/**/*.jsonl watch (native Codex hooks are now authoritative). Repairs ~/.codex/config.toml to set [features] hooks = true and [plugins."claude-mem@claude-mem-local"] enabled = true directly. Fixes transcript replay where files discovered after startup ignored startAtEnd and re-injected history. 
 
 Opt back into legacy Codex transcript ingestion with CLAUDE_MEM_CODEX_TRANSCRIPT_INGESTION=true if you depend on the JSONL watcher.