---
id: inbox_ef42e1aa
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.146"
author: "ashwin-ant"
published_at: 2026-05-21T01:51:52+00:00
fetched_at: 2026-05-21T09:17:23.804933+00:00
content_hash: "aa246dd3feb4bf427ca8241c8ad981eb217dcc4a5569b12cf540b0236e0a03a1"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.146

What's changed 
 
 Renamed /simplify to /code-review with an optional effort level (e.g. /code-review high ) 
 Auto mode no longer suppresses AskUserQuestion when the user or a skill explicitly relies on it 
 Fixed Windows PowerShell tool failing with "command line is invalid" when pwsh is installed via winget or the Microsoft Store (regression in v2.1.124) 
 Fixed MCP resources/list , resources/templates/list , and prompts/list dropping items past page 1 on paginating servers 
 Fixed full-screen strobing in attached background sessions on Windows Terminal while Claude is streaming 
 Fixed the auto-updater status line not showing your current version when an update fails 
 Fixed on Windows, removing a background-job worktree no longer follows NTFS junctions into the main repo 
 Fixed /background refusing sessions whose only typed input was a skill or custom slash command 
 Fixed backgrounded sessions re-prompting for tool permissions you already granted with "don't ask again" 
 Fixed /theme color editor and "New custom theme" dialogs not responding to Esc 
 Fixed an uncaught exception at the end of streaming sessions when running via the Agent SDK 
 Fixed forceLoginOrgUUID and forceLoginMethod managed-settings policies not being enforced against third-party-provider and API-key sessions 
 Fixed GNOME Terminal right-click and middle-click paste not inserting text 
 Fixed CLAUDE_CODE_SUBAGENT_MODEL not being forwarded to child processes in multi-agent sessions 
 Improved auto-updater reliability: native version checks and downloads now retry transient network failures instead of failing immediately 
 Improved diff rendering performance for large file edits