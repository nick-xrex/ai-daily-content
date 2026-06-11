---
id: inbox_dea0e855
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_dea0e855]]"
title: "v13.5.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.5.0
source: claude-mem-releases
published_at: 2026-06-10T01:57:35+00:00
fetched_at: 2026-06-11T00:25:10.273703+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.5.0 首次推出匿名使用分析功能，整合 PostHog 遙測。該版本預設啟用分析，蒐集 8 類事件（install_completed、uninstall_completed、worker_started、session_compressed、context_injected、search_performed、error_occurred 等），使用隨機安裝 UUID 標識，並透過嚴格白名單確保僅收集數字、布林值和預定義集合中的值，完全排除提示詞、程式碼、搜尋查詞、檔案路徑等敏感資訊。使用者可透過 `npx claude-mem telemetry disable`、`DO_NOT_TRACK=1` 或 `CLAUDE_MEM_TELEMETRY=0` 等多種方式禁用分析。這是 claude-mem 首度提供遙測功能，遵循 Homebrew、Next.js 等開發工具的標準隱私模式。"
key_points:
  - "claude-mem v13.5.0 首次集成 PostHog 遙測，預設啟用但提供多種禁用選項（npx 指令、環境變數、通用標準 DO_NOT_TRACK）"
  - "遙測嚴格白名單：僅收集數字、布林值和預定義集合，完全排除提示詞、程式碼、搜尋查詞、檔案路徑、IP、硬體識別符、PII 等"
  - "8 個事件類型追蹤：安裝、卸載、工作器啟動、會話壓縮、上下文注入、搜尋、錯誤，每事件附隨機安裝 UUID"
tags: [claude-mem, telemetry, privacy, analytics, open-source]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.5.0

claude-mem v13.5.0 首次推出匿名使用分析功能，整合 PostHog 遙測。該版本預設啟用分析，蒐集 8 類事件（install_completed、uninstall_completed、worker_started、session_compressed、context_injected、search_performed、error_occurred 等），使用隨機安裝 UUID 標識，並透過嚴格白名單確保僅收集數字、布林值和預定義集合中的值，完全排除提示詞、程式碼、搜尋查詞、檔案路徑等敏感資訊。使用者可透過 `npx claude-mem telemetry disable`、`DO_NOT_TRACK=1` 或 `CLAUDE_MEM_TELEMETRY=0` 等多種方式禁用分析。這是 claude-mem 首度提供遙測功能，遵循 Homebrew、Next.js 等開發工具的標準隱私模式。

### 重點
- claude-mem v13.5.0 首次集成 PostHog 遙測，預設啟用但提供多種禁用選項（npx 指令、環境變數、通用標準 DO_NOT_TRACK）
- 遙測嚴格白名單：僅收集數字、布林值和預定義集合，完全排除提示詞、程式碼、搜尋查詞、檔案路徑、IP、硬體識別符、PII 等
- 8 個事件類型追蹤：安裝、卸載、工作器啟動、會話壓縮、上下文注入、搜尋、錯誤，每事件附隨機安裝 UUID

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.5.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

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

</details>