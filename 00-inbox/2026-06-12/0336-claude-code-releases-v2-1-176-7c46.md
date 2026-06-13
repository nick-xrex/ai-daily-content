---
id: inbox_48811dde
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.176"
author: "ashwin-ant"
published_at: 2026-06-12T21:53:27+00:00
fetched_at: 2026-06-13T03:36:04.526001+00:00
content_hash: "7c46a4c9e143e48e9ab98cd84a9397c7f61d5789d5bec0149db4975923e8923a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.176

What's changed 
 
 Session titles are now generated in the language of your conversation (set the language setting to pin a specific language) 
 Added footerLinksRegexes setting for regex-matched link badges in the footer row, configurable via user or managed settings 
 Improved Bedrock credential caching: credentials from awsCredentialExport are now cached until their Expiration instead of a fixed 1 hour 
 Fixed availableModels enforcement: alias model picks can no longer be redirected to a blocked model via ANTHROPIC_DEFAULT_*_MODEL environment variables, and /fast now refuses to toggle when it would switch to a model outside the allowlist 
 Fixed auto mode failing on Fable 5 for organizations without Opus 4.8 enabled — the classifier now falls back to the best available Opus model 
 Fixed hook if conditions for Read/Edit/Write tool paths: documented patterns like Edit(src/**) , Read(~/.ssh/**) , and Read(.env) now match correctly 
 Fixed Linux sandbox failing to start when .claude/settings.json is a symlink with an absolute target 
 Fixed /copy and mouse-selection copy not reaching the system clipboard inside tmux over SSH, and tmux paste buffer not loading on versions older than 3.2 
 Fixed Remote Control connecting from web/mobile silently switching the session's model 
 Fixed Remote Control disconnect notifications showing a bare numeric code instead of a human-readable reason, and connection failures adding a duplicate line to the conversation transcript 
 Fixed Remote Control sessions not disconnecting when you sign in to a different account 
 Fixed /cd and worktree moves leaving the session reporting the previous directory's git branch 
 Fixed claude agents : pressing back in one window no longer detaches other windows attached to the same session 
 Fixed backgrounded sessions showing "Working" forever when /bg mid-turn had nothing left to continue 
 Fixed background agent search by PR URL: PRs opened during scheduled wakeups or while a job was blocked now appear in claude agents search 
 Fixed the agents view input showing no text cursor on Windows 
 Fixed claude --bg -cn &lt;name&gt; not seeding the session name 
 Fixed background sessions to neutralize Windows network paths in persisted state before respawn 
 Fixed background-session respawn rejecting malformed resume IDs from corrupted state files 
 Fixed the Windows background-service daemon not starting when ~/.claude/daemon has the ReadOnly attribute set 
 Fixed cloud sessions failing with "Could not resolve authentication method" when idle for too long before being claimed 
 Background sessions now show clearer guidance when a window left open across an auto-update can't submit a reply, and claude daemon status explains version-skew behavior