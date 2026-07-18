---
id: inbox_de702201
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.2"
author: "ruvnet"
published_at: 2026-07-17T04:03:06+00:00
fetched_at: 2026-07-17T22:30:44.647110+00:00
content_hash: "e4c3a00c275470ebbe617f9b955d9bb66c9d2b7b10100a099645c744dbb3d899"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ruflo v3.32.2 — Stable Codex Integration & Plugin Recovery

Ruflo v3.32.2 ? stable Codex integration and plugin recovery 
 This stable patch release fixes the hook parsing and MCP startup failures reported against cached Ruflo plugin bundles, hardens Codex initialization, restores security defend , and corrects plugin MCP tool names. 
 Highlights 
 
 Codex startup: generated Ruflo MCP registrations now use the platform-correct ruflo@latest mcp start command and a 120-second minimum startup timeout. 
 Valid versioned hooks: patched plugin identities ( ruflo-core 0.2.4 and ruflo-cost-tracker 0.26.2) replace stale cached bundles; shipped hook configs are non-empty, valid JSON. 
 Reliable shutdown: hooks session-end always closes the native bridge; hook shims use a 15-second watchdog and stable ruflo@latest fallback. 
 Correct plugin tools: 1,111 plugin MCP references now use the installed-plugin namespace. Standalone repository docs retain their correct standalone namespace. 
 Working security defense: a zero-dependency built-in scanner handles prompt injection, jailbreak, exfiltration, and common PII when the optional full AI Defense package is absent. 
 Honest statusline: project name is the default identity, and security status counts real findings instead of fabricated CVEs. 
 
 Install or update 
 npm install -g ruflo@3.32.2
npx -y ruflo@3.32.2 init --codex 
 For manual Codex configuration, set: 
 [ mcp_servers . ruflo ]
 startup_timeout_sec = 120 
 Windows uses command = "cmd" with args = ["/c", "npx", "-y", "ruflo@latest", "mcp", "start"] ; POSIX uses command = "npx" with args = ["-y", "ruflo@latest", "mcp", "start"] . 
 Published stable packages 
 
 @claude-flow/cli@3.32.2 
 claude-flow@3.32.2 
 ruflo@3.32.2 
 
 All three are published under npm's latest dist-tag. No alpha release tag was used. 
 Validation 
 PR #2700 merged after 122 successful checks, 3 intentional skips, and 0 failures . Focused validation also passed 144/144 tests, all package dry-runs, helper signature verification, 37/37 plugin manifests, 134/134 skill frontmatter files, Windows hook shim smoke (12/12), plugin namespace auditing, and signed witness verification. 
 Detailed recovery and technical notes 
 The full guide includes the exact Windows cache recovery commands, MCP TOML examples, package checksums, issue-by-issue behavior, and validation details: 
 https://gist.github.com/ruvnet/2b37060362af57bbffd421aa09e4db50 
 Issues fixed 
 
 #2670 ? security defend missing optional runtime 
 #2682 ? statusline project identity 
 #2685 ? plugin-bundled MCP namespace mismatch 
 #2691 ? hooks session-end native handle leak 
 #2694 ? fabricated CVE statusline counts 
 
 Full Changelog: v3.32.1...v3.32.2