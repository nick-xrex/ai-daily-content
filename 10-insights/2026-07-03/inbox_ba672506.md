---
id: inbox_ba672506
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-simon-willison-fable-s-judgement-1125]]"
title: "Fable&#39;s judgement"
url: https://simonwillison.net/2026/Jul/3/judgement/#atom-everything
source: simon-willison
published_at: 2026-07-03T18:51:06+00:00
fetched_at: 2026-07-04T01:23:13.277698+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 引述 Claude Code 團隊的關鍵建議：賦予 Fable/Opus 自主判斷權勝於規定工作方式。例如測試策略，應告知模型「僅為大功能自動化測試，小改動無需測試」，讓其自主決策，而非設立嚴格規則。進一步地，可委派小型任務給低階模型（Sonnet/Haiku），由 Fable 自主判斷模型選擇，藉此節省寶貴的 Fable tokens。Willison 已測試此方法，報告工作效率顯著提升，token 消耗速度明顯放緩。"
key_points:
  - "核心框架：賦予 Fable 自主判斷權，勿過度指導工作方式（例如測試策略）"
  - "委派策略：小型任務自動降級至 Sonnet/Haiku，由 Fable 自主判斷模型選擇，節省 token 成本"
  - "實測結果：自主判斷委派策略下，工作效率提升且 token 消耗速度明顯低於 Fable-only 方案"
tags: [claude-code, prompt-engineering, token-optimization, fable, model-delegation]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Fable's judgement

Simon Willison 引述 Claude Code 團隊的關鍵建議：賦予 Fable/Opus 自主判斷權勝於規定工作方式。例如測試策略，應告知模型「僅為大功能自動化測試，小改動無需測試」，讓其自主決策，而非設立嚴格規則。進一步地，可委派小型任務給低階模型（Sonnet/Haiku），由 Fable 自主判斷模型選擇，藉此節省寶貴的 Fable tokens。Willison 已測試此方法，報告工作效率顯著提升，token 消耗速度明顯放緩。

### 重點
- 核心框架：賦予 Fable 自主判斷權，勿過度指導工作方式（例如測試策略）
- 委派策略：小型任務自動降級至 Sonnet/Haiku，由 Fable 自主判斷模型選擇，節省 token 成本
- 實測結果：自主判斷委派策略下，工作效率提升且 token 消耗速度明顯低於 Fable-only 方案

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/3/judgement/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

One of the most interesting tips I got from the Fireside Chat I hosted with Cat Wu and Thariq Shihipar from the Claude Code team at AIE on Wednesday was to let Fable (and to a certain extent Opus) use their own judgement rather than dictating how they should work. 
 The example they gave was testing. You can tell Fable "only use automated testing for larger features, don't update and run tests for small copy or design changes" - but it's better to just tell Fable to use its own judgement when deciding to write tests instead. 
 Jesse Vincent just gave me a related tip to help avoid burning too many of those valuable Fable tokens in the few days we have left before the prices go up. Tell Fable to use other models for smaller tasks, applying its own judgement about which model to use. 
 I prompted Claude Code just now with: 
 
 For all coding tasks use your judgement to decide an appropriate lower power model and run that in a subagent 
 
 Claude saved this memory file in ~/.claude/projects/name-of-project/memory/delegate-coding-to-subagents.md : 
 
 ---
name: delegate-coding-to-subagents
description: Simon wants coding tasks delegated to subagents running an appropriately lower-power model
metadata: 
 node_type: memory
 type: feedback
 originSessionId: 30068d78-43a9-4fb1-bb29-9799e18c526a
---
 
 Stated by Simon on 2026-07-03: "For all coding tasks use your judgement to
decide an appropriate lower power model and run that in a subagent." 
 Why: cost/efficiency — implementation work rarely needs the top-tier
model; judgment, review, and synthesis stay with the main loop. 
 How to apply: when a task in this project is primarily writing/editing
code, spawn an Agent with a model override (sonnet for substantive
implementation, haiku for trivial/mechanical edits) and a self-contained
prompt; review the result in the main loop before committing. Design,
auditing, data synthesis, and anything judgment-heavy stays in the main
model. See also [[project-goals]]. 
 
 So far it seems to be working well. I'm getting a ton of work done and my Fable allowance is shrinking less quickly than before. 

 Tags: claude , ai , claude-code , llms , prompt-engineering , coding-agents , generative-ai , claude-mythos-fable , anthropic

</details>