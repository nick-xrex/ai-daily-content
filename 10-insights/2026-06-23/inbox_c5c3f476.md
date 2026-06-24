---
id: inbox_c5c3f476
date: 2026-06-23
source_ref: "[[00-inbox/2026-06-23/2200-claude-code-releases-v2-1-187-e714]]"
title: "v2.1.187"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.187
source: claude-code-releases
published_at: 2026-06-23T21:03:48+00:00
fetched_at: 2026-06-23T22:05:01.456894+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.187 發布，引入多項安全與功能改進。新增 sandbox.credentials 設定以防止沙箱命令存取密鑰檔案和環境變數，強化隔離安全性。修復遠程 MCP 工具呼叫 5 分鐘超時問題，改善系統穩定性。修復結構化輸出中模型無限重複呼叫 StructuredOutput 的缺陷。改進組織層級模型限制、滑鼠選單互動、子代理深度追蹤與 worktree 洩漏問題。支援 GitHub App 安裝與工作流程分離配置。"
key_points:
  - "新增 sandbox.credentials 設定阻止沙箱存取密鑰環境變數，增強隔離安全性"
  - "修復遠程 MCP 工具 5 分鐘超時中止機制（CLAUDE_CODE_MCP_TOOL_IDLE_TIMEOUT 可覆蓋），改善連線穩定性"
  - "修復結構化輸出中模型重複呼叫 StructuredOutput 的問題，確保後續轉向可靠返回結構化格式"
tags: [claude-code, release, security, mcp, structured-output]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.187

Claude Code v2.1.187 發布，引入多項安全與功能改進。新增 sandbox.credentials 設定以防止沙箱命令存取密鑰檔案和環境變數，強化隔離安全性。修復遠程 MCP 工具呼叫 5 分鐘超時問題，改善系統穩定性。修復結構化輸出中模型無限重複呼叫 StructuredOutput 的缺陷。改進組織層級模型限制、滑鼠選單互動、子代理深度追蹤與 worktree 洩漏問題。支援 GitHub App 安裝與工作流程分離配置。

### 重點
- 新增 sandbox.credentials 設定阻止沙箱存取密鑰環境變數，增強隔離安全性
- 修復遠程 MCP 工具 5 分鐘超時中止機制（CLAUDE_CODE_MCP_TOOL_IDLE_TIMEOUT 可覆蓋），改善連線穩定性
- 修復結構化輸出中模型重複呼叫 StructuredOutput 的問題，確保後續轉向可靠返回結構化格式

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.187)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added sandbox.credentials setting to block sandboxed commands from reading credential files and secret environment variables 
 Added org-configured model restrictions to the model picker, --model , /model , and ANTHROPIC_MODEL , with a "restricted by your organization's settings" message when a restricted model is selected 
 Added mouse click support to select menus (permission prompts, /model , /config , etc.) in fullscreen mode 
 Fixed --resume failing with "No conversation found" when the original -p run produced no model turns 
 Fixed --json-schema and workflow agent({schema}) structured output: the model can no longer re-call StructuredOutput indefinitely after a successful call, and follow-up turns now reliably return structured output 
 Fixed remote MCP tool calls that hang with no response for 5 minutes — they now abort with an error instead of blocking indefinitely (override with CLAUDE_CODE_MCP_TOOL_IDLE_TIMEOUT ) 
 Fixed Claude Code Remote sessions taking ~2.7s longer to start after the agent proxy CA system-trust install was added 
 Fixed pasted Korean/CJK text turning into mojibake in terminals that deliver paste as per-byte extended-key events 
 Fixed /update over Remote Control hanging when a startup trust dialog would have shown 
 Fixed background jobs in the agents view getting stuck in "working" indefinitely when the agent ended a turn without producing structured output 
 Fixed channel connections dropping after navigating to the agents view and back, and after /bg , /tui , or /update 
 Fixed agent stop notifications not correctly attributing who stopped the agent, and improved wording ("finished"/"stopped" instead of "came to rest") 
 Fixed subagent depth tracking: resumed subagents now restore their original spawn depth, and forked subagents now count toward the depth cap 
 Fixed leaked agent worktree registrations: locked .git/worktrees/ entries from killed agents are now cleaned up automatically 
 Fixed Cmd+click not opening URLs in fullscreen mode in Ghostty on macOS 
 Fixed claude --help not listing the --bg / --background flag 
 Fixed Esc, Ctrl-C, and Ctrl-D not working while /share is uploading 
 Improved /install-github-app : GitHub Actions workflow setup is now optional — you can install just the GitHub App and skip the workflow/secret steps 
 Improved /btw with ←/→ arrow navigation to step through earlier answers 
 Improved /plugin to surface plugins you haven't used recently so you can clean them up 
 [VSCode] Fixed extension becoming unresponsive when resuming a large session

</details>