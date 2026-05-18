---
id: inbox_e3c4a0f4
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_e3c4a0f4]]"
title: "Warelay -&gt; OpenClaw"
url: https://simonwillison.net/2026/May/16/openclaw-names/#atom-everything
source: simon-willison
published_at: 2026-05-16T20:23:30+00:00
fetched_at: 2026-05-18T04:02:17.961751+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "非 AI 技術內容。文章記錄 OpenClaw（AI 助手）項目的命名歷史演變（Warelay → CLAWDIS → CLAWDBOT → Clawdbot → Moltbot → OpenClaw），使用 first_line_history.py 工具追蹤 Git 記錄。核心是版本控制與命名歷史，不涉及 AI 功能或技術。"
key_points:
tags: []
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Warelay -> OpenClaw

非 AI 技術內容。文章記錄 OpenClaw（AI 助手）項目的命名歷史演變（Warelay → CLAWDIS → CLAWDBOT → Clawdbot → Moltbot → OpenClaw），使用 first_line_history.py 工具追蹤 Git 記錄。核心是版本控制與命名歷史，不涉及 AI 功能或技術。

### 重點

**原文：** [simon-willison](https://simonwillison.net/2026/May/16/openclaw-names/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Warelay -> OpenClaw

In preparation for a lightning talk I'm giving at PyCon US this afternoon I decided to figure out how many names OpenClaw has actually had since that first commit back in November. 
 Thanks to this first_line_history.py tool ( code here ) the answer, according to the Git history of the OpenClaw README, is: 
 Warelay → CLAWDIS → CLAWDBOT → Clawdbot → Moltbot →🦞 OpenClaw 
 Or in detail (the output from the tool): 
 
2025-11-24T11:23:15+01:00 16dfc1a # Warelay — WhatsApp Relay CLI (Twilio)
2025-11-24T11:41:37+01:00 d4153da # 📡 Warelay — WhatsApp Relay CLI (Twilio)
2025-11-24T17:47:57+01:00 343ef9b # 📡 warelay — WhatsApp Relay CLI (Twilio)
2025-11-25T04:44:10+01:00 14b3c6f # 📡 warelay — WhatsApp Relay CLI
2025-11-25T12:48:40+01:00 4814021 # 📡 warelay — Send, receive, and auto-reply on WhatsApp—Twilio-backed or QR-linked.
2025-11-25T13:50:18+01:00 d51a3e9 # warelay 📡 - Send, receive, and auto-reply on WhatsApp via Twilio or QR-linked WhatsApp Web; webhook setup in one command
2025-11-25T13:51:13+01:00 4d2a8a8 # 📡 warelay — Send, receive, and auto-reply on WhatsApp—Twilio-backed or QR-linked.
2025-11-25T14:52:43+01:00 1ef7f4d # 📡 warelay — Send, receive, and auto-reply on WhatsApp.
2025-12-03T15:45:32+00:00 a27ee23 # 🦞 CLAWDIS — WhatsApp Gateway for AI Agents
2025-12-08T12:43:13+01:00 17fa2f4 # 🦞 CLAWDIS — WhatsApp &amp; Telegram Gateway for AI Agents
2025-12-19T18:41:17+01:00 7710439 # 🦞 CLAWDIS — Personal AI Assistant
2026-01-04T14:32:47+00:00 246adaa # 🦞 CLAWDBOT — Personal AI Assistant
2026-01-10T05:14:09+01:00 cdb915d # 🦞 Clawdbot — Personal AI Assistant
2026-01-27T13:37:47-05:00 3fe4b25 # 🦞 Moltbot — Personal AI Assistant
2026-01-30T03:15:10+01:00 9a71607 # 🦞 OpenClaw — Personal AI Assistant
 

 Tags: openclaw , git , tools

</details>