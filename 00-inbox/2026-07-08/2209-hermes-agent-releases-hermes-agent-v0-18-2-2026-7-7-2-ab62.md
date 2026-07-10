---
id: inbox_bcc19b4a
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.7.2"
author: "teknium1"
published_at: 2026-07-08T03:13:14+00:00
fetched_at: 2026-07-09T22:09:31.181103+00:00
content_hash: "ab6209b557beaef453341778831a204d25ee37b376dc79939c8f334b34c6966d"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.18.2 (2026.7.7.2)

Hermes Agent v0.18.2 (v2026.7.7.2) 
 Release Date: July 7, 2026 
 
 Same-day patch on top of v0.18.1, picking up the WhatsApp Baileys dependency fix needed for tagged-release Docker builds. 
 
 
 What's in this patch 
 
 fix(whatsapp): unpin Baileys from git commit, use published 7.0.0-rc13 ( #60643 ) — the WhatsApp bridge dependency now installs from the published npm release instead of a pinned git commit, making installs and Docker image builds reliable. 
 
 Full curated release notes for the entire post-v0.18.0 window ship with v0.19.0. 
 Updating 
 hermes update # existing installs 
pip install -U hermes-agent 
 Full Changelog : v2026.7.7...v2026.7.7.2