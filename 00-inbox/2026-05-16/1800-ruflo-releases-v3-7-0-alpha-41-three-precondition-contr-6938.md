---
id: inbox_93a0f936
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.41"
author: "ruvnet"
published_at: 2026-05-16T12:52:08+00:00
fetched_at: 2026-05-22T18:00:34.017773+00:00
content_hash: "6938443f5e0c0908467a6f8d86295442c99bdc2d67826909a54defebcb3e9f36"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.7.0-alpha.41 — three precondition/contract fixes + CI guards (#1880, #2019, #2015)

Three small but high-impact fixes ship together — each one resolves a recurring failure whose root cause was the same anti-pattern: a try/catch (or missing flag) silently turned a clear precondition failure into a vague "verification failed" / "controller disabled" / "rvf create failed" outcome that downstream consumers couldn't act on. 
 Fixes 
 #1880 — scheduled witness verification stops misfiling install/build gaps as regressions 
 The 12-hour scheduled verification was opening a duplicate "HIGH — verification broken" issue every cron cycle since 2026-05-10 because the runner does a source-only checkout (no @noble/ed25519 install, no npm run build ) and verify.mjs lumped that into the same exit 1 bucket as a real signature regression. 
 verify.mjs now reserves exit 2 strictly for precondition misses: 
 
 @noble/ed25519 not installed → exit 2 
 every manifest entry missing AND the manifest references /dist/ paths → exit 2 (source-only checkout, build never ran) 
 
 Real failures (signature invalid, specific marker regressed) keep exit 1 . The scheduled runner can now distinguish "needs install/build" from "we broke something" and stop filing duplicate issues. 
 #2019 — vectorBackend no longer permanently disabled with agentdb@3.0.0-alpha.14+ 
 @claude-flow/memory 's controller registry called agentdb.getController('vectorBackend') . Upstream agentdb's getController switch only handles memory / reflexion / skills / causal and throws Unknown controller: vectorBackend for everything else — a try/catch silently swallowed the throw, leaving the controller enabled: false even though agentdb.vectorBackend is a real field on the instance (assigned in AgentDB.initialize() ). 
 The registry now probes agentdb[name] directly first and falls back to getController only when the field is absent. Applied to all three accessor paths ( initializeController , get , isEnabled ). RuntimeConfig gains an optional agentdb field for test injection and consumer-owned AgentDB lifecycles. 
 #2015 — ruflo-browser browser_session_record actually works 
 ruvector@0.2.25 makes -d, --dimension &lt;n&gt; required on rvf create . The browser_session_record MCP tool wrapper invoked rvf create ... --kind browser-session without the flag, so every call returned { success: false, error: "rvf create failed" } . All five call sites (TS, shell, three markdown recipes) now pass --dimension 384 to match the MiniLM-L6 / AgentDB index default. 
 New CI guards 
 Both fixes ship with dedicated regression smokes in v3-ci.yml , wired into witness-verify 's needs: so a contract break blocks publish. 
 
 witness-verify-precondition-smoke ( #1880 ) — drives all three shapes (missing dep / all-files-missing / built tree) through verify.mjs and asserts the exit-code contract. 
 browser-rvf-create-flags-smoke ( #2015 ) — static scan of every rvf create ... --kind browser-session invocation across TS, dist, shell, and markdown — fails on any missing --dimension / -d . 
 
 The pre-existing pre-bash-hook-smoke ( #2017 ) gate is unchanged and still wired in. 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/memory 
 3.0.0-alpha.16 
 
 
 @claude-flow/cli 
 3.7.0-alpha.41 
 
 
 claude-flow 
 3.7.0-alpha.41 
 
 
 ruflo 
 3.7.0-alpha.41 
 
 
 
 All latest / alpha / v3alpha dist-tags updated. 
 Install 
 npx @claude-flow/cli@latest doctor
 # or 
npx ruflo@latest 
 Regression check (post-publish) 
 Installed each published artifact fresh from the registry and confirmed: 
 
 @claude-flow/memory@3.0.0-alpha.16 — ControllerRegistry.get('vectorBackend') returns the live instance even when a fake agentdb's getController throws Unknown controller: vectorBackend (the exact bug shape from #2019 ). 
 @claude-flow/cli@3.7.0-alpha.41 — compiled dist/src/mcp-tools/browser-session-tools.js carries '--dimension', '384' in the rvf create shell invocation. 
 
 Commit: e4bd9bbcb 
 🤖 Generated with RuFlo