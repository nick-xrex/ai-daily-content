---
id: inbox_5a1108bb
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0029-claude-code-releases-v2-1-161-ccc4]]"
title: "v2.1.161"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.161
source: claude-code-releases
published_at: 2026-06-02T21:58:22+00:00
fetched_at: 2026-06-03T00:34:01.626671+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.161 發布 25+ 項修復，強化工具呼叫穩定性與可觀測性。OTEL 度量支持自訂維度切分（team、repo）；平行工具呼叫時單一失敗不再中斷其他呼叫，各自獨立返回結果。修復 Windows WSL、worktree 隔離、背景代理、終端渲染等多個平台問題，改進全屏模式剪貼板兼容性（wl-copy/xclip/xsel）。VSCode 新增 GPU 加速關閉提示，避免字形混亂。此版本著重生產環境穩定性與可靠性。"
key_points:
  - "平行工具呼叫改進：單一 Bash 失敗獨立返回，不中斷整批，各自傳回自己的結果"
  - "OTEL 度量可按 team/repo 等自訂維度切分，便於成本分析與效能監控"
  - "多平台終端修復：Windows/WSL/macOS/Linux 剪貼板、IME、link rendering 大幅改善"
tags: [claude-code, bug-fix, observability, parallel-execution, release]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.161

Claude Code v2.1.161 發布 25+ 項修復，強化工具呼叫穩定性與可觀測性。OTEL 度量支持自訂維度切分（team、repo）；平行工具呼叫時單一失敗不再中斷其他呼叫，各自獨立返回結果。修復 Windows WSL、worktree 隔離、背景代理、終端渲染等多個平台問題，改進全屏模式剪貼板兼容性（wl-copy/xclip/xsel）。VSCode 新增 GPU 加速關閉提示，避免字形混亂。此版本著重生產環境穩定性與可靠性。

### 重點
- 平行工具呼叫改進：單一 Bash 失敗獨立返回，不中斷整批，各自傳回自己的結果
- OTEL 度量可按 team/repo 等自訂維度切分，便於成本分析與效能監控
- 多平台終端修復：Windows/WSL/macOS/Linux 剪貼板、IME、link rendering 大幅改善

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.161)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 OTEL_RESOURCE_ATTRIBUTES values are now included as labels on metric datapoints, so you can slice usage metrics by custom dimensions like team or repo 
 claude agents rows now show done/total before the detail when work is fanned out; peek shows the longest-running item 
 /mcp now collapses claude.ai connectors you've never signed in to behind a "Show unused connectors" row 
 Parallel tool calls: a failed Bash command no longer cancels other calls in the same batch — each tool returns its own result independently 
 Fullscreen mode: clipboard now uses wl-copy / xclip / xsel on Linux when available, copies to both the clipboard and PRIMARY selection for middle-click paste, and the "hold {key} for native selection" hint now shows the correct key per terminal 
 Fixed the /effort dialog, workflow animations, and prompt keyword shimmer not honoring the "Reduce motion" setting 
 Fixed forceLoginOrgUUID / forceLoginMethod managed-settings policies blocking third-party provider sessions (Bedrock, Vertex, Foundry, Mantle) alongside the org pin (regression in 2.1.146) 
 Fixed background subagent output corrupting claude -p stdout when using --output-format text or json 
 Fixed /usage-credits starting a re-login for Team and Enterprise admins instead of pointing to the organization's usage settings page 
 Fixed /autofix-pr reporting "cannot run on the default branch" when the session is inside a git worktree or another repository 
 Fixed --resume picker not showing sessions from the current directory when it isn't a git worktree (e.g., jj workspaces) 
 Fixed Windows hooks that invoke bash explicitly (e.g., /usr/bin/bash script.sh ) failing with "command not found" or "cannot execute binary file" 
 Fixed OpenTelemetry log events ( user_prompt , api_request , tool_result , tool_decision ) being silently dropped when emitted before telemetry initialization completed 
 Fixed claude mcp list/get/add printing secrets to the terminal: ${VAR} references are no longer expanded, and credential headers and URL secrets are redacted 
 Fixed Workflow agents spawned with isolation: "worktree" in background sessions being blocked from editing files inside their own worktree 
 Fixed background sessions dispatched from claude agents booting on a stale model from the daemon's environment instead of the model in settings.json 
 Fixed a potential crash when rendering Write tool results after resuming a session 
 Fixed completed subagents getting stuck showing as running when an error occurs while finalizing their result 
 Fixed EADDRINUSE errors from tools that bind Unix sockets under $TMPDIR when CLAUDE_CODE_TMPDIR is set to a deep path 
 Improved terminal rendering performance by stabilizing the layout engine's JIT compilation profile 
 Improved rendering performance for large file writes 
 [VSCode] Added a tip suggesting disabling terminal GPU acceleration (or running /terminal-setup ) to fix garbled glyphs

</details>