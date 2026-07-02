---
id: inbox_f5d6a95a
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.9.2"
author: "thedotmack"
published_at: 2026-07-01T04:52:30+00:00
fetched_at: 2026-07-01T23:31:24.791545+00:00
content_hash: "f048e05bd32d5f48ae9520bd66047a766ad73c56c80fdf5ff57f2703dc372c4e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.9.2

Bug Fix 
 Removed client-side context truncation from the provider layer. 
 The OpenAICompatibleProvider applied a sliding-window truncation to conversation history — a hardcoded 20-message cap and a 100k-token "safety" limit layered on top of the model's own context window. In practice it fired on message count alone, dropping conversation messages at ~12k tokens (nowhere near the token limit) and silently corrupting history, mislabeled as "runaway cost" prevention. This broke setups whose real model context window bore no relation to those hardcoded assumptions. 
 The full conversation history is now sent to the provider, which owns its own context window. 
 Removed 
 
 OpenAICompatibleProvider.truncateHistory() and the requireNonEmptyToTruncate flag 
 truncateHistoryForOpenRouter / truncateHistoryForGemini wrappers and their message/token constants 
 CLAUDE_MEM_{GEMINI,OPENROUTER}_MAX_CONTEXT_MESSAGES / _MAX_TOKENS settings, defaults, and validation 
 Related tests, docs, and installer references 
 
 Merged in #3096 . Verified: tsc clean, 2248 tests passing, build-and-sync clean.