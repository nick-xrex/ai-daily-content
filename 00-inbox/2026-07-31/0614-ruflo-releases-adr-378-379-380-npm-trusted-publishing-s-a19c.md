---
id: inbox_1cd17cc7
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/adr-378-380-agntcy-outshift-integration"
author: "ruvnet"
published_at: 2026-07-31T15:30:07+00:00
fetched_at: 2026-08-01T06:14:51.100898+00:00
content_hash: "a19cf3cbbb6ba3e7001454260c478803463c63a6963b7a89324562023b4499fa"
lang: en
caption_quality: None
raw: true
topics: []
---

# ADR-378/379/380 — npm Trusted Publishing, statusline segments, AGNTCY/Outshift integration

Merge marker for PR #2879 — not an npm version release ( @claude-flow/cli / claude-flow / ruflo remain at 3.33.0 on npm). 
 Full consolidated release notes: https://gist.github.com/ruvnet/d6fc9bea2758049fd87424a2718dec1e 
 See it illustrated: ruflo × AGNTCY — an animated walkthrough 
 Three ADRs merged: npm Trusted Publishing proposal (ADR-378), optional statusline usage segments (ADR-379), and AGNTCY/Outshift runtime integration with real, tested CASA envelope enforcement + CLI scaffolding (ADR-380). Companion: ruvnet/metaharness PR #155 (ADR-240). 
 An adversarial security review found and PR #2879 fixed two real bugs in the CASA enforcement gate before merge — see the gist for details. 
 Update: PR #2888 pins @agntcy/slim-bindings to the confirmed-working pre-release build ( 2.0.0-alpha.5 ) — verified live, a real SLIM server/client bring-up now succeeds under plain Node with zero errors. Not yet in an npx ruflo@latest release; build from main to try it today.