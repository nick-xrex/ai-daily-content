---
id: inbox_704712dc
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.2"
author: "thedotmack"
published_at: 2026-06-10T04:49:49+00:00
fetched_at: 2026-06-10T22:04:26.402988+00:00
content_hash: "b158822cd532748d1d517b44e5fdfed77e30425bb0c506dd55b103a189e23e41"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.2

What's New in 13.5.2 
 Platform and toolchain telemetry to diagnose the install → live-worker activation dropoff (anonymous, opt-out — see npx claude-mem telemetry ): 
 
 Every event now carries os_version (kernel release — distinguishes Windows 10 vs 11, macOS releases), is_wsl , and node_version alongside the existing os / arch / runtime fields. 
 install_completed now reports interactive (TTY vs scripted), install_method (npm / bun / pnpm / yarn), and detected bun_version , uv_version , and claude_code_version . 
 install_failed carries the same install context so aborted installs are sliceable by platform too. 
 New fields are person properties as well, so activation funnels can be broken down by OS version, WSL, and install method. 
 Scrub whitelist, consent screen, docs, and tests updated for every new property. 
 
 🤖 Generated with Claude Code