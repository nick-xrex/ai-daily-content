---
id: inbox_0e3626d6
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-codex-releases-0-130-0-a829]]"
title: "0.130.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.130.0
source: codex-releases
published_at: 2026-05-08T23:10:31+00:00
fetched_at: 2026-05-09T01:55:36.856689+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Codex 0.130.0 發布，新增多項功能與修復 40+ 個 bug。新功能：(1) Plugin 詳情頁面現在展示 bundled hooks 與共享 metadata，支援 discoverability 控制；(2) codex remote-control 指令簡化 headless 伺服器啟動，支援自動化部署；(3) App-server thread pagination API 支援大型執行緒分頁載入（unloaded/summary/full 三種檢視），解決大規模對話記錄的效能問題。Bug 修復涵蓋 live 組態熱重載、turn diff 一致性、Windows sandbox 權限、OAuth 刷新令牌併發等。"
key_points:
  - "Plugin 共享新增 metadata 和 discoverability 控制——改善 plugin 發現與分享體驗"
  - "codex remote-control headless 伺服器入口點——簡化自動化部署與遠端控制場景"
  - "App-server thread pagination 支援大型執行緒分頁載入（unloaded/summary/full 檢視）——解決大規模對話記錄效能問題"
tags: [codex, openai, plugin, headless-server, pagination]
topics: [foundation_models.gpt]
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.130.0

Codex 0.130.0 發布，新增多項功能與修復 40+ 個 bug。新功能：(1) Plugin 詳情頁面現在展示 bundled hooks 與共享 metadata，支援 discoverability 控制；(2) codex remote-control 指令簡化 headless 伺服器啟動，支援自動化部署；(3) App-server thread pagination API 支援大型執行緒分頁載入（unloaded/summary/full 三種檢視），解決大規模對話記錄的效能問題。Bug 修復涵蓋 live 組態熱重載、turn diff 一致性、Windows sandbox 權限、OAuth 刷新令牌併發等。

