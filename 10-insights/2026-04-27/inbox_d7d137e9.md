---
id: inbox_d7d137e9
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/0248-medium-tag-claude-openclaw-broke-my-agents-again-here-is-t-d501]]"
title: "OpenClaw broke my agents again. Here is the 4-hour rabbit hole that fixed them."
url: https://medium.com/@ulmeanuadrian/openclaw-broke-my-agents-again-here-is-the-4-hour-rabbit-hole-that-fixed-them-192c9c60505c?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-04-27T22:48:24+00:00
fetched_at: 2026-04-28T03:05:50.205957+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文報告 OpenClaw 2026.4.24+ 版本引入的模型引用規範化導致 Claude Max OAuth 認證失敗。問題根源：配置中 `claude-cli/claude-sonnet-4-6` 被規範化為 `anthropic/claude-sonnet-4-6`，但路由邏輯只檢查 `claude-cli` 鍵，導致匹配失敗並降級至 PI Engine（缺少必要的 `anthropic-billing-header`、誤計費為額外用量而非 Claude Max 配額）。修復方案：在 `cliBackends` 同時配置 `claude-cli` 和 `anthropic` 兩個鍵。版本兼容性：≤2026.4.15 無此問題，≥2026.4.24 需套用修復。"
key_points:
  - "版本 2026.4.24+ 模型引用規範化：`claude-cli/` 自動轉為 `anthropic/`，路由邏輯失配"
  - "後果：降級至 PI Engine，喪失 Claude Max 計費，導致額外費用"
  - "修復：`cliBackends` 配置同時包含 `claude-cli` 和 `anthropic` 鍵"
tags: [openclaw, oauth, configuration, claude-max, bug-fix]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## OpenClaw broke my agents again. Here is the 4-hour rabbit hole that fixed them.

本文報告 OpenClaw 2026.4.24+ 版本引入的模型引用規範化導致 Claude Max OAuth 認證失敗。問題根源：配置中 `claude-cli/claude-sonnet-4-6` 被規範化為 `anthropic/claude-sonnet-4-6`，但路由邏輯只檢查 `claude-cli` 鍵，導致匹配失敗並降級至 PI Engine（缺少必要的 `anthropic-billing-header`、誤計費為額外用量而非 Claude Max 配額）。修復方案：在 `cliBackends` 同時配置 `claude-cli` 和 `anthropic` 兩個鍵。版本兼容性：≤2026.4.15 無此問題，≥2026.4.24 需套用修復。

### 重點
- 版本 2026.4.24+ 模型引用規範化：`claude-cli/` 自動轉為 `anthropic/`，路由邏輯失配
- 後果：降級至 PI Engine，喪失 Claude Max 計費，導致額外費用
- 修復：`cliBackends` 配置同時包含 `claude-cli` 和 `anthropic` 鍵

**原文：** [medium-tag-claude](https://medium.com/@ulmeanuadrian/openclaw-broke-my-agents-again-here-is-the-4-hour-rabbit-hole-that-fixed-them-192c9c60505c?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@ulmeanuadrian/openclaw-broke-my-agents-again-here-is-the-4-hour-rabbit-hole-that-fixed-them-192c9c60505c?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/1426/1*H_UZf8zeu1JWr9TqtpLojw.png" width="1426" /></a></p><p class="medium-feed-snippet">Your agents fall back to the PI engine, which can&apos;t authenticate Claude Max OAuth. Here&apos;s the exact config fix.</p><p class="medium-feed-link"><a href="https://medium.com/@ulmeanuadrian/openclaw-broke-my-agents-again-here-is-the-4-hour-rabbit-hole-that-fixed-them-192c9c60505c?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>