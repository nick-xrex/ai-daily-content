---
id: inbox_5a1108bb
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.161"
author: "ashwin-ant"
published_at: 2026-06-02T21:58:22+00:00
fetched_at: 2026-06-03T00:29:46.059349+00:00
content_hash: "ccc490ac37f98814ed92745c47cf9581af243a67bf2335d64542164f25022737"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.161

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