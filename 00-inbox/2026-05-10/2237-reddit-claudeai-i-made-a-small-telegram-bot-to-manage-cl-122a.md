---
id: inbox_4d625492
source: reddit-claudeai
source_type: rss
url: "https://www.reddit.com/r/ClaudeAI/comments/1t8ruo9/i_made_a_small_telegram_bot_to_manage_claude_code/"
author: "/u/YuryGagarin"
published_at: 2026-05-10T00:31:01+00:00
fetched_at: 2026-05-10T22:37:17.105437+00:00
content_hash: "122a508178bc0aa2b9957a6d62d5c77d66a294295f040db0658694e9ab71de20"
lang: en
caption_quality: None
raw: true
topics: []
---

# I made a small Telegram bot to manage Claude Code Channels sessions on a headless server

TL;DR: Telegram bot to keep Claude Code running on a remote server and control it from your phone. --- Claude Code recently got an experimental Channels feature — you can talk to Claude directly in Telegram like a chat. It's pretty cool if you haven't tried it. The problem: it needs a terminal open to keep running. I run Claude on a home Linux server and got tired of SSH-ing in just to restart it. So I wrote a small launcher bot — it manages the Claude tmux session and lets you start/stop/restart it from Telegram. What it does: - /launch /stop /restart /status /logs - Watchdog that notifies you (or auto-restarts) if Claude dies - Zero Python dependencies — stdlib only GitHub: https://github.com/gagarinyury/claude-channels-launcher Nothing fancy, just a weekend script that turned out useful. If you're running Claude Code on a remote machine, maybe it helps. https://preview.redd.it/qizbeodxg70h1.png?width=830&amp;format=png&amp;auto=webp&amp;s=d8958dd00053c41b58cdf72215ae827afc1dafc5 &#32; submitted by &#32; /u/YuryGagarin [link] &#32; [comments]