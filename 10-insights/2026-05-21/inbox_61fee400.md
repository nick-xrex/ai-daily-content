---
id: inbox_61fee400
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/0917-medium-tag-claude-how-li-fi-added-enterprise-auth-to-apach-8a37]]"
title: "How LI.FI Added Enterprise Auth to Apache Superset’s MCP Server"
url: https://medium.com/@onurtashan/how-li-fi-added-enterprise-auth-to-apache-supersets-mcp-server-5fe886e29a61?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-21T07:19:22+00:00
fetched_at: 2026-05-21T09:29:23.761856+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LI.FI 為 Apache Superset 的 MCP server 實現企業級身份驗證架構，集成 Okta SSO 單點登錄與多用戶 RBAC 權限控制，支持 claude.ai 接入，並部署於 AWS EKS 環境。該實踐為 MCP 應用於企業場景提供了完整的安全認證方案，使團隊能安全地共享和授權 Superset 分析能力。"
key_points:
  - "Okta SSO 整合實現企業級單點登錄，簡化身份驗證流程"
  - "多用戶 RBAC 模型提供角色級存取控制，細粒度權限管理"
  - "AWS EKS 容器化部署，支持 claude.ai 雲端接入與大規模協作"
tags: [mcp-enterprise-integration, okta-sso, rbac, apache-superset, aws-eks]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## How LI.FI Added Enterprise Auth to Apache Superset’s MCP Server

LI.FI 為 Apache Superset 的 MCP server 實現企業級身份驗證架構，集成 Okta SSO 單點登錄與多用戶 RBAC 權限控制，支持 claude.ai 接入，並部署於 AWS EKS 環境。該實踐為 MCP 應用於企業場景提供了完整的安全認證方案，使團隊能安全地共享和授權 Superset 分析能力。

### 重點
- Okta SSO 整合實現企業級單點登錄，簡化身份驗證流程
- 多用戶 RBAC 模型提供角色級存取控制，細粒度權限管理
- AWS EKS 容器化部署，支持 claude.ai 雲端接入與大規模協作

**原文：** [medium-tag-claude](https://medium.com/@onurtashan/how-li-fi-added-enterprise-auth-to-apache-supersets-mcp-server-5fe886e29a61?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Making Superset&#x2019;s built-in MCP server work with Okta SSO, multi-user RBAC, and claude.ai on AWS EKS Continue reading on Medium »

</details>