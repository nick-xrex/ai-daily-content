---
id: inbox_99a4eb5b
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.195"
author: "ashwin-ant"
published_at: 2026-06-26T21:29:42+00:00
fetched_at: 2026-06-26T22:23:18.297882+00:00
content_hash: "b0aa7071e87ba7328f7e905cac9158604ad70f1a827480b427ea6e91e8aa232b"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.195

What's changed 
 
 Added CLAUDE_CODE_DISABLE_MOUSE_CLICKS to disable mouse click/drag/hover in fullscreen mode while keeping wheel scroll 
 Fixed hook matchers with hyphenated identifiers (e.g. code-reviewer , mcp__brave-search ) accidentally substring-matching — they now exact-match. Use mcp__brave-search__.* to match all tools from a hyphenated MCP server. 
 Fixed voice dictation on macOS capturing silence in long-running sessions after the default input device changes 
 Fixed voice dictation auto-submit never firing for languages written without spaces (Japanese, Chinese, Thai) 
 Fixed external plugins enabled only by project .claude/settings.json not requiring explicit install consent on every loader path 
 Fixed /plugin Enable/Disable not working when a plugin's plugin.json name differs from its marketplace entry name 
 Fixed background jobs disappearing from claude agents or losing data when written by a newer Claude Code version 
 Fixed reopening a crashed background task showing a blank screen for up to 5 seconds instead of its restart 
 Fixed background agent daemons running unreachable when the control socket fails to start, blocking restarts 
 Improved voice mode on Linux: now distinguishes "no microphone" from "SoX not installed" when SoX is present but no audio capture device exists 
 Improved claude agents completed list to fill available vertical space; on short terminals the header compacts so live sessions stay visible 
 Improved Remote session startup with a provisioning checklist while the container starts