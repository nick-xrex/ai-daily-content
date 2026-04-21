---
id: inbox_6bb7f1d4
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_6bb7f1d4]]"
title: "0.122.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.122.0
source: (resumed)
published_at: 2026-04-20T18:39:04+00:00
fetched_at: 2026-04-21T02:33:40.089275+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v0.122.0 發布，帶來多項重大功能更新。獨立安裝程式改進在 Windows 及 Intel Mac 上的自我包含性與應用安裝流程；TUI 新增 `/side` 快速側邊對話功能，並在執行中支援斜線命令與 shell 提示詞排隊輸入。Plan Mode 可在新鮮上下文中啟動實作，並在決策前顯示上下文使用量。插件工作流新增標籤瀏覽、內嵌啟用/停用切換、marketplace 移除功能，支援遠端、跨 repo 或本地 marketplace 來源。檔案系統權限現支援 deny-read glob 策略、託管 deny-read 需求、平台沙箱強制與隔離 `codex exec` 執行。工具發現與影像生成預設啟用，MCP 與 js_repl 影像輸出支援更高解析度與原始詳細中繼資料。此版本包含多項安全強化（logout 撤銷管理 ChatGPT token、project hook 與 exec 策略要求信任工作區、Windows 沙箱避免寬鬆權限授予）及 TUI 穩定性修復。"
key_points:
  - "Plan Mode 支援在新鮮上下文啟動實作，顯示上下文使用量供決策參考"
  - "插件工作流新增標籤瀏覽、內嵌切換、跨來源 marketplace（遠端/本地/跨 repo）"
  - "安全增強：deny-read glob 策略、managed deny-read、Windows 沙箱隔離、logout token 撤銷、project hook 信任要求"
tags: [claude-code, release, plan-mode, plugin-system, security]
topics: [agents.mcp]
importance: 5
novelty: 4
deep_dive_candidate: true
deep_dive_approved: false
---

## 0.122.0

Claude Code v0.122.0 發布，帶來多項重大功能更新。獨立安裝程式改進在 Windows 及 Intel Mac 上的自我包含性與應用安裝流程；TUI 新增 `/side` 快速側邊對話功能，並在執行中支援斜線命令與 shell 提示詞排隊輸入。Plan Mode 可在新鮮上下文中啟動實作，並在決策前顯示上下文使用量。插件工作流新增標籤瀏覽、內嵌啟用/停用切換、marketplace 移除功能，支援遠端、跨 repo 或本地 marketplace 來源。檔案系統權限現支援 deny-read glob 策略、託管 deny-read 需求、平台沙箱強制與隔離 `codex exec` 執行。工具發現與影像生成預設啟用，MCP 與 js_repl 影像輸出支援更高解析度與原始詳細中繼資料。此版本包含多項安全強化（logout 撤銷管理 ChatGPT token、project hook 與 exec 策略要求信任工作區、Windows 沙箱避免寬鬆權限授予）及 TUI 穩定性修復。

### 重點
- Plan Mode 支援在新鮮上下文啟動實作，顯示上下文使用量供決策參考
- 插件工作流新增標籤瀏覽、內嵌切換、跨來源 marketplace（遠端/本地/跨 repo）
- 安全增強：deny-read glob 策略、managed deny-read、Windows 沙箱隔離、logout token 撤銷、project hook 信任要求

**原文：** [(resumed)](https://github.com/openai/codex/releases/tag/rust-v0.122.0)