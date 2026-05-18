---
id: inbox_68020dd7
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_68020dd7]]"
title: "v2.1.143"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.143
source: claude-code-releases
published_at: 2026-05-15T22:28:22+00:00
fetched_at: 2026-05-18T04:01:07.012170+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.143 強化插件依賴管理——禁用時檢查上游依賴並給出 disable-chain hint，啟用時自動傳遞依賴，避免手動配置鏈。新增投影 context 成本顯示（per-turn + per-invocation 估算），marketplace browse pane 透明展示資源消耗。引入 worktree.bgIsolation: \"none\" 設定支援無 worktree 背景會話直編工作目錄，適用 worktree 不實用的 repo。修復 20+ bug，包括 .credentials.json 損毀導致 OAuth 失敗、stop hook 無限迴圈、背景會話模型/effort 重置、PowerShell 執行策略等。Windows Bedrock/Vertex/Foundry 用戶 PowerShell 工具預設啟用。"
key_points:
  - "插件依賴自動化：disable 時檢查上游依賴給 hint；enable 時遞迴啟用傳遞依賴，減少手動配置負擔"
  - "Context 成本透明化：marketplace 顯示 per-turn + per-invocation token 估算，用戶提前知道資源成本"
  - "靈活 worktree 配置：worktree.bgIsolation: \"none\" 模式直編工作目錄，支援多樣工作流"
tags: [claude-code, plugin-dependency, context-cost, background-sessions, powershell-windows]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.143

Claude Code v2.1.143 強化插件依賴管理——禁用時檢查上游依賴並給出 disable-chain hint，啟用時自動傳遞依賴，避免手動配置鏈。新增投影 context 成本顯示（per-turn + per-invocation 估算），marketplace browse pane 透明展示資源消耗。引入 worktree.bgIsolation: "none" 設定支援無 worktree 背景會話直編工作目錄，適用 worktree 不實用的 repo。修復 20+ bug，包括 .credentials.json 損毀導致 OAuth 失敗、stop hook 無限迴圈、背景會話模型/effort 重置、PowerShell 執行策略等。Windows Bedrock/Vertex/Foundry 用戶 PowerShell 工具預設啟用。

### 重點
- 插件依賴自動化：disable 時檢查上游依賴給 hint；enable 時遞迴啟用傳遞依賴，減少手動配置負擔
- Context 成本透明化：marketplace 顯示 per-turn + per-invocation token 估算，用戶提前知道資源成本
- 靈活 worktree 配置：worktree.bgIsolation: "none" 模式直編工作目錄，支援多樣工作流

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.143)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.143

What's changed 
 
 Added plugin dependency enforcement: claude plugin disable now refuses when another enabled plugin depends on the target (with a copy-pasteable disable-chain hint), and claude plugin enable force-enables transitive dependencies 
 Added projected context cost (per-turn and per-invocation token estimates) to the /plugin marketplace browse pane 
 Added worktree.bgIsolation: "none" setting to let background sessions edit the working copy directly without EnterWorktree , for repos where worktrees are impractical 
 PowerShell tool now passes -ExecutionPolicy Bypass . Opt out with CLAUDE_CODE_POWERSHELL_RESPECT_EXECUTION_POLICY=1 
 Background sessions now preserve the model and effort level you set after waking from idle 
 Shift+Tab in attached agent sessions now includes auto mode in the cycle 
 Fixed a corrupt .credentials.json with a non-array scopes value hanging the CLI on startup or silently aborting OAuth token refresh 
 Fixed right-click paste in claude agents on Windows Terminal and WSL 
 Fixed stop hooks that block repeatedly looping forever — the turn now ends with a warning after 8 consecutive blocks (override via CLAUDE_CODE_STOP_HOOK_BLOCK_CAP ) 
 Fixed Esc/Ctrl+C not cancelling a pending /loop wakeup while Claude is idle between iterations 
 Fixed /goal evaluator firing while background shells or delegated subagents are still running 
 Fixed NO_COLOR / FORCE_COLOR in settings.json env stripping Claude Code's own UI colors — they now apply to subprocesses only 
 Fixed agent view spawning repeated PowerShell processes on Windows when listing sessions 
 Fixed /bg without a prompt sending "continue" to the forked session — the fork now waits for input 
 Fixed --agent &lt;name&gt; not finding plugin-contributed agents without the plugin: prefix 
 Fixed deleting a session from agent view not removing its transcript file 
 Fixed stale-fragment rendering when scrolling in attached background sessions on Windows Terminal 
 Fixed background agents false-positive worker-stall detection storm after host sleep or macOS App Nap 
 Fixed 5xx error messages pointing at status.claude.com instead of naming the configured gateway or cloud provider 
 The PowerShell tool is now enabled by default on Windows for Bedrock, Vertex, and Foundry users. Opt out with CLAUDE_CODE_USE_POWERSHELL_TOOL=0 . 
 claude agents now accepts --add-dir , --settings , --mcp-config , and --plugin-dir and applies them to the dashboard and to background sessions dispatched from it 
 claude agents accepts --permission-mode , --model , --effort , and --dangerously-skip-permissions to set defaults for sessions dispatched from the view 
 claude --bg --dangerously-skip-permissions now persists across retire→wake 
 Fixed background sessions silently capturing IDE file references into the warm spare's input, which caused the reference to be prepended to the next prompt dispatched from claude agents 
 Worktree cleanup no longer falls back to rm -rf when git worktree remove fails, preventing loss of gitignored or in-progress files 
 Fixed background-job sessions on macOS getting "Operation not permitted" errors when reading files under ~/Documents , ~/Desktop , or ~/Downloads , even with Full Disk Access granted. 
 /bg now preserves --mcp-config , --settings , --add-dir , --plugin-dir , and --strict-mcp-config , so backgrounded sessions keep their MCP servers and settings across respawn. 
 Background sessions launched from claude agents now honor permissions.defaultMode from settings.json (was previously overridden to auto mode) 
 Fixed: on Windows, pressing ← in claude agents while a response was streaming could leave the agents list unresponsive to all input 
 /bg and ← -detach now preserve --fallback-model , so backgrounded workers degrade to the fallback model on overload instead of hard-failing. 
 /bg and ← -detach now preserve --allow-dangerously-skip-permissions , so the forked worker keeps bypass-permissions available in its Shift+Tab cycle. 
 Fixed: background daemon spawn now falls back to the running binary when the ~/.local/bin/claude launcher is missing or non-executable 
 Fixed claude agents --allow-dangerously-skip-permissions defaulting dispatched sessions to bypass mode instead of making it available in the permission cycle

</details>