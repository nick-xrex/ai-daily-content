---
id: inbox_d6333c13
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-claude-code-releases-v2-1-174-dffb]]"
title: "v2.1.174"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.174
source: claude-code-releases
published_at: 2026-06-12T01:16:36+00:00
fetched_at: 2026-06-13T03:40:37.897323+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.174 發佈，包含 20+ 項修復和改進。重點包括：新增 wheelScrollAccelerationEnabled 設定以禁用全螢幕滾輪加速、/model picker 邏輯修復使 Opus 在 Max/Team Premium/Enterprise plans 獨立顯示、Bedrock GovCloud 修復（us-gov-* regions 現使用正確的 us-gov prefix 而非 global，避免 400 errors）、Fable 5 banner 修復避免誤導 usage-based billing 帳戶、背景 session 環境變數隔離修復、macOS/Linux exit delay 修復、Skill hot-reload 優化（只重新公告變更的 skill）、Workflow tool agent() 歸因修復、VSCode 用量歸因增強顯示 cache misses/long context/subagents 細項。"
key_points:
  - "/model picker 邏輯修復：不同 plan 等級現正確顯示預設模型（Max/Enterprise 顯示 Opus；Pro/Team 顯示 Sonnet）"
  - "Bedrock GovCloud 修復：us-gov-* regions 現使用正確的 us-gov inference profile prefix，之前使用 global 導致 400 errors"
  - "Skill hot-reload 優化：僅重新公告變更的 skills 而非整個列表，降低 hook overhead"
tags: [claude-code-release, bug-fixes, bedrock-integration, govcloud, ui-improvements]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.174

Claude Code v2.1.174 發佈，包含 20+ 項修復和改進。重點包括：新增 wheelScrollAccelerationEnabled 設定以禁用全螢幕滾輪加速、/model picker 邏輯修復使 Opus 在 Max/Team Premium/Enterprise plans 獨立顯示、Bedrock GovCloud 修復（us-gov-* regions 現使用正確的 us-gov prefix 而非 global，避免 400 errors）、Fable 5 banner 修復避免誤導 usage-based billing 帳戶、背景 session 環境變數隔離修復、macOS/Linux exit delay 修復、Skill hot-reload 優化（只重新公告變更的 skill）、Workflow tool agent() 歸因修復、VSCode 用量歸因增強顯示 cache misses/long context/subagents 細項。

### 重點
- /model picker 邏輯修復：不同 plan 等級現正確顯示預設模型（Max/Enterprise 顯示 Opus；Pro/Team 顯示 Sonnet）
- Bedrock GovCloud 修復：us-gov-* regions 現使用正確的 us-gov inference profile prefix，之前使用 global 導致 400 errors
- Skill hot-reload 優化：僅重新公告變更的 skills 而非整個列表，降低 hook overhead

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.174)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added wheelScrollAccelerationEnabled setting to disable mouse-wheel scroll acceleration in fullscreen mode 
 Fixed the /model picker hiding the model family that Default resolves to — Opus now appears as its own row on Max/Team Premium/Enterprise plans, Sonnet on Pro/Team plans, and Opus on pay-as-you-go API accounts 
 Fixed /model picker showing a hardcoded Sonnet version label when ANTHROPIC_DEFAULT_SONNET_MODEL pins a different Sonnet 
 Fixed the "Fable 5 is now consuming usage credits" banner incorrectly showing for enterprise accounts with usage-based billing 
 Fixed Bedrock GovCloud regions ( us-gov-* ) deriving the wrong inference profile prefix ( global instead of us-gov ), causing 400 errors on derived model IDs 
 Fixed background sessions inheriting another session's ANTHROPIC_* provider env (gateway URL, custom headers, /model aliases) from the shell that started the background daemon 
 Fixed a 1-2 second pause when exiting Claude Code shortly after a shell command was interrupted or killed on macOS and Linux 
 Fixed git commit co-author attribution showing an incorrect model name for some models 
 Fixed the /advisor dialog pre-selecting a saved advisor model that is blocked by the availableModels allowlist 
 Fixed skill hot-reload re-sending the entire skill listing when a single skill changed; only changed skills are now re-announced 
 Fixed Workflow tool agent() subagents missing per-agent attribution headers 
 [VSCode] Added usage attribution to the Account &amp; usage dialog ( /usage ) showing cache misses, long context, subagents, and per-skill/agent/plugin/MCP breakdowns over the last 24h or 7d 
 Fixed pre-warmed background workers failing with "Could not resolve authentication method" when claimed after sitting idle

</details>