---
id: inbox_5f5f59d6
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.10.42"
author: "ruvnet"
published_at: 2026-06-11T15:04:38+00:00
fetched_at: 2026-06-11T22:00:26.815485+00:00
content_hash: "a617c8bdfd729a0830bec92cd34d2eaadfdceab3cd9afa91c6e647a38ffdcd88"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.10.42 — community bug batch: Windows path validation, trajectory feedback, init hooks

Patch release fixing three reproducible community bugs reported by @grym3s , batched in the style of v3.10.41 / PR #2346 . 
 Fixes 
 #2352 — hooks post-edit : Windows paths rejected, failure printed as [OK] 
 
 validatePath used the general SHELL_META set which includes \ , so every absolute Windows path ( E:\Repos\... ) failed with "shell metacharacters" . Claude Code hook events deliver absolute paths in tool_input.file_path , so every forwarded post-edit call failed silently on Windows. 
 The CLI action printed [OK] Outcome recorded for ... whenever the MCP call returned at all, masking the failure. Now checks result.success , surfaces the error, and exits non-zero. 
 
 #2351 — trajectory-end : step-less feedback never distilled 
 When trajectory-end is called with feedback but no recorded steps (the common LLM-agent case), the feedback was persisted with the trajectory but never embedded as a searchable pattern — patternsExtracted always reported 0 and pattern-search never surfaced it. Now routes the trimmed feedback through bridge.bridgeStorePattern (or store-fallback) with modest default confidence, tagged trajectory-feedback . New feedbackDistilled.{patternId, controller} field on the response. 
 #2350 — init hooks : subcommand wrote no hooks block to settings.json 
 The settings generator gates the hooks block on components.helpers (the hook commands point at the helper script). The init hooks subcommand had helpers: false , so the one subcommand whose purpose is "Initialize only hooks configuration" produced settings.json with no hooks key while reporting "N hooks enabled" . Helpers now ship with the subcommand. 
 Install / upgrade 
 npx ruflo@latest init # 3.10.42 
npx @claude-flow/cli@latest # 3.10.42 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) are pinned to 3.10.42. 
 Tests 
 
 New validate-input-path-2352.test.ts — 22 tests pin Windows-path acceptance, POSIX still works, all shell metacharacters and traversal still rejected. 
 All existing validate-input , init-wizard-bugs , hooks-intelligence-learning , hooks-post-task tests still pass. 
 
 Diff 
 PR #2355 · main...v3.10.42 
 🤖 Generated with RuFlo