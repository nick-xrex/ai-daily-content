---
id: inbox_bb8e754c
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.38"
author: "ruvnet"
published_at: 2026-07-29T19:56:43+00:00
fetched_at: 2026-07-29T22:26:10.220056+00:00
content_hash: "c00027f1e7b8b03951befa4156258219020f0d636d58b90f18e4aa41211254c7"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ruflo v3.32.38 — Daemons Start Only for Ruflo Projects

Ruflo v3.32.38: Daemons Start Only for Ruflo Projects 
 Ruflo v3.32.38 fixes a background-process leak discovered during the 
post-release audit: a read-only command in a directory containing only a 
Claude Code .claude/ folder could start a detached Ruflo daemon. 
 The trigger was subtle. Signed-champion startup migration created a 
 .claude-flow/ state directory, and daemon auto-start then mistook that 
startup-created directory for prior user initialization. Repeated commands in 
unrelated Claude projects could therefore accumulate one daemon per directory. 
 Install or upgrade 
 npm install --global ruflo@3.32.38
ruflo --version 
 What changed 
 Daemon auto-start now requires a durable Ruflo project marker: 
 
 a Ruflo runtime config under .claude-flow/ ; 
 a legacy claude-flow.config.json ; 
 an initialized .swarm/memory.db ; 
 a Ruflo-specific Claude settings section; or 
 a Ruflo/Claude Flow MCP server entry. 
 
 A generic .claude/ directory, an empty .claude-flow/ directory, or policy 
state created during the current startup no longer authorizes a detached 
process. Explicit ruflo daemon start remains available everywhere, and 
initialized Ruflo projects retain automatic background workers. 
 Validation 
 
 The exact issue reproduction was run against 3.32.37 and produced a daemon. 
 The same reproduction against the patched build produced no process and no 
daemon PID file, even though signed-champion and policy state were applied. 
 Daemon auto-start regression suite: 13/13. 
 CLI TypeScript build passes. 
 The stable release pipeline builds immutable archives, smoke-installs all 
three public packages, publishes those same bytes, and verifies a fresh 
registry installation. 
 
 This release resolves 
 #2852 .