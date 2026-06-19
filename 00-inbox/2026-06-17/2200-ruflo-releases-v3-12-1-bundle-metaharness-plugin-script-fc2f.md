---
id: inbox_16002e71
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.12.1"
author: "ruvnet"
published_at: 2026-06-17T22:09:21+00:00
fetched_at: 2026-06-18T22:00:29.584903+00:00
content_hash: "fc2fb5cee6ba4aee91640b9ec8af88260c75129b8044b3bef518c6af7cf8b46c"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.12.1 — bundle metaharness plugin scripts

Hotfix 
 3.12.0 shipped the metaharness CLI dispatcher + 9 MCP tools but the 
plugin scripts the dispatcher delegates to weren't packed into the 
published tarball. Real-user impact: 
 $ npx ruflo@3.12.0 metaharness score --path .
metaharness: plugins/ruflo-metaharness/scripts/ not found.
 Install ruflo with `npm i ruflo` or run from the ruflo repo.
 
 Fix 
 @claude-flow/cli/package.json : 
 
 Added "plugins" to the files field 
 Added prepublishOnly hook that copies ../../../plugins/ruflo-metaharness/ into the package before npm pack 
 
 Verified end-to-end on a fresh install — all 10 npx ruflo metaharness * subcommands now find their underlying scripts. 
 Tarball size: 1310 → 1348 files (+38 plugin scripts). 
 Anyone on 3.12.0 should npm install ruflo@latest (or @3.12.1 ) to pick up the fix. 
 🤖 Generated with RuFlo