---
id: inbox_73a89d3d
source: codex-releases
source_type: rss
url: "https://github.com/openai/codex/releases/tag/rust-v0.144.1"
author: "github-actions[bot]"
published_at: 2026-07-09T23:04:05+00:00
fetched_at: 2026-07-10T00:23:34.393758+00:00
content_hash: "208d636fd1e6760d927d6469427313ea5a74489a29e16e97a329ebe57811629b"
lang: en
caption_quality: None
raw: true
topics: []
---

# 0.144.1

Bug Fixes 
 
 Fixed standalone installs failing when GitHub returns compact or reordered release metadata. ( #31913 ) 
 Ensured macOS package installs expose the code-mode host alongside the codex executable. ( #31913 ) 
 Kept code mode working when the companion host binary is unavailable by falling back to the embedded runtime. ( #31913 ) 
 
 Changelog 
 Full Changelog: rust-v0.144.0...rust-v0.144.1 
 
 #31913 [0.144] Backport installer and code-mode reliability fixes @bolinfest