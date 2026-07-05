---
id: inbox_95247c36
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.10.1"
author: "thedotmack"
published_at: 2026-07-04T04:53:09+00:00
fetched_at: 2026-07-04T22:00:23.674158+00:00
content_hash: "6ddd5c74f7038b4b8e6469c144f74bcddc2c72f8cec89e5f8c97d8c10764e41f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.10.1

Fixes 
 
 Codex SessionStart hook no longer fails at startup. When a hook errored before its handler ran (missing session_id , invalid cwd , or a missing transcript path), claude-mem fell back to a bare {"continue":true} regardless of which hook fired. Codex's strict SessionStart validator rejects that shape as "invalid session start JSON output," breaking context injection at Codex startup. The fallback now emits a valid hookSpecificOutput: { hookEventName: "SessionStart", additionalContext: "" } for the context hook, matching what Codex expects. 
 Fixed a related gap where the Codex adapter silently dropped an explicit empty-string additionalContext from its output instead of preserving it, which could leave the SessionStart payload incomplete. 
 
 Closes #2947 , #2972 . Supersedes #2953 and #2948 .