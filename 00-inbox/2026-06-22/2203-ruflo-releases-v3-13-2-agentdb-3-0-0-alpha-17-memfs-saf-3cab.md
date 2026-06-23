---
id: inbox_015ecf39
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.13.2"
author: "ruvnet"
published_at: 2026-06-22T16:08:01+00:00
fetched_at: 2026-06-22T22:03:43.573746+00:00
content_hash: "3cab6b73946193dde943c41dc169e088a16e300398f5621893139191ac78ad06"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.13.2 — agentdb 3.0.0-alpha.17 MEMFS safety net (upstream-side #2432 fix)

🔧 Picks up upstream agentdb fix 
 `agentdb@3.0.0-alpha.17` adds a `FinalizationRegistry` safety net inside `SqlJsRvfBackend` ( ruvnet/agentdb#10 ). This is the upstream-side fix for the MEMFS leak class that ruflo v3.13.1 already addressed downstream. 
 Combined effect on #2432 : the leak class is now closed at BOTH layers — downstream (close-on-replace in ControllerRegistry) and upstream (defensive FinalizationRegistry that catches consumers who forget). Belt + suspenders. 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 `agentdb` 
 3.0.0-alpha.17 
 — 
 — 
 
 
 `@claude-flow/cli` 
 3.13.2 
 3.13.2 
 3.13.2 
 
 
 `claude-flow` 
 3.13.2 
 3.13.2 
 3.13.2 
 
 
 `ruflo` 
 3.13.2 
 3.13.2 
 3.13.2 
 
 
 
 Upgrade 
 ```bash 
npx ruflo@latest # picks up 3.13.2 + agentdb 3.0.0-alpha.17 
``` 
 Cross-references 
 
 🔗 Upstream PR: ruvnet/agentdb#10 
 🔗 Upstream issue: ruvnet/agentdb#9 
 🔗 Downstream issue: #2432 (closed in v3.13.1) 
 🔗 Companion: v3.13.1 downstream-side fix (PR #2444 ) 
 
 
 🤖 Generated with RuFlo