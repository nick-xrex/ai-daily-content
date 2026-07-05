---
id: inbox_2112e903
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.10.0"
author: "thedotmack"
published_at: 2026-07-04T02:17:18+00:00
fetched_at: 2026-07-04T22:00:23.678325+00:00
content_hash: "010bcf81e6eb38d4cb8df94f01116d6156e621a068eee743181456bfc9ce652a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.10.0

Antigravity CLI support, Gemini CLI removed 
 Google deprecated Gemini CLI's free/individual tier (cutoff June 18, 2026) in favor of Antigravity CLI , the official successor announced May 19, 2026. This release migrates claude-mem accordingly. 
 Removed 
 
 Gemini CLI host integration (adapter, installer, IDE-detection entry, hooks, dedicated docs/tests). The separate, still-supported Gemini LLM/observation provider ( CLAUDE_MEM_GEMINI_API_KEY , GeminiProvider ) is unaffected. 
 
 Added 
 
 Full Antigravity CLI ( agy ) support at feature parity: hooks (7-event map sharing Gemini CLI's proven ~/.gemini/settings.json ), dual MCP server registration, and GEMINI.md /rules-file context injection. 
 npx claude-mem antigravity-cli install|status|uninstall subcommand support. 
 
 Verified end-to-end against a real live Antigravity CLI install, including hook firing, MCP tool registration, and context injection.