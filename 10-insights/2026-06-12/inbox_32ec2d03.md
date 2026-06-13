---
id: inbox_32ec2d03
date: 2026-06-12
source_ref: "[[00-inbox/.../inbox_32ec2d03]]"
title: "v3.10.43 — Fable 5 / Opus 4.x temperature fix, daemon TTL, federation cap"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.43
source: ruflo-releases
published_at: 2026-06-12T14:58:21+00:00
fetched_at: 2026-06-13T04:10:04.850117+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.43 修復四個重要問題。最關鍵（#2358）：Fable 5、Opus 4.8、Opus 4.7 移除了 temperature/top_p/top_k 參數，導致所有請求返回 400 invalid_request_error: temperature: Extra inputs are not permitted，修復通過新增 modelRejectsSamplingParams(model) 謂詞條件發送。其次 OpenRouter 模型 slug 刷新（#2365）：更新 Oct-2025 退役 ID 到 4.x 家族（claude-3.5-sonnet → claude-sonnet-4-6）。第三 daemon 自終止 TTL（#2361）：發現 6 個不死後台程序（最老 19 天）在 1-2 天內耗盡 Max-plan 配額，94% token 花在背景任務。第四 federation 版本約束（#2364）：agentic-flow peer 限制到 <2.0.13。"
key_points:
  - "新模型移除採樣參數：Fable 5/Opus 4.8/4.7 刪除 temperature/top_p/top_k，需條件發送以避免 400 錯誤；Sonnet 4.6/Haiku 4.5/Opus ≤4.6 保留"
  - "後台程序配額洩漏關鍵數據：6 個長生命週期 daemon（最老 19 天）、17 個 per-project daemon、34,533 total worker runs、94% token 耗在背景機制，修復添加自終止 TTL 和空閒關閉"
  - "OpenRouter 模型 ID 映射更新：claude-3.5-sonnet/haiku/opus 的 Oct-2025 退役 slug 重映射到 claude-sonnet-4-6/haiku-4-5/opus-4-8"
tags: [ruflo, fable-5, opus-4.x, model-compatibility, daemon-leak, openrouter]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.43 — Fable 5 / Opus 4.x temperature fix, daemon TTL, federation cap

Ruflo v3.10.43 修復四個重要問題。最關鍵（#2358）：Fable 5、Opus 4.8、Opus 4.7 移除了 temperature/top_p/top_k 參數，導致所有請求返回 400 invalid_request_error: temperature: Extra inputs are not permitted，修復通過新增 modelRejectsSamplingParams(model) 謂詞條件發送。其次 OpenRouter 模型 slug 刷新（#2365）：更新 Oct-2025 退役 ID 到 4.x 家族（claude-3.5-sonnet → claude-sonnet-4-6）。第三 daemon 自終止 TTL（#2361）：發現 6 個不死後台程序（最老 19 天）在 1-2 天內耗盡 Max-plan 配額，94% token 花在背景任務。第四 federation 版本約束（#2364）：agentic-flow peer 限制到 <2.0.13。

### 重點
- 新模型移除採樣參數：Fable 5/Opus 4.8/4.7 刪除 temperature/top_p/top_k，需條件發送以避免 400 錯誤；Sonnet 4.6/Haiku 4.5/Opus ≤4.6 保留
- 後台程序配額洩漏關鍵數據：6 個長生命週期 daemon（最老 19 天）、17 個 per-project daemon、34,533 total worker runs、94% token 耗在背景機制，修復添加自終止 TTL 和空閒關閉
- OpenRouter 模型 ID 映射更新：claude-3.5-sonnet/haiku/opus 的 Oct-2025 退役 slug 重映射到 claude-sonnet-4-6/haiku-4-5/opus-4-8

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.43)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.10.43 — Fable 5 / Opus 4.x temperature fix, daemon TTL, federation cap

Patch release bundling four bug fixes landed since 3.10.42. 
 Fixes 
 #2358 — agent_execute 400s every current frontier Anthropic model (HIGH) 
 callAnthropicMessages() always sent temperature (default 0.7), but Fable 5, Opus 4.8, and Opus 4.7 removed temperature / top_p / top_k . Every request returned 400 invalid_request_error: temperature: Extra inputs are not permitted . Invisible on Claude-Max (no key → provider check short-circuits before fetch); fatal on a raw ANTHROPIC_API_KEY . New modelRejectsSamplingParams(model) predicate gates the field; Sonnet 4.6 / Haiku 4.5 / Opus ≤ 4.6 unchanged. Closes #2357 Finding A. (HF-teamdev — first-time contributor, thank you for the file:line-cited finding map.) 
 #2365 — OpenRouter slugs refreshed to current 4.x family 
 The OpenAI-compat path still referenced the Oct-2025 retired model IDs: 
 
 default model: anthropic/claude-3.5-sonnet → anthropic/claude-sonnet-4-6 
 haiku alias: anthropic/claude-3.5-haiku → anthropic/claude-haiku-4-5 
 sonnet / inherit alias: anthropic/claude-3.5-sonnet → anthropic/claude-sonnet-4-6 
 opus alias: anthropic/claude-3-opus → anthropic/claude-opus-4-8 
 
 OPENROUTER_DEFAULT_MODEL still wins for callers who want to pin a specific slug. Closes #2357 Finding C. 
 #2361 — daemon self-terminating TTL + global status + HNSW/init footguns 
 Community PR by @shaal addressing @pacphi 's ruflo-machine-ref investigation. The daemon used to run interval workers (audit ~30m, optimize/testgaps ~60m, ...) forever, each spawning a headless claude --print sweep. Audited evidence traced a Max-plan quota burned in 1–2 days to 6 immortal daemons (oldest 19 days) and a recurrence to 17 per-project daemons (34,533 total worker runs — ~94% of token spend was background machinery). This release adds: self-terminating TTL, idle shutdown, daemon status --all (global, not just current workspace), honest HNSW reporting, init footgun guards. Closes #2360 . 
 #2364 — federation plugin: cap agentic-flow peer to &lt;2.0.13 
 Upstream agentic-flow@2.0.13 dropped the ./transport/loader subpath. Runtime impact was bounded — midstream-aware-loader.ts wraps the dynamic import in try/catch and falls back to midstream-native — but the peer range previously said &gt;=2.0.12-fix.8 and silently accepted 2.0.13. Tightened to &gt;=2.0.12-fix.8 &lt;2.0.13 so npm install warns about the incompat instead of hiding it behind a silent fallback. 
 Still open from #2357 
 
 Finding B (Fable routing tier RFC, PR #2359 ) — behavior-neutral, 21/21 tests green, awaiting maintainer decision before the June 22 Max-plan API-credits window. Review comment on the PR lays out the three design calls. 
 
 Install / upgrade 
 npx ruflo@latest init # 3.10.43 
npx @claude-flow/cli@latest # 3.10.43 
 All three packages ( @claude-flow/cli , claude-flow , ruflo ) and all three dist-tags ( latest , alpha , v3alpha ) verified at 3.10.43. 
 Diff 
 main...v3.10.42 — PRs #2358 , #2361 , #2364 , #2365 plus the release bump. 
 🤖 Generated with RuFlo

</details>