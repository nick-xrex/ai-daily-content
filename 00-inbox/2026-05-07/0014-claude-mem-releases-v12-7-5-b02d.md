---
id: inbox_eca1d3d2
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v12.7.5"
author: "thedotmack"
published_at: 2026-05-07T04:31:22+00:00
fetched_at: 2026-05-26T00:14:50.187510+00:00
content_hash: "b02d4bf87d4eb8c8faf947d366fd5fcd223d32e82deb93c39a593548c5c06242"
lang: en
caption_quality: None
raw: true
topics: []
---

# v12.7.5

Patch release for npx installs that hit an existing Codex marketplace registration. 
 Fixes: 
 
 If Codex already has claude-mem-local registered from a different source, the installer now removes that stale registration and re-adds the local npx marketplace instead of failing. 
 Keeps Codex plugin_hooks enablement and legacy AGENTS cleanup after the marketplace registration succeeds. 
 Updates the release workflow instructions to use npm run build-and-sync instead of plain npm run build so the local marketplace and worker are synced during releases. 
 
 Validation: 
 
 npm run build-and-sync 
 bun test tests/install-non-tty.test.ts tests/infrastructure/plugin-distribution.test.ts tests/servers/mcp-tool-schemas.test.ts tests/setup-runtime.test.ts tests/hook-command.test.ts 
 Docker smoke with codex-cli 0.128.0 reproducing the remote-to-local marketplace source conflict and verifying install completion. 
 npx --yes claude-mem@12.7.5 --version