### 重點
- Plugin 共享新增 metadata 和 discoverability 控制——改善 plugin 發現與分享體驗
- codex remote-control headless 伺服器入口點——簡化自動化部署與遠端控制場景
- App-server thread pagination 支援大型執行緒分頁載入（unloaded/summary/full 檢視）——解決大規模對話記錄效能問題

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.130.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Plugin details now show bundled hooks, and plugin sharing exposes link metadata plus discoverability controls. ( #21447 , #21495 , #21637 ) 
 Added codex remote-control as a simpler entrypoint for starting a headless, remotely controllable app-server. ( #21424 ) 
 App-server clients can page large threads with unloaded, summary, or full turn item views. ( #21566 ) 
 Bedrock auth can now use AWS console-login credentials from aws login profiles. ( #21623 ) 
 view_image can resolve files through the selected environment for multi-environment sessions. ( #21143 ) 
 
 Bug Fixes 
 
 Live app-server threads now pick up config changes without requiring a restart. ( #21187 ) 
 Turn diffs stay accurate across apply-patch operations, including partial failures that still mutated files. ( #21180 , #21518 ) 
 Thread summaries, renames, resume, and fork paths work better through ThreadStore , including threads without local rollout paths. ( #21264 , #21265 , #21266 ) 
 Remote compaction now emits response.processed for v2 streams and avoids sending service_tier on API-key compact requests. ( #21642 , #21676 ) 
 Windows sandbox setup now grants sandbox users access to the desktop runtime binary cache. ( #21564 ) 
 Removed stale “research preview” wording from the codex exec startup banner. ( #21683 ) 
 
 Documentation 
 
 Fixed issue templates so CLI reports keep the intended guidance, labels apply correctly, and feature requests link to the right contributing docs. ( #21685 , #21686 , #21688 ) 
 Updated install and tooling docs to consistently use cargo install --locked . ( #21592 ) 
 
 Chores 
 
 Added a faster Cargo profiling build profile and disabled empty doctest targets to speed up Rust development loops. ( #21574 , #21584 ) 
 Hardened dependency and CI hygiene with fully qualified GitHub Action pins, a Dependabot cooldown, and a cargo-shear upgrade. ( #21436 , #21547 , #21599 ) 
 Simplified internal surfaces by removing unused device-key APIs, extra skills roots, the remote thread-store implementation, and string-keyed MCP tool maps. ( #21487 , #21485 , #21596 , #21454 ) 
 Added configurable OpenTelemetry trace metadata and richer review/feedback analytics for better debugging and triage. ( #21556 , #18747 , #21434 , #21498 ) 
 
 Changelog 
 Full Changelog: rust-v0.129.0...rust-v0.130.0 
 
 #21494 [codex] fix PluginListParams test initializer @xli-oai 
 #21447 Show plugin hooks in plugin details @abhinav-oai 
 #21356 feat: make built-in MCPs first-class runtime servers @jif-oai 
 #21180 Make turn diff tracking operation backed @jif-oai 
 #21498 [codex] add account id to feedback uploads @pakrym-oai 
 #21487 device-key: clean up unused crate @euroelessar 
 #21518 fix: preserve exact turn diffs after partial apply_patch failures @jif-oai 
 #18747 [codex-analytics] add tool review event schema @rhan-oai 
 #21495 feat: Expose plugin share metadata in shareContext @xl-openai 
 #21454 [codex] Remove string-keyed MCP tool maps @pakrym-oai 
 #21424 add top-level remote-control command @owenlin0 
 #21187 app-server: refresh live threads from latest config snapshot @jif-oai 
 #21461 [codex] Move tool specs onto handlers @pakrym-oai 
 #21547 Upgrade cargo-shear to 1.11.2 @charliemarsh-oai 
 #21264 Move thread name edits to ThreadStore @wiltzius-openai 
 #21266 [codex] Fix pathless thread summaries @wiltzius-openai 
 #21265 Route ThreadManager rollout path reads through thread store @wiltzius-openai 
 #21564 Grant sandbox users access to desktop runtime bin @iceweasel-oai 
 #21582 Use descriptive names for Cargo profile options @zanie-oai 
 #21574 Add a Cargo build profile for benchmarking @zanie-oai 
 #21436 [codex] Fully qualify hash-pins in GitHub Actions @ww-oai 
 #21592 Ensure all mentions of cargo-install are --locked @gankra-oai 
 #21584 Disable empty Cargo test targets @charliemarsh-oai 
 #21566 feat(app-server, threadstore): Thread pagination APIs and ThreadStore contract @owenlin0 
 #21556 codex-otel: add configurable trace metadata @bbrown-oai 
 #21599 [codex] Apply a Dependabot cooldown of 7 days @ww-oai 
 #21602 Use --locked in cargo build and lint invocations @zanie-oai 
 #20664 Add stdio exec-server client transport @starr-openai 
 #21596 [codex] Remove remote thread store implementation @wiltzius-openai 
 #20665 Make environment providers own default selection @starr-openai 
 #21143 Route view_image through selected environments @starr-openai 
 #20666 Add CODEX_HOME environments TOML provider @starr-openai 
 #21642 Send response.processed after remote compaction v2 @pakrym-oai 
 #21646 Revert "Use --locked in cargo build and lint invocations" @pakrym-oai 
 #21434 [codex-analytics] plumb protocol-native review timing @rhan-oai 
 #21485 Remove skills list extra roots @xli-oai 
 #21623 feat: enable AWS login credentials for Bedrock auth @celia-oai 
 #21637 feat: Update plugin share settings with discoverability @xl-openai 
 #21685 Fix duplicate CLI issue template description @etraut-openai 
 #21686 Fix issue template labels @etraut-openai 
 #21688 Fix feature request Contributing link @etraut-openai 
 #21683 Remove exec research preview banner wording @etraut-openai 
 #21676 Omit service_tier from remote /responses/compact requests under API auth @aibrahim-oai

</details>