---
id: inbox_9af0a8a9
date: 2026-04-14
source_ref: "[[00-inbox/2026-04-14/0158-claude-code-releases-v2-1-108-a461]]"
title: "v2.1.108"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.108
source: claude-code-releases
published_at: 2026-04-14T19:12:01+00:00
fetched_at: 2026-04-21T02:01:53.205143+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.108 是功能豐富的大版本更新。引入環境變數 ENABLE_PROMPT_CACHING_1H 和 FORCE_PROMPT_CACHING_5M 讓使用者調整提示快取 TTL（支援 API key、Bedrock、Vertex、Foundry）；新增 recap 功能在回到會話時自動提供上下文摘要；模型可透過 Skill 工具發現並調用 /init、/review、/security-review 等內建命令。同時包含 20+ 項修復與改進：改善 /model 中途切換警告、/resume 預設當前目錄選擇器、錯誤訊息（區分伺服器速率限制、顯示狀態頁面連結）、減少檔案操作記憶體佔用、修復 /login 貼上問題、會話名稱遺失、終端逸出碼顯示等問題。"
key_points:
  - "新增 ENABLE_PROMPT_CACHING_1H 和 FORCE_PROMPT_CACHING_5M 環境變數，支援 Bedrock/Vertex 的快取 TTL 調整（已棄用 ENABLE_PROMPT_CACHING_1H_BEDROCK）"
  - "新增 recap 功能透過會話摘要提供返回時的上下文，可在 /config 配置或手動用 /recap 調用"
  - "模型可透過 Skill 工具自動發現內建命令；20+ 項修復包括密鑰管理、Session 復原、終端相容性、MCP 工具延遲載入"
tags: [claude-code, prompt-caching, recap-feature, skill-discovery]
topics: [foundation_models.claude]
importance: 5
novelty: 4
deep_dive_candidate: true
deep_dive_approved: false
---

## v2.1.108

Claude Code v2.1.108 是功能豐富的大版本更新。引入環境變數 ENABLE_PROMPT_CACHING_1H 和 FORCE_PROMPT_CACHING_5M 讓使用者調整提示快取 TTL（支援 API key、Bedrock、Vertex、Foundry）；新增 recap 功能在回到會話時自動提供上下文摘要；模型可透過 Skill 工具發現並調用 /init、/review、/security-review 等內建命令。同時包含 20+ 項修復與改進：改善 /model 中途切換警告、/resume 預設當前目錄選擇器、錯誤訊息（區分伺服器速率限制、顯示狀態頁面連結）、減少檔案操作記憶體佔用、修復 /login 貼上問題、會話名稱遺失、終端逸出碼顯示等問題。

### 重點
- 新增 ENABLE_PROMPT_CACHING_1H 和 FORCE_PROMPT_CACHING_5M 環境變數，支援 Bedrock/Vertex 的快取 TTL 調整（已棄用 ENABLE_PROMPT_CACHING_1H_BEDROCK）
- 新增 recap 功能透過會話摘要提供返回時的上下文，可在 /config 配置或手動用 /recap 調用
- 模型可透過 Skill 工具自動發現內建命令；20+ 項修復包括密鑰管理、Session 復原、終端相容性、MCP 工具延遲載入

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.108)