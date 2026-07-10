---
id: inbox_758b07a0
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.25.4"
author: "ruvnet"
published_at: 2026-07-08T02:21:39+00:00
fetched_at: 2026-07-09T22:09:33.307092+00:00
content_hash: "485811efb41a019efeeca072465c046fdcc56adc7c52f7dcf1a54b252bf3dc35"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.25.4 — re-sign helpers manifest

Metadata-only patch closing the #2593 loop. 
 3.25.3 shipped the CI guard for stale helpers.manifest.json but couldn't self-repair its own release because the GCP signing secret wasn't accessible from the publish environment. 3.25.4 ships a properly-signed manifest at version 3.25.4 that matches the package version. 
 No source or dependency changes. All fixes from 3.25.3 remain — this only re-signs the shipped manifest. 
 Install 
 npx ruflo@3.25.4
npx ruflo@latest
npx claude-flow@v3alpha
npx @claude-flow/cli@alpha
 
 All three legacy dist-tags ( latest , alpha , v3alpha ) point to 3.25.4. 
 Packages 
 
 @claude-flow/cli@3.25.4 
 claude-flow@3.25.4 
 ruflo@3.25.4 
 
 🤖 Generated with RuFlo