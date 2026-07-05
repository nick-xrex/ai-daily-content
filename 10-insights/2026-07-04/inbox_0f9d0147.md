---
id: inbox_0f9d0147
date: 2026-07-04
source_ref: "[[00-inbox/.../inbox_0f9d0147]]"
title: "Release Candidate v1.6.10-rc.2"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.2
source: gitnexus-releases
published_at: 2026-07-04T13:11:20+00:00
fetched_at: 2026-07-05T01:42:20.682688+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus v1.6.10-rc.2 發布，版本號為 1.6.10-rc.2，基於 main 分支的 187c162 提交。本版本新增 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理的 MCP 集成，支援完整的 setup 和 uninstall 流程。同時實現了完整的 OpenAI Codex 支持，包含 hooks、plugin marketplace 和 setup 功能（PR #2328，取代了之前的 #1131）。這是 1.6.10 的第二個發布候選版本，用戶可透過 npm install gitnexus@rc 命令安裝進行測試。新集成讓 GitNexus 能與主流編碼代理協作，擴展了編輯器生態支持。"
key_points:
  - "新增 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理集成至 setup/uninstall 流程"
  - "完整的 OpenAI Codex 支持：hooks、plugin marketplace、setup 功能集成（PR #2328）"
  - "版本 1.6.10-rc.2 基於 commit 187c162，可透過 npm install gitnexus@rc 安裝測試"
tags: [gitnexus, mcp-integration, coding-agents, codex-support]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Release Candidate v1.6.10-rc.2

GitNexus v1.6.10-rc.2 發布，版本號為 1.6.10-rc.2，基於 main 分支的 187c162 提交。本版本新增 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理的 MCP 集成，支援完整的 setup 和 uninstall 流程。同時實現了完整的 OpenAI Codex 支持，包含 hooks、plugin marketplace 和 setup 功能（PR #2328，取代了之前的 #1131）。這是 1.6.10 的第二個發布候選版本，用戶可透過 npm install gitnexus@rc 命令安裝進行測試。新集成讓 GitNexus 能與主流編碼代理協作，擴展了編輯器生態支持。

### 重點
- 新增 Tencent CodeBuddy 和 Alibaba Qoder 編碼代理集成至 setup/uninstall 流程
- 完整的 OpenAI Codex 支持：hooks、plugin marketplace、setup 功能集成（PR #2328）
- 版本 1.6.10-rc.2 基於 commit 187c162，可透過 npm install gitnexus@rc 安裝測試

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/v1.6.10-rc.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Release Candidate v1.6.10-rc.2

Automated release candidate build from main .\n\n npm: npm install gitnexus@rc \n Version: 1.6.10-rc.2 \n Target base: 1.6.10 (rc #2)\n Source commit (main): 187c162 \n Release commit (versioned tree): 3fc3ab0 \n\nRelease candidates are pre-stable builds intended for early testing. Stable releases remain on the latest dist-tag. 

 What's Changed 
 📝 Other Changes 
 
 feat(setup): add CodeBuddy and Qoder coding-agent integrations by @magyargergo in #2368 
 feat: full Codex support — hooks, plugin marketplace, and setup ( #2328 , supersedes #1131 ) by @magyargergo in #2369 
 
 Full Changelog : v1.6.9...v1.6.10-rc.2

</details>