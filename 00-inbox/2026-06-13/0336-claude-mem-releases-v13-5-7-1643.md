---
id: inbox_8cec93fc
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.7"
author: "thedotmack"
published_at: 2026-06-13T00:06:28+00:00
fetched_at: 2026-06-13T03:36:13.643523+00:00
content_hash: "164384b2cd1a9176cdc14c3412421785a0eea7f176dfdef27d79841c96ae0373"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.7

What's Fixed 
 Stale Claude CLI can no longer silently kill every observation ( #2911 ) 
 If an abandoned npm-global claude binary sat earlier in PATH than your current install, every Observer spawn died instantly at flag parsing — worker healthy, zero observations, nothing in the logs. The resolver now: 
 
 Probes every candidate for capability , not just existence: each CLI is tested with --permission-mode dontAsk --version , the exact flags claude-mem passes on every agent spawn. Binaries that reject them (older than the 2.1.x line) are skipped up front with a clear warning. 
 Prefers the newest capable version — PATH order only breaks ties, so a stale binary can't shadow a current one. 
 Fails loud, never silent : an explicit CLAUDE_CODE_PATH that's too old throws with the version and the remedy; if every CLI found is too old, the error names each path and version. 
 Self-heals on CLI updates : successful resolutions are cached 15 minutes, failures are never cached — updating your CLI is picked up on the next observation without a worker restart. 
 Keeps a 2KB stderr tail from SDK children, included in exit warnings (and read on close , so it's never truncated) — a CLI dying at flag parsing now says why at default log level. 
 
 Build 
 
 Bundle-size budgets are now advisory warnings instead of hard build failures.