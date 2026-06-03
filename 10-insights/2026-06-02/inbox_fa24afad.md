---
id: inbox_fa24afad
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0030-medium-tag-claude-one-missing-tool-in-aem-mcp-registry-and-aafc]]"
title: "One missing tool in AEM MCP registry.. and how to build it on AIO.."
url: https://medium.com/@bsaravanaprakash/one-missing-tool-in-aem-mcp-registry-and-how-to-build-it-on-aio-902cc13b1afa?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-02T19:32:00+00:00
fetched_at: 2026-06-03T00:44:37.336581+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Adobe Experience Manager (AEM) MCP 工具欠缺案例研究。官方 MCP registry 含有 `publish-aem-content` 但缺乏 `preview-aem-content` 工具，導致開發人員無法在不發佈的情況下預覽內容變更。作者使用 `@adobe/generator-app-remote-mcp-server-generic` 範本在 Adobe I/O AppBuilder 實現該工具：新建 AppBuilder 專案 → 撰寫 echo + preview-pages 兩個工具（後者向 AEM `/bin/replicate.json` 端點發送 POST，agentId 設為 preview） → 部署到 AppBuilder → 在 Claude Desktop config 註冊。目前使用 BasicAuth，未來規劃 OAuth。"
key_points:
  - "AEM MCP registry 缺少 preview 工具，開發人員需自建"
  - "使用 AppBuilder remote-mcp-server 範本 4 步快速實現（init → code → deploy → config）"
  - "Preview 工具向 /bin/replicate.json 發送 agentId=preview POST，與 publish 工具邏輯平行"
tags: [aem, mcp, adobe-io, appbuilder, custom-tool]
topics: [agents.mcp]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## One missing tool in AEM MCP registry.. and how to build it on AIO..

Adobe Experience Manager (AEM) MCP 工具欠缺案例研究。官方 MCP registry 含有 `publish-aem-content` 但缺乏 `preview-aem-content` 工具，導致開發人員無法在不發佈的情況下預覽內容變更。作者使用 `@adobe/generator-app-remote-mcp-server-generic` 範本在 Adobe I/O AppBuilder 實現該工具：新建 AppBuilder 專案 → 撰寫 echo + preview-pages 兩個工具（後者向 AEM `/bin/replicate.json` 端點發送 POST，agentId 設為 preview） → 部署到 AppBuilder → 在 Claude Desktop config 註冊。目前使用 BasicAuth，未來規劃 OAuth。

### 重點
- AEM MCP registry 缺少 preview 工具，開發人員需自建
- 使用 AppBuilder remote-mcp-server 範本 4 步快速實現（init → code → deploy → config）
- Preview 工具向 /bin/replicate.json 發送 agentId=preview POST，與 publish 工具邏輯平行

**原文：** [medium-tag-claude](https://medium.com/@bsaravanaprakash/one-missing-tool-in-aem-mcp-registry-and-how-to-build-it-on-aio-902cc13b1afa?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A step-by-step guide to run custom MCP server from AIO AppBuilder using remote-mcp-server-starter template Continue reading on Medium »

</details>