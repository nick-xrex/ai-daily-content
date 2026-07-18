---
id: inbox_de702201
date: 2026-07-17
source_ref: "[[00-inbox/.../inbox_de702201]]"
title: "Ruflo v3.32.2 — Stable Codex Integration &amp; Plugin Recovery"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.2
source: ruflo-releases
published_at: 2026-07-17T04:03:06+00:00
fetched_at: 2026-07-18T01:46:16.513175+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.2 穩定版釋出，修復並穩定 Codex 整合及插件恢復。Codex 啟動改用 ruflo@latest MCP 命令、120 秒最小啟動逾時、hook 15 秒監看狗保證會話結束原生橋接關閉。修補插件身份（ruflo-core 0.2.4、ruflo-cost-tracker 0.26.2）替換舊快取包；1,111 個插件 MCP 參考修復命名空間分離（已安裝插件用 installed-plugin、獨立倉庫保留 standalone）。零依賴內建安全掃描器處理提示注入、越獄、資料洩露、常見 PII。PR #2700 通過 122 次成功檢查零失敗。"
key_points:
  - "Codex 啟動：ruflo@latest mcp start 命令 + 120 秒最小逾時、hook 15 秒監看狗自動會話結束"
  - "1,111 個插件 MCP 參考命名空間分離：installed-plugin vs standalone（防止工具衝突與註冊失敗）"
  - "零依賴內建安全防禦、PR #2700 通過 122/122 成功檢查、焦點驗證 144/144 測試"
tags: [ruflo, codex-integration, plugin-recovery, mcp-namespace, security-hardening]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Ruflo v3.32.2 — Stable Codex Integration & Plugin Recovery

Ruflo v3.32.2 穩定版釋出，修復並穩定 Codex 整合及插件恢復。Codex 啟動改用 ruflo@latest MCP 命令、120 秒最小啟動逾時、hook 15 秒監看狗保證會話結束原生橋接關閉。修補插件身份（ruflo-core 0.2.4、ruflo-cost-tracker 0.26.2）替換舊快取包；1,111 個插件 MCP 參考修復命名空間分離（已安裝插件用 installed-plugin、獨立倉庫保留 standalone）。零依賴內建安全掃描器處理提示注入、越獄、資料洩露、常見 PII。PR #2700 通過 122 次成功檢查零失敗。

### 重點
- Codex 啟動：ruflo@latest mcp start 命令 + 120 秒最小逾時、hook 15 秒監看狗自動會話結束
- 1,111 個插件 MCP 參考命名空間分離：installed-plugin vs standalone（防止工具衝突與註冊失敗）
- 零依賴內建安全防禦、PR #2700 通過 122/122 成功檢查、焦點驗證 144/144 測試

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.2 — Stable Codex Integration & Plugin Recovery

Ruflo v3.32.2 ? stable Codex integration and plugin recovery 
 This stable patch release fixes the hook parsing and MCP startup failures reported against cached Ruflo plugin bundles, hardens Codex initialization, restores security defend , and corrects plugin MCP tool names. 
 Highlights 
 
 Codex startup: generated Ruflo MCP registrations now use the platform-correct ruflo@latest mcp start command and a 120-second minimum startup timeout. 
 Valid versioned hooks: patched plugin identities ( ruflo-core 0.2.4 and ruflo-cost-tracker 0.26.2) replace stale cached bundles; shipped hook configs are non-empty, valid JSON. 
 Reliable shutdown: hooks session-end always closes the native bridge; hook shims use a 15-second watchdog and stable ruflo@latest fallback. 
 Correct plugin tools: 1,111 plugin MCP references now use the installed-plugin namespace. Standalone repository docs retain their correct standalone namespace. 
 Working security defense: a zero-dependency built-in scanner handles prompt injection, jailbreak, exfiltration, and common PII when the optional full AI Defense package is absent. 
 Honest statusline: project name is the default identity, and security status counts real findings instead of fabricated CVEs. 
 
 Install or update 
 npm install -g ruflo@3.32.2
npx -y ruflo@3.32.2 init --codex 
 For manual Codex configuration, set: 
 [ mcp_servers . ruflo ]
 startup_timeout_sec = 120 
 Windows uses command = "cmd" with args = ["/c", "npx", "-y", "ruflo@latest", "mcp", "start"] ; POSIX uses command = "npx" with args = ["-y", "ruflo@latest", "mcp", "start"] . 
 Published stable packages 
 
 @claude-flow/cli@3.32.2 
 claude-flow@3.32.2 
 ruflo@3.32.2 
 
 All three are published under npm's latest dist-tag. No alpha release tag was used. 
 Validation 
 PR #2700 merged after 122 successful checks, 3 intentional skips, and 0 failures . Focused validation also passed 144/144 tests, all package dry-runs, helper signature verification, 37/37 plugin manifests, 134/134 skill frontmatter files, Windows hook shim smoke (12/12), plugin namespace auditing, and signed witness verification. 
 Detailed recovery and technical notes 
 The full guide includes the exact Windows cache recovery commands, MCP TOML examples, package checksums, issue-by-issue behavior, and validation details: 
 https://gist.github.com/ruvnet/2b37060362af57bbffd421aa09e4db50 
 Issues fixed 
 
 #2670 ? security defend missing optional runtime 
 #2682 ? statusline project identity 
 #2685 ? plugin-bundled MCP namespace mismatch 
 #2691 ? hooks session-end native handle leak 
 #2694 ? fabricated CVE statusline counts 
 
 Full Changelog: v3.32.1...v3.32.2

</details>