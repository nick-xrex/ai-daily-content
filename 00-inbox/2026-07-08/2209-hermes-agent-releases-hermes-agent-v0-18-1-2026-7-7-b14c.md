---
id: inbox_6ee637a0
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v2026.7.7"
author: "teknium1"
published_at: 2026-07-08T01:16:58+00:00
fetched_at: 2026-07-09T22:09:31.186282+00:00
content_hash: "b14c87d078c699f78504d6b359bf72e6571f80f79e3dc36aa486c713270cc4c0"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.18.1 (2026.7.7)

Hermes Agent v0.18.1 (v2026.7.7) 
 Release Date: July 7, 2026 
 
 Patch release. This tag rolls up the ~660 PRs merged since v0.18.0 (July 1) — bug fixes, hardening, and in-progress feature work — into a stable tagged release for downstream consumers (Docker images, hosted deployments, PyPI installs). 
 
 
 About this release 
 This is an infrastructure-driven patch tag rather than a fully curated release. Since v0.18.0 shipped six days ago, main has accumulated roughly 667 commits across ~990 files (+89.5k/−10.4k lines) , including installer/updater self-healing on Windows, dashboard and gateway fixes, WhatsApp dashboard pairing, MCP and provider fixes, and a large volume of stability work. 
 Full curated release notes for this window will ship with v0.19.0 , which will document everything from v0.18.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped; it's documented in the next minor release. 
 Updating 
 hermes update # existing installs 
pip install -U hermes-agent 
 Full Changelog : v2026.7.1...v2026.7.7