---
id: inbox_512cb68a
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_512cb68a]]"
title: "The MCP Security Gap No One Is Talking About"
url: https://medium.com/@MCPNest/the-mcp-security-gap-no-one-is-talking-about-f57d98a5fa60?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-17T17:13:48+00:00
fetched_at: 2026-05-18T04:07:02.688585+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "MCP生態擴展至生產環境時面臨系統性安全設計缺陷：現狀為所有團隊成員共享單一Bearer Token，導致權限無差別（實習生與資深工程師同權）且撤銷困難（1人離職牽連全隊重配）。MCPNest Gateway Layer 2提出OAuth-style解決方案：每成員各別Token、工具級Allowlist（細粒度如Alice限資料庫工具）、秒級即時撤銷、Audit log含member_id粒度。作者指出MCP正處OAuth 2010年臨界點，應採「最小權限」原則而非「全員同權」架構，否則一次Credential洩漏等於全工作區暴露。"
key_points:
  - "共享Token缺陷：Credential洩漏=完整工作區暴露，無法實現細粒度權限（實習生無法限制存取部署工具）"
  - "撤銷成本對比：單一Token模型 O(N team size)重配vs Per-member模型秒級delete token O(1)生效"
  - "MCPNest方案：Per-member token + Per-tool allowlist + Audit log(workspace_id/member_id/tool_name/latency_ms/status) —— OAuth臨界點下的最小可行安全態勢"
tags: [mcp-security, access-control, least-privilege, governance, mcpnest]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## The MCP Security Gap No One Is Talking About

MCP生態擴展至生產環境時面臨系統性安全設計缺陷：現狀為所有團隊成員共享單一Bearer Token，導致權限無差別（實習生與資深工程師同權）且撤銷困難（1人離職牽連全隊重配）。MCPNest Gateway Layer 2提出OAuth-style解決方案：每成員各別Token、工具級Allowlist（細粒度如Alice限資料庫工具）、秒級即時撤銷、Audit log含member_id粒度。作者指出MCP正處OAuth 2010年臨界點，應採「最小權限」原則而非「全員同權」架構，否則一次Credential洩漏等於全工作區暴露。

### 重點
- 共享Token缺陷：Credential洩漏=完整工作區暴露，無法實現細粒度權限（實習生無法限制存取部署工具）
- 撤銷成本對比：單一Token模型 O(N team size)重配vs Per-member模型秒級delete token O(1)生效
- MCPNest方案：Per-member token + Per-tool allowlist + Audit log(workspace_id/member_id/tool_name/latency_ms/status) —— OAuth臨界點下的最小可行安全態勢

**原文：** [medium-tag-claude](https://medium.com/@MCPNest/the-mcp-security-gap-no-one-is-talking-about-f57d98a5fa60?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Malasartes"
published_at: 2026-05-17T17:13:48+00:00
fetched_at: 2026-05-17T18:00:43.202287+00:00
content_hash: "4fba71931e73956a4b8cf0796a27505af55d57c799b5e9fdddc1dabe21113c0e"
lang: en
caption_quality: None
raw: true
topics: []
---

# The MCP Security Gap No One Is Talking About

The MCP ecosystem is growing fast. Thousands of servers, dozens of clients, and teams across the industry moving from personal&#x2026; Continue reading on Medium »

</details>