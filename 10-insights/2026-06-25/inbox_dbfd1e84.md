---
id: inbox_dbfd1e84
date: 2026-06-25
source_ref: "[[00-inbox/2026-06-25/2200-claude-code-releases-v2-1-193-a054]]"
title: "v2.1.193"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.193
source: claude-code-releases
published_at: 2026-06-25T21:45:57+00:00
fetched_at: 2026-06-25T22:04:06.083079+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 发布 v2.1.193，主要改进命令执行控制、后台任务管理和 MCP 集成稳定性。新增 autoMode.classifyAllShell 设置将所有 Bash/PowerShell 命令通过自动分类器路由；改进 auto-mode 拒绝原因记录；添加 OpenTelemetry 日志事件跟踪模型响应；bash 模式新增实时文件路径自动补全；MCP 服务器认证时显示启动通知；自动回收空闲后台 shell 命令内存。修复了 /model 显示过时状态、后台任务放弃警告误触发、pinned 代理重复提示等多个 bug，改进了后台代理工作流和 MCP 头部认证自动重连机制。"
key_points:
  - "新增 autoMode.classifyAllShell 设置，将所有 Bash/PowerShell 命令通过自动模式分类器路由，加强命令执行安全控制"
  - "修复后台任务管理中的多个边界案例：避免误触发「背景任务被放弃」警告；pinned 代理升级后不再被迫重新提示；phantom subagent 不再生成"
  - "改进 MCP 认证处理：headersHelper 在收到 401/403 时自动重连；MCP 服务器需要认证时启动时提示用户"
tags: [claude-code, version-update, command-execution, background-task-management]
topics: []
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.193

Claude Code 发布 v2.1.193，主要改进命令执行控制、后台任务管理和 MCP 集成稳定性。新增 autoMode.classifyAllShell 设置将所有 Bash/PowerShell 命令通过自动分类器路由；改进 auto-mode 拒绝原因记录；添加 OpenTelemetry 日志事件跟踪模型响应；bash 模式新增实时文件路径自动补全；MCP 服务器认证时显示启动通知；自动回收空闲后台 shell 命令内存。修复了 /model 显示过时状态、后台任务放弃警告误触发、pinned 代理重复提示等多个 bug，改进了后台代理工作流和 MCP 头部认证自动重连机制。

### 重點
- 新增 autoMode.classifyAllShell 设置，将所有 Bash/PowerShell 命令通过自动模式分类器路由，加强命令执行安全控制
- 修复后台任务管理中的多个边界案例：避免误触发「背景任务被放弃」警告；pinned 代理升级后不再被迫重新提示；phantom subagent 不再生成
- 改进 MCP 认证处理：headersHelper 在收到 401/403 时自动重连；MCP 服务器需要认证时启动时提示用户

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.193)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added autoMode.classifyAllShell setting to route all Bash/PowerShell commands through the auto-mode classifier instead of only arbitrary-code-execution patterns 
 Added auto-mode denial reasons to the transcript, the denial toast, and /permissions recent denials 
 Added claude_code.assistant_response OpenTelemetry log event containing the model's response text. Redacted unless OTEL_LOG_ASSISTANT_RESPONSES=1 ; when that var is unset it follows OTEL_LOG_USER_PROMPTS , so deployments that already log prompt content will start receiving response content on upgrade — set OTEL_LOG_ASSISTANT_RESPONSES=0 to keep prompts-only. 
 Added live file path autocomplete to bash mode ( ! ) 
 Added a startup notice when MCP servers need authentication, pointing at /mcp 
 Added automatic memory-pressure reaping for idle background shell commands (disable with CLAUDE_CODE_DISABLE_BG_SHELL_PRESSURE_REAP=1 ) 
 Fixed /model and other client-data-gated UI showing stale/empty state immediately after /login 
 Fixed backgrounding (←←) spuriously cancelling with "N background tasks would be abandoned" when all running tasks carry over to the new session 
 Fixed pinned background agents being re-prompted to "Continue from where you left off" after every auto-update 
 Fixed backgrounding the main turn spawning a phantom "general-purpose (resumed)" subagent that re-ran the main conversation 
 Fixed agent panel hiding sibling agents when viewing a subagent 
 Improved background agents: the launch result no longer instructs Claude to "end your response" — it keeps working on other tasks while the agent runs 
 Improved MCP headersHelper auth: the helper now re-runs and reconnects automatically when a tool call returns 401/403 
 Improved plugin auto-rename: marketplace renames maps are now followed automatically, updating your settings to the new name 
 Improved /add-dir message when the directory is already a working directory

</details>