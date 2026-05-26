---
id: inbox_084f12b6
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.2"
author: "ruvnet"
published_at: 2026-05-25T21:21:40+00:00
fetched_at: 2026-05-26T00:14:49.533704+00:00
content_hash: "7b92a8181c18d105399b2cc9f54134dd813293d55b6d62fbad20624f2c34dff9"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.2 — #2132 Windows plugin hooks fix

Highlights 
 Windows plugin hooks now work natively without WSL / Git Bash ( #2132 ). 
 Reporter @marioja documented every offending plugin hooks.json file: /bin/bash -c invocations, POSIX-only pipelines (jq, xargs -0, tr), and .sh shim scripts that crashed on native Windows with exit 126 ("cannot execute binary file"). 
 What shipped 
 
 Node shim : new plugins/ruflo-core/scripts/ruflo-hook.cjs (and copies in .claude-plugin/scripts/ and plugin/scripts/ ) — cross-platform port of the bash shim, reads stdin JSON via Node, dispatches via child_process.spawn, always exits 0 
 Init-time platform detection : ruflo init on Windows now writes a .claude/settings.json that overrides plugin bash hooks with node-based equivalents 
 Mac/Linux unchanged : existing ruflo-hook.sh and plugin hooks.json byte-identical — Windows path is purely additive 
 
 CI validation 
 
 Static audit: scripts/audit-plugin-hooks-cross-platform.mjs enforces no /bin/bash , no POSIX-only pipelines, no .sh references in plugin hooks 
 3 new smoke jobs on ubuntu + macos + windows-latest matrix: shim invocation, init-generated settings, end-to-end hook execution (proves no exit-126) 
 Test baseline preserved: 1999 passing | 46 skipped throughout 
 
 Versions 
 
 @claude-flow/cli@3.10.1 
 claude-flow@3.10.1 
 ruflo@3.10.2 
 
 All dist-tags (latest + alpha + v3alpha) updated. 
 🤖 Generated with RuFlo