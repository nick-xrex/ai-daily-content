---
id: inbox_7688d9be
date: 2026-05-15
source_ref: "[[00-inbox/2026-05-15/0036-simon-willison-datasette-agent-0-1a2-e967]]"
title: "datasette-agent 0.1a2"
url: https://simonwillison.net/2026/May/15/datasette-agent/#atom-everything
source: simon-willison
published_at: 2026-05-15T00:03:00+00:00
fetched_at: 2026-05-22T00:41:25.760689+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-agent 0.1a2 發布新增權限系統功能。工具現在可附加到 required_permission，預設背景代理工具需要新的 datasette-agent-background 權限。這是細粒度權限控制的進一步演進，使代理工具的使用更加受控。"
key_points:
  - "Tool availability 支援 required_permission 屬性，實現細粒度權限附加"
  - "datasette-agent-background permission 成為預設背景工具的必需權限"
  - "權限系統設計逐步成熟，支援更複雜的存取控制場景"
tags: [datasette-agent, permissions, api-security]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent 0.1a2

datasette-agent 0.1a2 發布新增權限系統功能。工具現在可附加到 required_permission，預設背景代理工具需要新的 datasette-agent-background 權限。這是細粒度權限控制的進一步演進，使代理工具的使用更加受控。

### 重點
- Tool availability 支援 required_permission 屬性，實現細粒度權限附加
- datasette-agent-background permission 成為預設背景工具的必需權限
- 權限系統設計逐步成熟，支援更複雜的存取控制場景

**原文：** [simon-willison](https://simonwillison.net/2026/May/15/datasette-agent/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent 0.1a2 
 
 
 Tool availability can now be attached to a required_permission . The default background agent tools now require the new datasette-agent-background permission. #10 
 
 
 
 
 Tags: datasette , datasette-agent

</details>