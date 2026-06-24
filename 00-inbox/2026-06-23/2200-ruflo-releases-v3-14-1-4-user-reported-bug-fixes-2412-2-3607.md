---
id: inbox_d69cbc1f
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.14.1"
author: "ruvnet"
published_at: 2026-06-23T16:16:50+00:00
fetched_at: 2026-06-23T22:00:26.262181+00:00
content_hash: "360759ae78937bf5c43e8d3ae0347272590a8785836cb31042243f5b289ef1a9"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.14.1 — 4 user-reported bug fixes (#2412, #2422, #2426, #2450)

Patch release fixing four user-reported bugs across CI, MCP transport, init migration, and docs. 
 Fixes 
 
 #2412 — v3-ci.yml red on main for 5+ days (10+ verification recurrences). Lockfile drifted after version bumps in cli/package.json ; CI's pnpm install --frozen-lockfile failed on every job. Regenerated v3/pnpm-lock.yaml . 
 #2450 — hooks statusline cold-loaded the ONNX model on every invocation (~1s), Claude Code timed out the statusLine command and hid the status bar. #2448 's migration only caught the npx @latest form; broadened the regex to also catch the bare claude-flow hooks statusline form so existing settings.json files get rewritten on next ruflo init / doctor. 
 #2426 — On macOS, the MCP tools/list response (65,747 bytes for 314 tools) exceeded the 64KB pipe buffer and was truncated mid-frame, leaving Claude Code unable to register any MCP tools. Set stdout/stderr to blocking mode in stdio MCP server — same approach as the official MCP SDK's StdioServerTransport. 
 #2422 — docs/USERGUIDE.md documented Weighted (Queen 3×) / Majority consensus modes and Strategic/Tactical/Adaptive queen types that aren't wired in the shipped engine. Rewrote 4 USERGUIDE locations to the actually-shipped 5 modes: byzantine / raft / gossip / crdt / quorum. 
 
 Verification 
 
 pnpm install --frozen-lockfile exits 0 locally (CI's exact gate) 
 @claude-flow/cli builds clean with no new TS errors 
 Direct stdio probe: baseline truncates 70KB payload to exactly 65,536 bytes (matches #2426 reporter's number); with fix, full 83,146 bytes delivered intact across 3 runs 
 End-to-end smoke against published ruflo@3.14.1 : spawned ruflo mcp start in stdio mode, sent tools/list , received 207,678 bytes (305 tools) intact — 3.17× the pipe buffer limit 
 Statusline regex unit test: 7/7 (5 broken forms caught, 2 correct forms skipped) 
 grep "Weighted\|Queen 3" docs/USERGUIDE.md returns 0 matches 
 
 Install 
 npx ruflo@3.14.1
 # or 
npx @claude-flow/cli@3.14.1 
 All three packages — @claude-flow/cli , claude-flow , ruflo — at 3.14.1 with consistent latest === alpha === v3alpha dist-tags. 
 PR 
 #2454 — full diff, per-commit review available there.