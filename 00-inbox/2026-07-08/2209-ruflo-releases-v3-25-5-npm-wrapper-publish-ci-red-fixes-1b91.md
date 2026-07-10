---
id: inbox_df4916eb
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.5"
author: "ruvnet"
published_at: 2026-07-08T17:27:46+00:00
fetched_at: 2026-07-09T22:09:33.305973+00:00
content_hash: "1b917a78521f2dcc0764b2189c530db54c89f98384b473b7e34882e38c15663d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.5 — npm wrapper publish + CI-red fixes

Published to npm 
 This release publishes the CI-red fixes from fix/main-v3-ci-red-shim-types to npm, including the root claude-flow wrapper package. 
 Packages 
 
 claude-flow@3.25.5 ( latest , alpha , v3alpha ) 
 @claude-flow/cli@3.25.5 ( latest , alpha , v3alpha ) 
 @claude-flow/plugin-agent-federation@1.0.0-alpha.17 ( latest , alpha ) 
 
 Fixes covered 
 
 #2613 — PreToolUse hook stdout contract for Cursor/Claude Code compatibility 
 #2608 — optional dependency import safety and plugin-agent-federation TS build 
 #2590 — Node 24 pnpm smoke verified green 
 #2578 — in-repo phantom subpath guard verified green 
 
 Verification 
 
 npx -y claude-flow@3.25.5 --version returned ruflo v3.25.5 
 npx -y @claude-flow/cli@3.25.5 --version returned ruflo v3.25.5 
 npx -y @claude-flow/plugin-agent-federation@1.0.0-alpha.17 --help ran successfully 
 V3 CI/CD run 28961054348 completed successfully for the relevant checks 
 
 Tracking issue: #2614 
 Release gist: https://gist.github.com/ruvnet/ed276119404d4d3fffdadfc0797705f8 
 Note: npm packages were published from temporary staging directories to avoid including unrelated dirty worktree state. A follow-up source metadata commit should update package versions to match the published artifacts.