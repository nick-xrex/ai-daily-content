---
id: inbox_74d232d7
date: 2026-06-07
source_ref: "[[00-inbox/.../inbox_74d232d7]]"
title: "v0.17.1"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.17.1
source: repowise-releases
published_at: 2026-06-07T11:13:27+00:00
fetched_at: 2026-07-22T01:05:31.885209+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.17.1 patch版本（2026年6月7日發布）專注穩定性與品質改進。主要內容包括：(1) 初始化流程UX最佳化（進度條顯示改進、並發度預設10、Resume提示、成本門檻預設yes），加速用戶上手；(2) 針對MCP工具與自動生成CLAUDE.md進行回應品質全面掃描與增強（#413）；(3) 搜尋排序與嵌入管道重新校準，含共變持久化與風險校準（#414），並引入骨架預設與統計專屬蒸餾；(4) 安全層現已在託管部署中可用（#411）。版本代表v0.17.0之後的穩定性加固與用戶體驗精細調整。"
key_points:
  - "初始化流程並發度預設10 + Resume提示 + 成本門檻預設yes（#412）：降低用戶設置障礙"
  - "MCP工具與CLAUDE.md生成的回應品質全面掃描（#413）：確保生成文件的準確性與一致性"
  - "搜尋排序與嵌入共變持久化 + 風險校準（#414）：修正RAG系統中搜尋與向量表示的不同步"
tags: [repowise, patch-release, quality-sweep, mcp-integration, ux-improvement]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.17.1

Repowise v0.17.1 patch版本（2026年6月7日發布）專注穩定性與品質改進。主要內容包括：(1) 初始化流程UX最佳化（進度條顯示改進、並發度預設10、Resume提示、成本門檻預設yes），加速用戶上手；(2) 針對MCP工具與自動生成CLAUDE.md進行回應品質全面掃描與增強（#413）；(3) 搜尋排序與嵌入管道重新校準，含共變持久化與風險校準（#414），並引入骨架預設與統計專屬蒸餾；(4) 安全層現已在託管部署中可用（#411）。版本代表v0.17.0之後的穩定性加固與用戶體驗精細調整。

### 重點
- 初始化流程並發度預設10 + Resume提示 + 成本門檻預設yes（#412）：降低用戶設置障礙
- MCP工具與CLAUDE.md生成的回應品質全面掃描（#413）：確保生成文件的準確性與一致性
- 搜尋排序與嵌入共變持久化 + 風險校準（#414）：修正RAG系統中搜尋與向量表示的不同步

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.17.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.17.1

What's Changed 
 
 docs(commercial): security layer now available on hosted by @RaghavChamadiya in #411 
 fix(init): health progress-bar UX, cost-gate default yes, concurrency 10, resume hint by @RaghavChamadiya in #412 
 fix(mcp,claude-md): response-quality sweep across MCP tools and generated CLAUDE.md by @RaghavChamadiya in #413 
 fix(mcp,rag,git): search ranking + embedding pipeline, risk calibration, co-change persistence, skeleton default, stat-only distill by @RaghavChamadiya in #414 
 release: v0.17.1 — MCP Registry listing + post-0.17.0 fixes by @RaghavChamadiya in #415 
 
 Full Changelog : v0.17.0...v0.17.1

</details>