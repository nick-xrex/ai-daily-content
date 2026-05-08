---
id: inbox_845c8360
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.133"
author: "ashwin-ant"
published_at: 2026-05-07T23:49:04+00:00
fetched_at: 2026-05-08T07:37:23.581755+00:00
content_hash: "033fed84720b29eadfc04e7a111d6120fc93ddc7551eeb9f50df27dbb3e1c4e0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.133

What's changed 
 
 Added worktree.baseRef setting ( fresh | head ) to choose whether --worktree , EnterWorktree , and agent-isolation worktrees branch from origin/&lt;default&gt; or local HEAD . Note: the default fresh changes EnterWorktree 's base back to origin/&lt;default&gt; (it has been local HEAD since 2.1.128) — set worktree.baseRef: "head" to keep unpushed commits in new worktrees 
 Added sandbox.bwrapPath and sandbox.socatPath managed settings (Linux/WSL) to specify custom bubblewrap and socat binary locations 
 Added parentSettingsBehavior admin-tier key ( 'first-wins' | 'merge' ) to let admins opt SDK managedSettings (parent tier) into the policy merge 
 Hooks now receive the active effort level via the effort.level JSON input field and the $CLAUDE_EFFORT environment variable, and Bash tool commands can read $CLAUDE_EFFORT 
 Improved focus mode behavior 
 Improved memory usage by releasing warm-spare background workers under memory pressure 
 Fixed parallel sessions all dead-ending at 401 after a refresh-token race wiped shared credentials 
 Fixed Edit / Write allow rules scoped to a drive root ( C:\ ) or POSIX / matching incorrectly and always prompting 
 Fixed an unhandled rejection ( ECOMPROMISED ) when a history or session-log file lock is compromised by clock skew or slow disk 
 Fixed pressing Esc during conversation compaction showing a spurious "Error compacting conversation" notification 
 Fixed HTTP(S)_PROXY / NO_PROXY / mTLS not being respected for the full MCP OAuth flow including discovery, dynamic client registration, token exchange, and token refresh 
 Fixed Read/Write/Edit being denied on mapped network drives passed via --add-dir / SDK additionalDirectories 
 Fixed Remote Control stop/interrupt from claude.ai not fully canceling the CLI session the same way local Esc does, causing queued messages to never advance after interrupting a stuck tool or prompt 
 Fixed /effort in one session unexpectedly changing the effort level of other concurrent sessions, and a related issue where an IDE effort change could be silently dropped 
 Fixed subagents not discovering project, user, or plugin skills via the Skill tool 
 claude --help now lists --remote-control alongside --remote-control-session-name-prefix 
 [VSCode] Fixed claudeCode.claudeProcessWrapper failing with "Unsupported platform" when the extension build doesn't bundle a Claude binary