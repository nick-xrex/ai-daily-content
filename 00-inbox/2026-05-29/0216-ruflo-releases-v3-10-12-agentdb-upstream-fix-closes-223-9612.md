---
id: inbox_5aa114fc
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.12"
author: "ruvnet"
published_at: 2026-05-29T23:01:38+00:00
fetched_at: 2026-05-30T02:16:29.842959+00:00
content_hash: "9612f126a6eeab87be5bcfb307b2b6804ad3fc80459a47052ef1e8851d70b1f1"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.12 — agentdb upstream fix (closes #2235 A)

Bumps the bundled agentdb to 3.0.0-alpha.15 so the optionally-installed 
 better-sqlite3 is finally engaged by the MCP memory bridge — the part (A) 
half of #2235 that was upstream-only. 
 The matching agentdb fix also closes ruvnet/agentdb#1 and #2 (schemas inlined as bundled string constants so loadSchemas() works in the browser and in globally-installed CLIs). 
 Install: npx ruflo@3.10.12 
 Closes: ruflo#2235 (A).