---
id: inbox_a5aec140
date: 2026-07-18
source_ref: "[[00-inbox/.../inbox_a5aec140]]"
title: "0.144.6"
url: https://github.com/openai/codex/releases/tag/rust-v0.144.6
source: codex-releases
published_at: 2026-07-18T13:53:50+00:00
fetched_at: 2026-07-20T00:35:56.931420+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex v0.144.6 發布了針對 GPT-5.6 系列三個新模型（Sol、Terra、Luna）的重要更新。主要變更包括刷新了 bundled instructions（打包指令集）以及統一調整 context window 為 272,000 tokens。這個版本通過兩個 PR（#33972 負責 backport bundled model metadata，#34009 負責 prompts 和 context 的 hotfix）完成。對於依賴 GPT-5.6 系列的開發者和使用者，context window 大小的統一規範直接影響了提示詞規劃和上下文管理策略。"
key_points:
  - "GPT-5.6 Sol、Terra、Luna 的 context window 統一調整為 272,000 tokens"
  - "Bundled instructions 已刷新，確保三個模型行為一致性"
  - "通過 PR #33972 和 #34009 完成元數據 backport 和 hotfix"
tags: [openai-codex, gpt-5-6, model-update, context-window]
topics: [foundation_models.gpt]
importance: 4
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.144.6

OpenAI Codex v0.144.6 發布了針對 GPT-5.6 系列三個新模型（Sol、Terra、Luna）的重要更新。主要變更包括刷新了 bundled instructions（打包指令集）以及統一調整 context window 為 272,000 tokens。這個版本通過兩個 PR（#33972 負責 backport bundled model metadata，#34009 負責 prompts 和 context 的 hotfix）完成。對於依賴 GPT-5.6 系列的開發者和使用者，context window 大小的統一規範直接影響了提示詞規劃和上下文管理策略。

### 重點
- GPT-5.6 Sol、Terra、Luna 的 context window 統一調整為 272,000 tokens
- Bundled instructions 已刷新，確保三個模型行為一致性
- 通過 PR #33972 和 #34009 完成元數據 backport 和 hotfix

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.144.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 0.144.6

Bug Fixes 
 
 Refreshed bundled instructions for GPT-5.6 Sol, Terra, and Luna, and corrected their context windows to 272,000 tokens. ( #33972 , #34009 ) 
 
 Changelog 
 Full Changelog: rust-v0.144.5...rust-v0.144.6 
 
 #33972 Backport refreshed bundled model metadata to 0.144 @sayan-oai 
 #34009 Narrow 0.144 hotfix to GPT-5.6 prompts and context @sayan-oai

</details>