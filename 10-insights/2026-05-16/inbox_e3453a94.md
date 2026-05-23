---
id: inbox_e3453a94
date: 2026-05-16
source_ref: "[[00-inbox/2026-05-16/1800-ruflo-releases-v3-7-0-alpha-42-2015-round-2-strip-bogus-40d9]]"
title: "v3.7.0-alpha.42 — #2015 round 2: strip bogus --kind flag"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.42
source: ruflo-releases
published_at: 2026-05-16T13:02:27+00:00
fetched_at: 2026-05-22T18:11:11.702554+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.7.0-alpha.42 為 hotfix，修復 alpha.41 未完整解決的 #2015 bug。Alpha.41 添加 --dimension 384 flag 修復 rvf create 失敗，但遺留 --kind browser-session flag；Commander.js 的 required-option 檢查先於 unknown-option 執行，導致真實錯誤（unknown option）被掩蓋在 dimension 錯誤之下。Alpha.42 移除所有 5 個 call sites（TS 源碼、compiled dist、shell script、browser-record/SKILL.md、browser-agent.md）的 --kind browser-session。強化 smoke-browser-rvf-create-flags.mjs 檢查兩個不變量：--dimension/-d 存在且 --kind 不存在，用明確的 PATHS_IN_SCOPE 列表而非內容錨點。"
key_points:
  - "移除 5 個 rvf create 呼叫位置的 --kind browser-session flag（TS、dist、shell、markdown）"
  - "強化 CI smoke test 同時檢查 --dimension 存在與 --kind 不存在，改用 PATHS_IN_SCOPE 列表避免誤刪錨點"
tags: [bug-fix, command-line-parsing, ci-regression-guard]
topics: []
importance: 1
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.7.0-alpha.42 — #2015 round 2: strip bogus --kind flag

RuFlo v3.7.0-alpha.42 為 hotfix，修復 alpha.41 未完整解決的 #2015 bug。Alpha.41 添加 --dimension 384 flag 修復 rvf create 失敗，但遺留 --kind browser-session flag；Commander.js 的 required-option 檢查先於 unknown-option 執行，導致真實錯誤（unknown option）被掩蓋在 dimension 錯誤之下。Alpha.42 移除所有 5 個 call sites（TS 源碼、compiled dist、shell script、browser-record/SKILL.md、browser-agent.md）的 --kind browser-session。強化 smoke-browser-rvf-create-flags.mjs 檢查兩個不變量：--dimension/-d 存在且 --kind 不存在，用明確的 PATHS_IN_SCOPE 列表而非內容錨點。

### 重點
- 移除 5 個 rvf create 呼叫位置的 --kind browser-session flag（TS、dist、shell、markdown）
- 強化 CI smoke test 同時檢查 --dimension 存在與 --kind 不存在，改用 PATHS_IN_SCOPE 列表避免誤刪錨點

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.7.0-alpha.42)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hotfix on top of alpha.41 — the post-publish live regression check exposed a second-layer bug in the #2015 fix. 
 What round 1 missed 
 ruvector@0.2.25 rvf create accepts only: 
 
 -d, --dimension &lt;n&gt; (required) 
 -m, --metric &lt;metric&gt; (optional, default cosine) 
 
 Round 1 added the required --dimension 384 but left --kind browser-session in place. Commander's required-option check fires before its unknown-option check, so the original bug report ( #2015 ) only ever surfaced the dimension error — there was no way to discover the second layer without actually running the command end-to-end. 
 The live functional check after publishing alpha.41 surfaced it: 
 error: unknown option '--kind'
 
 What changed in alpha.42 
 
 Stripped --kind browser-session from all 5 call sites (TS source, compiled dist, replay-spike.sh , browser-agent.md , browser-record/SKILL.md ) + ADR prose example. 
 Tightened smoke-browser-rvf-create-flags.mjs to police BOTH invariants per line:
 
 --dimension / -d is present 
 --kind is absent 
 
 
 The smoke now uses an explicit PATHS_IN_SCOPE list (round 1's content-anchor was the very flag we just deleted). 
 
 Live functional check (everything green) 
 
 ruvector rvf create --dimension 384 (no --kind ): exit 0 , .rvf file written. 
 Published @claude-flow/cli@3.7.0-alpha.42 dist:113: --dimension present, --kind absent. 
 #2019 vectorBackend/graphAdapter functional test from alpha.41: still passes against @claude-flow/memory@3.0.0-alpha.16 . 
 verify.mjs precondition contract from #1880 : still holds (exit 2 for source-only, exit 1 for built tree with real regressions). 
 
 Packages 
 
 
 
 Package 
 Version 
 
 
 
 
 @claude-flow/cli 
 3.7.0-alpha.42 
 
 
 claude-flow 
 3.7.0-alpha.42 
 
 
 ruflo 
 3.7.0-alpha.42 
 
 
 @claude-flow/memory 
 3.0.0-alpha.16 (unchanged from alpha.41 release) 
 
 
 
 All latest / alpha / v3alpha dist-tags updated. 
 Commit: 905672021 
 🤖 Generated with RuFlo

</details>