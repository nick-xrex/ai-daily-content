---
id: inbox_1a4a47a8
date: 2026-07-04
source_ref: "[[00-inbox/.../inbox_1a4a47a8]]"
title: "Release Candidate v1.6.10-rc.1"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.1
source: gitnexus-releases
published_at: 2026-07-04T10:13:38+00:00
fetched_at: 2026-07-05T01:42:20.745353+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.1 版本發布，這是 1.6.10 穩定版的首個發布候選版本，基於 main 分支的 6252aa7 提交。本版本新增 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理集成功能，透過編輯器目標註冊表（editor-targets registry）和 --coding-agent 選項進行集成。相較後續的 rc.2，該版本功能較為精簡，主要聚焦在編碼代理集成，尚未納入完整的 Codex 支持。用戶可透過 npm install gitnexus@rc 安裝測試本預發布版本。"
key_points:
  - "新增 CodeBuddy 和 Qoder 編碼代理 MCP 集成，接入 editor-targets 和 --coding-agent 選項"
  - "版本 v1.6.10-rc.1 基於 commit 6252aa7，是該版本系列的首個 RC"
  - "功能相對精簡的早期 RC，完整 Codex 支持將在 rc.2 納入"
tags: [gitnexus, mcp-integration, coding-agents, rc-version]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.1

GitNexus v1.6.10-rc.1 版本發布，這是 1.6.10 穩定版的首個發布候選版本，基於 main 分支的 6252aa7 提交。本版本新增 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理集成功能，透過編輯器目標註冊表（editor-targets registry）和 --coding-agent 選項進行集成。相較後續的 rc.2，該版本功能較為精簡，主要聚焦在編碼代理集成，尚未納入完整的 Codex 支持。用戶可透過 npm install gitnexus@rc 安裝測試本預發布版本。

### 重點
- 新增 CodeBuddy 和 Qoder 編碼代理 MCP 集成，接入 editor-targets 和 --coding-agent 選項
- 版本 v1.6.10-rc.1 基於 commit 6252aa7，是該版本系列的首個 RC
- 功能相對精簡的早期 RC，完整 Codex 支持將在 rc.2 納入

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.1

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.1 \n Target base: 1.6.10 (rc #1 )\n Source commit (main): 6252aa7 \n Release commit (versioned tree): c3d8b30 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 
 Full Changelog : v1.6.9...v1.6.10-rc.1

</details>