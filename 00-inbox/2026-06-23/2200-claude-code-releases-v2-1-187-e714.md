---
id: inbox_c5c3f476
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.187"
author: "ashwin-ant"
published_at: 2026-06-23T21:03:48+00:00
fetched_at: 2026-06-23T22:00:14.944244+00:00
content_hash: "e7149ef59b14c5ac84927980b4684f81a1d732101f9253a8fd9adb81a1c45614"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.187

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