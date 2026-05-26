---
id: inbox_d8a9e2bb
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/v0.41.0"
author: "rtk-release-bot[bot]"
published_at: 2026-05-23T07:50:22+00:00
fetched_at: 2026-05-26T00:14:51.707122+00:00
content_hash: "48b9e9e083a253c8b2d59996dc66ef4f676a6322465250a1ce9f1a613a43905f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.41.0

0.41.0 (2026-05-22) 
 Features 
 
 hints: add tail hints for tee &amp; hints + address reviews ( 46fe7c4 ) 
 
 Bug Fixes 
 
 docker: forward --tail flag in compose logs ( 5f1d8b0 ) 
=* filters: add test for aggressive filter batch fix ( f6b28c2 ) 
 filters: address adversarial test-suite findings on aggressive filtering ( 62fc0e0 ) 
 filters: aggresivity batch fix ( 90c285c ) 
 filters: split docker ps/-a paths, cap ruff violations at 50 ( f21b864 ) 
 git: drop -uall from compact status so output never exceeds raw ( 7753e48 ) 
 git: preserve full status paths and untracked files ( 3ba1634 ) 
 git: stream push output to avoid spurious 30s timeout ( #963 ) ( d6c5647 ) 
 git: stream push output via FilterMode::Streaming ( #963 ) ( be51783 ) 
 hooks/init: preserve user content in copilot-instructions.md ( d108165 ) 
 install: reject archive with path traversal before extraction ( #1250 ) ( e827184 ) 
 kubectl: compact get pods and services aliases ( 2dd0ec9 ) 
 re-add env python as noisy dir ( 4eefe2f ) 
 rust: multi-line blocks used with tail hint ( 4960630 ) 
 tee: safe truncation caps and compose-ps tee content fix ( 548e4dd ) 
 tee: safe truncation caps and tee/hint coverage ( 15a0d2e ) 
 truncate: global caps reduce (avoid underflow and 0 results) ( d5a1731 ) 
 
 
 '...' ascii to unicode, remove some comments ( 3571d52 )