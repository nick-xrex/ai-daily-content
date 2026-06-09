---
id: inbox_85248c58
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.4.1"
author: "thedotmack"
published_at: 2026-06-08T01:47:09+00:00
fetched_at: 2026-06-08T18:00:52.519315+00:00
content_hash: "3bfc015ccc9d4bf224fbc2f38ff100a36d8c49ae591aa9a20cbaf75d6c75168f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.4.1

What's new 
 🟣 CMEM Online email opt-in during npx claude-mem install 
 An optional, interactive email opt-in now appears at the start of the installer. Press Enter to skip — it never blocks or fails the install. 
 
 Collects an email + an optional "what are you working on / how can we help your team" note. 
 POSTs to the live https://cmem.ai/api/waitlist endpoint (handles persistence, dedup, and the confirmation email server-side). Overridable via CLAUDE_MEM_SIGNUP_URL ; tagged source: npx-installer . 
 Skipped automatically when non-interactive, under CI, or with CLAUDE_MEM_ONLINE_OPTIN=false . 
 Signup is persisted locally so returning users aren't re-prompted; a failed send is retried silently on the next install. 
 No secrets ship in the npx package — the endpoint is unauthenticated and the Resend key stays server-side. The waitlist endpoint was extended to capture the optional note. 
 
 🔴 Fixes 
 
 Remove a duplicate ModeManager import that was breaking the typecheck. 
 Exempt the transcript-watcher-entry CLI process entry point from the console-logging guard.