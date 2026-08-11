---
id: inbox_1a9b32e2
date: 2026-08-07
source_ref: "[[00-inbox/.../inbox_1a9b32e2]]"
title: "v2.1.224"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.224
source: claude-code-releases
published_at: 2026-08-07T04:00:59+00:00
fetched_at: 2026-08-11T01:16:59.818533+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.224 新增自託管環境功能，用戶可透過 claude self-hosted-runner 將自有機器或容器納入 Team/Enterprise 方案中執行 Claude Code 網頁、行動和桌面工作階段。同時推出檔案封存外掛來源（支援 HTTPS zip 安裝與可選 SHA-256 驗證）、跨工作階段訊息傳送（ListAgents 發現、crossSessionInbound 核准流程）、沙箱憑證遮罩強化（JWT 解碼、AWS SigV4 重簽），以及多項錯誤修正，包括修復長路徑工作階段解析、SendMessage 失敗報告和沙箱檔案系統拒絕規則繞過。"
key_points:
  - "Claude Code v2.1.224 新增 self-hosted-runner，Team/Enterprise 用戶可在自有機器執行工作階段，突破中央託管限制"
  - "跨工作階段 SendMessage 支援 macOS/Linux，搭配 crossSessionInbound 使跨工作階段訊息需核准，其他工作階段自動遞送"
  - "沙箱憑證遮罰強化：支援 extract/onExtractNoMatch 結構化 env 值、decode:jwt 含 maskClaims、awsPairs/sigv4 AWS 重簽"
tags: [self-hosted-runner, cross-session-messaging, credential-masking, plugin-archive, sandbox-security]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.224

Claude Code v2.1.224 新增自託管環境功能，用戶可透過 claude self-hosted-runner 將自有機器或容器納入 Team/Enterprise 方案中執行 Claude Code 網頁、行動和桌面工作階段。同時推出檔案封存外掛來源（支援 HTTPS zip 安裝與可選 SHA-256 驗證）、跨工作階段訊息傳送（ListAgents 發現、crossSessionInbound 核准流程）、沙箱憑證遮罩強化（JWT 解碼、AWS SigV4 重簽），以及多項錯誤修正，包括修復長路徑工作階段解析、SendMessage 失敗報告和沙箱檔案系統拒絕規則繞過。

### 重點
- Claude Code v2.1.224 新增 self-hosted-runner，Team/Enterprise 用戶可在自有機器執行工作階段，突破中央託管限制
- 跨工作階段 SendMessage 支援 macOS/Linux，搭配 crossSessionInbound 使跨工作階段訊息需核准，其他工作階段自動遞送
- 沙箱憑證遮罰強化：支援 extract/onExtractNoMatch 結構化 env 值、decode:jwt 含 maskClaims、awsPairs/sigv4 AWS 重簽

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.224)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.224

What's changed 
 
 Added self-hosted environments: claude self-hosted-runner turns your own machines or containers into a place Claude Code web, mobile, and desktop sessions can run, on Team and Enterprise plans 
 Added archive plugin source: install plugins from a zip over HTTPS without git or npm, with optional SHA-256 pinning 
 Added a cancel-and-confirm step when removing an unavailable paste changes a command's text 
 Added ANTHROPIC_BEDROCK_REGION_PREFIX env var for Bedrock to prefer a specific cross-region inference profile over the AWS_REGION -derived one 
 Added crossSessionInbound and dialogExpiry settings: cross-session messages sent to a session running with bypassed permissions are held for your approval, and messages to other sessions auto-deliver 
 Added sandbox credential-masking options: extract and onExtractNoMatch for structured env values, decode: "jwt" with maskClaims for JWT-aware masking, and awsPairs / sigv4 for AWS SigV4 re-signing; these need network.tlsTerminate and are honored only from user, managed, or --settings settings 
 Added cross-session SendMessage : Claude Code sessions can now message each other, on any of your machines, with ListAgents to discover them (macOS and Linux) 
 Fixed long (&gt;200 char) project paths resolving to another project's session directory under a shared sanitized prefix; session list, rename, fork, delete and /resume no longer cross projects 
 Fixed SendMessage reporting "Message sent" when the write to a teammate's inbox had actually failed; failed deliveries are now reported as errors 
 Fixed sandbox filesystem deny entries written with a trailing slash (e.g. denyRead: "~/.aws/" ) being silently bypassable on Linux and macOS 
 Fixed sandbox violation details never appearing in Bash tool results; Claude now sees which file or network access was denied and why 
 Fixed MCP tools that connect mid-turn being deferred for tool search without their names announced to the model 
 Fixed plugin install records being silently corrupted when the same plugin is installed in multiple projects 
 Fixed recalled or restored paste content occasionally attaching wrong data or silently losing text when the paste had aged out or placeholder numbers collided 
 Fixed copy-on-select on Wayland sometimes not reaching the clipboard; the two selection writes no longer race 
 Fixed the feedback survey's transcript share silently failing on long sessions; a failed share now shows an error instead of a success message 
 Fixed Remote Control auto-start intermittently failing with "Remote credentials fetch failed" on a cold start with a stale login token 
 Fixed Remote Control and SDK clients showing a blank "(no content)" message after /clear and other output-less commands 
 Fixed a Remote Control session recreated after its server session expired uploading prior local conversation history into the new session 
 Improved fullscreen mode to keep the full pre-compaction history in scrollback across repeated compactions, instead of only the most recent interval 
 Improved Remote Control: attached web and mobile clients now see compaction progress and the post-compaction boundary instead of a silent pause; /clear resets now propagate to attached clients 
 Improved Remote Control: connection failures now show a persistent failure indicator with details and a reconnect shortcut, instead of only an 8-second toast 
 Removed the 200-subagent-per-session spawn cap; long-running sessions no longer refuse new agents (concurrency and depth limits still apply) 
 Changed managed settings: the approval prompt no longer re-appears after re-login or org switching when the organization's settings are unchanged 
 Changed the feedback-survey transcript share: with your consent it now also uploads the last request's model settings — the system prompt (which includes your CLAUDE.md instructions), tool definitions, and model parameters. Secrets are redacted as before, and these fields are dropped first if the share is too large 
 Changed the Bash tool description to always note that command output is displayed to the model, not reliably to the user 
 Changed recalled paste placeholder numbers to renumber when accepted into the input 
 Changed Remote Control to archive the stale server session instead of leaving a dead one listed when a fresh session is minted after compaction or /resume 
 [VSCode] Fixed the extension showing Remote Control as connected after the connection failed 
 Fixed a session resume silently reconnecting Remote Control after the user turned it off ( --resume , SDK hosts, and the VS Code extension) 
 [VSCode] Fixed sessions not honoring remoteControlAtStartup when explicitly enabled

</details>