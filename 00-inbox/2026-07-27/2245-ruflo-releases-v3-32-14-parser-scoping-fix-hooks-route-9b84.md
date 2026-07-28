---
id: inbox_1a4ddc98
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.14"
author: "ruvnet"
published_at: 2026-07-27T02:20:52+00:00
fetched_at: 2026-07-27T22:45:54.323761+00:00
content_hash: "9b842b672e42869edbd35fd14c0584951dd320e56f5822d7700a897c68859641"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.32.14 — parser scoping fix + hooks route --parallel canonical restored

Follow-up to v3.32.13 that closes the last thing I left as a documented workaround. 
 Fixed 
 Parser: subcommand's non-boolean flag now overrides the global boolean set. The prior getBooleanFlags() walked every registered command + subcommand and merged all boolean options into one flat set that governed value-consumption everywhere. Any command anywhere declaring a name as boolean poisoned that name on every other command. That forced the --moa-parallel rename in v3.32.13. Fix: getScopedBooleanFlags now REMOVES flags from the boolean set when the resolved subcommand declares them as non-boolean. Narrowest scope wins. 
 hooks route --parallel restored as the canonical MoA fanout flag (with short -p ). --moa-parallel kept as a deprecated compat alias for anyone who upgraded to v3.32.13 in the ~15-minute window before this patch. 
 Test plan run 
 
 Parser tests: 55/55 → 56/56 (new regression test guarding the scoping fix) 
 hooks route --mode moa E2E matrix, all pass: --parallel 5 → 5, --moa-parallel 6 → 6, -p 4 → 4, default → 3, both-passed → canonical wins. 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.14