---
id: inbox_dea0e855
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.5.0"
author: "thedotmack"
published_at: 2026-06-10T01:57:35+00:00
fetched_at: 2026-06-10T22:04:26.429908+00:00
content_hash: "567aa2a96491457e44b1f8610825c5870d5d7583297e25dced3a3aa3c7d1ce4a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.5.0

Anonymous usage analytics (PostHog) — and the v13.5.0 release 
 claude-mem now ships anonymous, privacy-hardened usage analytics. This is the first release with any telemetry, and it follows the standard dev-tool model (Homebrew, Next.js, Astro): on by default, one command to opt out, and incapable of carrying your content by construction. 
 What's collected 
 Eight events ( install_completed , install_failed , uninstall_completed , worker_started , session_compressed , context_injected , search_performed , error_occurred ), identified by a random install UUID generated locally. Every property passes a strict whitelist scrubber — only numbers, booleans, and values from closed sets we define (platform, version, IDE choice, durations, counts) can leave your machine. 
 Never collected — enforced by whitelist, not blocklist: prompts or conversation content, file paths, source code, project or repo names, search queries, error messages, IP addresses, hardware identifiers, env values, emails, or any PII. 
 Opting out 
 Any one of these turns it off: 
 
 npx claude-mem telemetry disable 
 DO_NOT_TRACK=1 (the universal standard — overrides everything) 
 CLAUDE_MEM_TELEMETRY=0 
 
 npx claude-mem telemetry status shows the current state and which setting decided it. The installer asks once at the end of npx claude-mem install , and your answer is never re-asked. 
 Full documentation of every field and event: https://docs.claude-mem.ai/telemetry 
 Also in this release 
 
 Install flow: live progress for dependency steps and a consent prompt at the end of install 
 npx claude-mem telemetry [status|enable|disable] CLI command 
 Worker shutdown now flushes telemetry with a hard 3s bound — never delays stop 
 
 🤖 Generated with Claude Code