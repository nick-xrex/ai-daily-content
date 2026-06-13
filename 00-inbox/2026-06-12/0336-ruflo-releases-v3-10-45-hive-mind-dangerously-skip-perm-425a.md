---
id: inbox_7f3084ec
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.45"
author: "ruvnet"
published_at: 2026-06-12T21:04:59+00:00
fetched_at: 2026-06-13T03:36:12.947106+00:00
content_hash: "425aa2de5f020bed84a77477676a65bf257bb329bb668e8bc09c38c7c7653da7"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.45 — hive-mind --dangerously-skip-permissions deny clause

Patch release shipping the completion of the hive-mind permissions fix from v3.10.44's held PR. 
 Fix 
 #2301 — hive-mind --dangerously-skip-permissions now also honors --no-auto-permissions 
 Background: the arg parser converts kebab-case CLI flags to camelCase and stores only the normalized key. The original predicate in hive-mind.ts read only the kebab form for both the activation and deny halves, so: 
 
 --dangerously-skip-permissions silently no-op'd (closed #2269 originally) 
 --no-auto-permissions silently no-op'd (uncovered when validating the v3.10.44 batch) 
 
 The earlier patch (PR #2301 in JOhnsonKC201's branch) correctly fixed the activation half by accepting both kebab + camelCase keys, but the deny half still missed: the parser does NOT produce noAutoPermissions: true for --no-auto-permissions — it uses yargs-style negation and stores autoPermissions: false . 
 Net effect of the partial fix: after activation worked, --dangerously-skip-permissions --no-auto-permissions would have skipped permissions anyway — strictly more permissive than the pre-fix state where activation never even fired. 
 This release adds the third deny clause: 
 const skipPermissions = 
 ( flags [ 'dangerously-skip-permissions' ] === true || flags . dangerouslySkipPermissions === true ) &amp;&amp; 
 ! ( flags [ 'no-auto-permissions' ] || flags . noAutoPermissions || flags . autoPermissions === false ) ; 
 Three new regression tests pin the contract: 
 
 parser produces autoPermissions: false for --no-auto-permissions 
 predicate denies on the parser-produced shape { dangerouslySkipPermissions: true, autoPermissions: false } 
 autoPermissions: true is NOT a deny signal (only === false is) 
 
 Test suite: 9/9 pass. Closes #2269 . 
 Co-authored: @JOhnsonKC201 (original PR), @rvrheenen (reporter who supplied the patch). 
 Install / upgrade 
 npx ruflo@latest init # 3.10.45 
npx @claude-flow/cli@latest # 3.10.45 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.45. 
 Diff 
 main...v3.10.44 — PR #2301 plus the release bump. 
 🤖 Generated with RuFlo