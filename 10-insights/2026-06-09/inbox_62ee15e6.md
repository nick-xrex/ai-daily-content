---
id: inbox_62ee15e6
date: 2026-06-09
source_ref: "[[00-inbox/2026-06-09/2200-medium-tag-claude-how-to-auto-approve-claude-code-cli-prom-70a9]]"
title: "How to Auto-Approve Claude Code CLI Prompts (Even When Your Org Disables the Bypass Flag)"
url: https://arusharma.medium.com/how-to-auto-approve-claude-code-cli-prompts-even-when-your-org-disables-the-bypass-flag-be0402f16da9?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-09T20:37:55+00:00
fetched_at: 2026-06-09T22:13:28.652967+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章揭露企業禁用 Claude Code CLI 官方 `--dangerously-skip-permissions` 旗標後的自動化方案：使用 Unix 系統工具 `expect` 來監控互動式命令行提示，在檢測到「Do you want to proceed?」後自動發送 Enter 鍵（延遲 200 毫秒以容納 ANSI 轉義碼渲染），透過別名簡化為 `claude-auto` 指令。這個方案技術上規避組織策略限制，無需修改官方安全機制，適用於頻繁批准重複提示的開發工作流。"
key_points:
  - "使用 `expect` 腳本監控 CLI 提示並自動回應，200 毫秒延遲確保 ANSI 轉義碼完全渲染後才送鍵"
  - "建立 shell 別名簡化調用：`alias claude-auto=\"/path/to/claude-auto.exp\"`"
  - "技術上符合禁用 `--dangerously-skip-permissions` 的組織政策，同時實現自動審批流，避免手動重複確認的生產力損失"
tags: [claude-code-cli, automation, expect-script, permission-bypass]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How to Auto-Approve Claude Code CLI Prompts (Even When Your Org Disables the Bypass Flag)

文章揭露企業禁用 Claude Code CLI 官方 `--dangerously-skip-permissions` 旗標後的自動化方案：使用 Unix 系統工具 `expect` 來監控互動式命令行提示，在檢測到「Do you want to proceed?」後自動發送 Enter 鍵（延遲 200 毫秒以容納 ANSI 轉義碼渲染），透過別名簡化為 `claude-auto` 指令。這個方案技術上規避組織策略限制，無需修改官方安全機制，適用於頻繁批准重複提示的開發工作流。

### 重點
- 使用 `expect` 腳本監控 CLI 提示並自動回應，200 毫秒延遲確保 ANSI 轉義碼完全渲染後才送鍵
- 建立 shell 別名簡化調用：`alias claude-auto="/path/to/claude-auto.exp"`
- 技術上符合禁用 `--dangerously-skip-permissions` 的組織政策，同時實現自動審批流，避免手動重複確認的生產力損失

**原文：** [medium-tag-claude](https://arusharma.medium.com/how-to-auto-approve-claude-code-cli-prompts-even-when-your-org-disables-the-bypass-flag-be0402f16da9?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

If you&#x2019;ve been using Anthropic&#x2019;s new Claude Code CLI, you already know it&#x2019;s a game-changer. Having an AI agent that can navigate your&#x2026; Continue reading on Medium »

</details>