---
id: inbox_a9f6aaef
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-medium-tag-claude-setting-up-gitlab-mcp-for-claude-code-in-b36b]]"
title: "Setting up Gitlab MCP for Claude Code in 3 steps"
url: https://grassrootengineer.medium.com/setting-up-gitlab-mcp-for-claude-code-in-3-steps-4b082a49c0d9?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-07-04T17:39:56+00:00
fetched_at: 2026-07-04T22:12:35.060620+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "本文介紹如何用三個簡單步驟將 GitLab MCP 整合到 Claude Code。第一步：在 GitLab 中建立個人存取令牌（api、read_api、read_user 作用域，有效期約一年）。第二步：修改 ~/.claude.json 配置檔，在 mcpServers 區段新增 GitLab 條目，使用 stdio 連線型別。第三步文章中未完整揭露。本指南強調此方法適用於單一儲存庫配置，而非全域設定。"
key_points:
  - "建立 GitLab PAT 需設定 api、read_api、read_user 作用域"
  - "透過修改 ~/.claude.json 在 mcpServers 中新增 GitLab MCP 配置"
  - "採用 stdio 連線型別實現整合"
tags: [claude-code, mcp, gitlab, integration, setup]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Setting up Gitlab MCP for Claude Code in 3 steps

本文介紹如何用三個簡單步驟將 GitLab MCP 整合到 Claude Code。第一步：在 GitLab 中建立個人存取令牌（api、read_api、read_user 作用域，有效期約一年）。第二步：修改 ~/.claude.json 配置檔，在 mcpServers 區段新增 GitLab 條目，使用 stdio 連線型別。第三步文章中未完整揭露。本指南強調此方法適用於單一儲存庫配置，而非全域設定。

### 重點
- 建立 GitLab PAT 需設定 api、read_api、read_user 作用域
- 透過修改 ~/.claude.json 在 mcpServers 中新增 GitLab MCP 配置
- 採用 stdio 連線型別實現整合

**原文：** [medium-tag-claude](https://grassrootengineer.medium.com/setting-up-gitlab-mcp-for-claude-code-in-3-steps-4b082a49c0d9?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Prerequisites Continue reading on Medium »

</details>