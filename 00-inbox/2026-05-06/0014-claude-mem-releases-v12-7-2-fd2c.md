---
id: inbox_03a3a83f
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v12.7.2"
author: "thedotmack"
published_at: 2026-05-06T10:34:46+00:00
fetched_at: 2026-05-26T00:14:50.190337+00:00
content_hash: "fd2c5023cd713b4efd401bcbe474b8c2211a38afa2950058b09571d005413bda"
lang: en
caption_quality: None
raw: true
topics: []
---

# v12.7.2

v12.7.2 
 Fixed 
 
 Disable Claude Code built-in auto-memory during claude-code installs by setting CLAUDE_CODE_DISABLE_AUTO_MEMORY=1 in Claude settings. 
 Make JSON config writes crash-safe, durable, symlink-safe, and safe for dangling symlink destinations. 
 Add regression coverage for atomic JSON writes through symlinked and dangling-symlink settings paths.