---
id: inbox_c8d3ec7a
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/0657-claude-code-releases-v2-1-123-4ce4]]"
title: "v2.1.123"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.123
source: claude-code-releases
published_at: 2026-04-29T03:29:13+00:00
fetched_at: 2026-04-29T07:01:50.730311+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.123 修復了特定環境設定下的驗證問題。當 CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS=1 環境變數被設定時，OAuth 驗證會陷入 401 重試迴圈，導致使用者無法成功登入。這個問題影響所有使用該環境變數禁用實驗性功能的使用者。修復後，OAuth 流程能正常完成，使用者可以直接通過驗證。這是一個關鍵的緊急修補，確保配置該環境變數的部署仍能正常運行。"
key_points:
  - "修復 OAuth 401 重試迴圈，特定於 CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS=1 環境設定"
  - "v2.1.123 版本發布"
tags: [claude-code, bug-fix, oauth, authentication]
topics: [foundation_models.claude]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.123

Claude Code v2.1.123 修復了特定環境設定下的驗證問題。當 CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS=1 環境變數被設定時，OAuth 驗證會陷入 401 重試迴圈，導致使用者無法成功登入。這個問題影響所有使用該環境變數禁用實驗性功能的使用者。修復後，OAuth 流程能正常完成，使用者可以直接通過驗證。這是一個關鍵的緊急修補，確保配置該環境變數的部署仍能正常運行。

### 重點
- 修復 OAuth 401 重試迴圈，特定於 CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS=1 環境設定
- v2.1.123 版本發布

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.123)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Fixed OAuth authentication failing with a 401 retry loop when <code>CLAUDE_CODE_DISABLE_EXPERIMENTAL_BETAS=1</code> is set</li>
</ul>

</details>