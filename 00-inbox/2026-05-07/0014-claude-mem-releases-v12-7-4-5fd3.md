---
id: inbox_213bdcbc
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v12.7.4"
author: "thedotmack"
published_at: 2026-05-07T02:40:42+00:00
fetched_at: 2026-05-26T00:14:50.188658+00:00
content_hash: "5fd327b4bba93569de0d8472e8f06a73fefb3682f855051260bc596509df5ccc"
lang: en
caption_quality: None
raw: true
topics: []
---

# v12.7.4

Patch release for the Codex mem-search marketplace fix. 
 Highlights: 
 
 Restores Codex access to the claude-mem MCP/search plugin by pointing the Codex marketplace at the bundled plugin root. 
 Adds resilient MCP launcher fallbacks for local installs, Codex plugin cache installs, Claude plugin cache installs, and remote marketplace clones. 
 Registers Codex plugin marketplaces during install, enables plugin_hooks, and cleans up legacy AGENTS-based Codex context injection. 
 Includes the Codex session-start hook migration and Codex version-mismatch investigation plan. 
 
 Validation: 
 
 npm run build 
 bun test tests/install-non-tty.test.ts tests/infrastructure/plugin-distribution.test.ts tests/servers/mcp-tool-schemas.test.ts tests/setup-runtime.test.ts tests/hook-command.test.ts 
 Docker smoke with codex-cli 0.128.0 for local install, remote marketplace add/upgrade, and MCP initialize.