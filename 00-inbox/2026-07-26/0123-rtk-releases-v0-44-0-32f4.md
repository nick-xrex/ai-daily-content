---
id: inbox_01aebefc
source: rtk-releases
source_type: rss
url: "https://github.com/rtk-ai/rtk/releases/tag/v0.44.0"
author: "rtk-release-bot[bot]"
published_at: 2026-07-26T12:45:56+00:00
fetched_at: 2026-07-27T01:23:06.464099+00:00
content_hash: "32f49e194e2a2d437a81e96e8448f29f84ead47ba5646e0acaef9c21585e498a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.44.0

0.44.0 (2026-07-26) 
 Features 
 
 add git checkout support ( be1844c ) 
 add uv run support ( a5f0774 ) 
 cargo: route --message-format=json builds through explicit arg detection ( 5ea03f3 ) 
 hook: add Cargo.lock ( 531bc93 ) 
 hook: add support for Kimi AI agent ( 7624c43 ) 
 hooks: add Factory Droid integration ( 8a8b356 ) 
 hook: wire TOML filters + better tee tail hint ( 31f9d43 ) 
 hook: wire TOML filters into the rewrite path + reversible truncation ( 73b8cb3 ) 
 php: consolidated PHP tooling (php, artisan, phpunit, phpstan, pest, paratest, ecs, pint) ( 1052c1c ) 
 pipe: expose PHP tool filters as stdin pipe filters ( 214a79a ) 
 sbt: add SBT (Scala Build Tool) support ( 4f86523 ) 
 trust: gate custom filters (project + user-global) + init opt-in flags ( 1130a7c ) 
 trust: rtk trust uses the same opt-in prompt as init ( e0a83ac ) 
 
 Bug Fixes 
 
 analytics: floor prefix slices to char boundary instead of full-string fallback ( c9468ee ) 
 analytics: truncate display strings on UTF-8 char boundaries ( 47b22e0 ), closes #2787 
 benchmark: use deterministic curl and wget responses ( 6c57836 ) 
 benchmark: use stable indexed MockHTTP responses ( 8dd5a34 ) 
 cargo: give the json batch filter the exit code ( a3e65e9 ) 
 cargo: honor last --message-format when the flag is repeated ( 25d6a09 ) 
 cargo: keep "No issues found" wording for clean clippy json runs ( 1f74614 ) 
 cargo: label check output as "check" instead of "build" ( 90b4f5f ) 
 cargo: match the human path when skipping the json warning summary ( 59ed885 ) 
 cargo: restore failure check before trusting reused build filter ( e4bfe35 ) 
 cargo: skip "N warnings generated" record in json diagnostics ( 9ae0872 ) 
 cargo: strip ansi from json rendered diagnostics ( b47653a ) 
 cargo: surface --message-format=json test compile errors ( f9b720c ) 
 cargo: tee-hint dropped json diagnostics beyond the cap ( cf1caf9 ) 
 cargo: tighten json warning-summary skip to ends_with ( 6c9a60d ) 
 ccusage: accept period key from current ccusage ( d823aaf ) 
 cicd: next release pr target fork compatibel ( 6e34bba ) 
 copilot: add missing 'get' to kubectl example in init template ( f9d8c77 ) 
 copilot: remove unnecessary test ( b49568f ) 
 copilot: support IDE terminal hooks ( 1d6798d ) 
 detect absolute rtk path in Claude hook settings ( 5d32d07 ) 
 filter: address review findings in the TOML filter path ( 315a943 ) 
 gain: note untrusted custom filters so they can be re-trusted ( a4872d9 ) 
 git: compact git stash show instead of forcing -p ( 1b38eec ) 
 grep: only insert -- separator when context flags are active ( 34a0f0e ) 
 grep: preserve -- separator between non-adjacent match blocks ( 6871e55 ) 
 hook: handle AskRewrite in Cursor hook when no rules configured ( ff0b9ac ), closes #2372 
 hook: include ask rules in cursor_has_explicit_rules check ( 3362325 ) 
 hook: kimi init writes AGENTS.md instead of dead .kimirules ( 8fe4a40 ) 
 hooks: distinguish explicit ask from default in AskRewrite ( 0df6929 ) 
 hooks: don't force-allow Droid rewrites ( 9dd8211 ) 
 hooks: emit permissionDecision allow for simple Copilot CLI rewrites ( 23d1e89 ) 
 hooks: source Droid verdicts from Droid's own permission lists ( 70ed82a ) 
 hook: use ask action in audit log for AskRewrite verdict ( 36dd8f2 ) 
 hook: use ask permission for AskRewrite in Cursor hook ( a0c16ef ) 
 init: honor RTK_TELEMETRY_DISABLED in consent prompt ( #1307 ) ( debac0f ) 
 openclaw: handle exit code 3 from rtk rewrite ( 487a2e7 ), closes #2202 
 parser: use byte offsets instead of char indices in extract_json_object ( 32dda24 ) 
 parser: use byte offsets instead of char indices in extract_json_object ( 27f9739 ), closes #2509 
 permissions: stop extra whitespace from evading deny rules ( 3483786 ) 
 permissions: stop extra whitespace from evading deny rules ( f6b9290 ) 
 php: address phpstan review feedback (resolution, text fallback, path compaction) ( 07c231e ) 
 php: anchor phpunit failure-heading detection to the "N) " format ( 128d04f ) 
 php: classify php subcommands in the PASSTHROUGH list ( 4a37246 ) 
 php: default pint applied_fixers when key is absent ( 0cc15dc ) 
 php: detect phpstan analyse after global flags; avoid duplicate format ( 7cc46b4 ) 
 php: drop bogus pest.php check in test-runner detection ( 28366ce ) 
 php: rewrite ./vendor/bin/&lt;tool&gt; form for phpunit/pest/paratest/ecs/pint ( 88e56ce ) 
 php: route php_tool_command through resolved_command ( 8eae6b7 ) 
 php: strip ANSI in phpunit filter and split errors from failures ( 8825480 ) 
 pipe: anchor phpunit auto-detection to the leading banner ( 50a8743 ) 
 pytest: strip ANSI so colored runs don't dump raw output ( aba7643 ) 
 python: stop reporting a failed tool run as clean ( 86b34df ) 
 remove absolute Claude hook commands ( b0c0b20 ) 
 rewrite only safe final pipeline commands ( 590445e ) 
 rewrite: keep pipeline-final wc commands raw ( 1c5a23c ) 
 ruff: honour a user-supplied --output-format ( 44982e0 ) 
 run: propagate signal exit code instead of unwrap_or(1) ( 113ae11 ) 
 sbt: address review feedback on output guard, routing, and dead code ( ef38103 ) 
 sbt: compute tee label before args_display move ( 3dff2aa ) 
 sbt: drop sbt 0.13 legacy task names ( f6a4c41 ) 
 sbt: filter testOnly/testQuick like sbt test ( 194f392 ) 
 sbt: separate tee label for selective test tasks ( 973b3b6 ) 
 search: stream piped grep and rg output ( 66b95cb ) 
 test: adapt new rewrite_command signature in php-tooling tests ( c37eed9 ) 
 tokenize |&amp; as a single pipe operator ( ee149ee ) 
 trust: label detected filters as project- or global-scoped ( a9c33e2 ) 
 trust: skip untrusted filters silently on the command path ( 9d3b678 ) 
 trust: surface parse errors, skip already-trusted files, fail loudly when non-interactive ( 2d487cb ) 
 uv: make tee recovery hints resolve to the data they promise ( bf14bf5 ) 
 uv: pass guard_raw arg to print_with_hint after signature change ( 7e42d92 ) 
 uv: preserve program stdout and restore inner-command filtering ( 8dd4aac ) 
 uv: remove uv run from transparent prefixes to fix rewrite conflicts ( 96f9422 ) 
 
 Performance Improvements 
 
 hook: match TOML filters with a match-only RegexSet ( 34c0bcf ) 
 php: cache composer_bin_dirs to avoid per-segment file reads ( 5d2928c ) 
 php: resolve cwd once in pint output instead of per file ( b5c3f7f ) 
 
 Reverts 
 
 cargo: drop --message-format=json install routing ( 751bf3e )